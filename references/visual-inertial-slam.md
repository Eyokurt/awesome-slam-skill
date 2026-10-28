# Visual-Inertial SLAM & Odometry (VIO) Reference Guide

Fusing visual cameras with Inertial Measurement Units (IMUs: 3-axis accelerometer + 3-axis gyroscope) yields metric scale, high-frequency state estimation (100–200 Hz), and resilience against temporary visual occlusion or aggressive maneuvers.

---

## 1. Mathematical Principle of IMU Preintegration

Standard numerical integration of IMU measurements depends on the world-frame orientation $R_{w}^{b_i}$, requiring complete re-integration whenever older keyframe poses change during non-linear optimization.

**Preintegration (Forster et al.)** decouples IMU measurements from the global world frame into the local frame of keyframe $i$:

$$\Delta R_{ij} = \prod_{k=i}^{j-1} \operatorname{Exp}\left((\boldsymbol{\omega}_k - \mathbf{b}_{g,i}) \Delta t\right)$$
$$\Delta \mathbf{v}_{ij} = \sum_{k=i}^{j-1} \Delta R_{ik} (\mathbf{a}_k - \mathbf{b}_{a,i}) \Delta t$$
$$\Delta \mathbf{p}_{ij} = \sum_{k=i}^{j-1} \left( \Delta \mathbf{v}_{ik} \Delta t + \frac{1}{2} \Delta R_{ik} (\mathbf{a}_k - \mathbf{b}_{a,i}) \Delta t^2 \right)$$

### First-Order Bias Correction
When accelerometer bias $\mathbf{b}_a$ or gyroscope bias $\mathbf{b}_g$ change slightly during optimization, preintegrated values are updated via first-order Taylor expansion without re-running the integration:
$$\Delta R_{ij}(\mathbf{b}_g) \approx \Delta \bar{R}_{ij} \cdot \operatorname{Exp}\left( J_{b_g}^{\Delta R} (\mathbf{b}_{g,i} - \bar{\mathbf{b}}_{g,i}) \right)$$
$$\Delta \mathbf{v}_{ij}(\mathbf{b}_a, \mathbf{b}_g) \approx \Delta \bar{\mathbf{v}}_{ij} + J_{b_a}^{\Delta v} (\mathbf{b}_{a,i} - \bar{\mathbf{b}}_{a,i}) + J_{b_g}^{\Delta v} (\mathbf{b}_{g,i} - \bar{\mathbf{b}}_{g,i})$$
$$\Delta \mathbf{p}_{ij}(\mathbf{b}_a, \mathbf{b}_g) \approx \Delta \bar{\mathbf{p}}_{ij} + J_{b_a}^{\Delta p} (\mathbf{b}_{a,i} - \bar{\mathbf{b}}_{a,i}) + J_{b_g}^{\Delta p} (\mathbf{b}_{g,i} - \bar{\mathbf{b}}_{g,i})$$

---

## 2. Filtering vs Optimization (Sliding Window)

| Paradigm | Representatives | Estimation Method | State Dimension | CPU Overhead | Accuracy & Consistency |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **MSCKF (Multi-State Constraint KF)** | **[msckf_vio](https://github.com/KumarRobotics/msckf_vio)**, **[OpenVINS](https://github.com/rpng/open_vins)** | Extended Kalman Filter (EKF) | Fixed window of camera poses; landmarks marginalized analytically | Extremely light (~5–10% of 1 CPU core) | High short-term accuracy; linearization errors cannot be corrected retrospectively. |
| **Iterated EKF with Direct Photometry** | **[ROVIO](https://github.com/ethz-asl/rovio)** | Iterated EKF tracking intensity patches directly | Multi-level image patches + IMU states | Very light | Robust against motion blur; no feature extraction needed. |
| **Fixed-Lag Smoothing / Factor Graph** | **[VINS-Mono](https://github.com/HKUST-Aerial-Robotics/VINS-Mono)**, **[VINS-Fusion](https://github.com/HKUST-Aerial-Robotics/VINS-Fusion)**, **[OKVIS](https://github.com/ethz-asl/okvis)** | Non-linear least squares over a sliding window of 10 keyframes | Poses + Velocities + Biases + 3D Features | Medium | Higher accuracy; iterative re-linearization refines past estimates. |
| **Full Factor Graph Bundle Adjustment** | **[ORB-SLAM3](https://github.com/UZ-SLAMLab/ORB_SLAM3)**, **[Basalt](https://gitlab.com/VladyslavUsenko/basalt)** | Joint Visual-Inertial BA + global pose graph | Local window + global covisibility graph | Medium to High | State-of-the-art accuracy, global consistency, zero scale drift on loop closure. |

---

## 3. VIO Initialization Pipeline

A monocular camera alone has no metric scale, unknown gravity vector direction, and unknown accelerometer bias. A robust VIO initialization procedure follows these steps:

1. **Pure Visual Structure-from-Motion (SfM)**:
   - Track features across a short sequence of frames (1–2 seconds) using optical flow.
   - Establish up-to-scale relative poses and triangulate 3D point cloud.
2. **Visual-Inertial Alignment**:
   - Align preintegrated gyroscope data to visual rotation to calibrate gyroscope bias $\mathbf{b}_g$.
   - Formulate a linear system solving for:
     - Metric scale factor $s$.
     - Gravity vector in visual world frame $\mathbf{g}^c_0$.
     - Camera-to-body velocity at keyframes $\mathbf{v}_k$.
3. **Gravity Vector Refinement**:
   - Gravity magnitude is fixed ($\|\mathbf{g}\| = 9.81\text{ m/s}^2$). Optimize rotation on tangent space of sphere to fix gravity direction.
4. **State Transition**:
   - Initialize the sliding-window optimizer with the recovered metric scale and gravity direction.

---

## 4. Marginalization and the Schur Complement

To keep computational complexity bounded, old keyframes must be removed from the sliding window. Simply dropping them discards valuable information.

**Marginalization**:
1. Partition system into states to be removed $\mathbf{x}_m$ (oldest frame or frame without parallax) and states to be retained $\mathbf{x}_r$:
   $$\begin{bmatrix} H_{mm} & H_{mr} \\ H_{rm} & H_{rr} \end{bmatrix} \begin{bmatrix} \Delta \mathbf{x}_m \\ \Delta \mathbf{x}_r \end{bmatrix} = \begin{bmatrix} \mathbf{b}_m \\ \mathbf{b}_r \end{bmatrix}$$
2. Eliminate $\Delta \mathbf{x}_m$ using Schur complement:
   $$H^* = H_{rr} - H_{rm} H_{mm}^{-1} H_{mr}, \quad \mathbf{b}^* = \mathbf{b}_r - H_{rm} H_{mm}^{-1} \mathbf{b}_m$$
3. Convert $H^*, \mathbf{b}^*$ into a **linearized prior factor** connected to remaining active states in the next optimization cycle.

> [!CAUTION]
> **First-Estimate Jacobians (FEJ)**: Because $H^*$ fixes the linearization point of marginalized states, all subsequent measurements evaluated against those states must use the same linearization point. Violating FEJ causes artificial information gain, unobservable subspace corruption (yaw becomes spuriously observable), and filter inconsistency.

---

## 5. Leading Visual-Inertial Frameworks

- **[VINS-Mono](https://github.com/HKUST-Aerial-Robotics/VINS-Mono) & [VINS-Fusion](https://github.com/HKUST-Aerial-Robotics/VINS-Fusion)**:
  - Fuses Monocular / Stereo / RGB-D with IMU and external GPS.
  - Features real-time loop detection using DBoW2 and 4-DoF pose graph optimization.
- **[ORB-SLAM3](https://github.com/UZ-SLAMLab/ORB_SLAM3)**:
  - Fast IMU initialization in $<2\text{ seconds}$.
  - Seamless switching between Visual-Inertial and pure Visual modes if IMU drops out.
- **[Basalt](https://gitlab.com/VladyslavUsenko/basalt)**:
  - Extracts non-linear factor representations from visual-inertial odometry to enable full real-time global mapping and non-linear factor recovery.
- **[OpenVINS](https://github.com/rpng/open_vins)**:
  - State-of-the-art open-source platform for visual-inertial research with extensive benchmarking tools, camera-IMU calibration, and multi-camera support.
- **[Kimera](https://github.com/MIT-SPARK/Kimera)**:
  - Open-source C++ library for real-time metric-semantic simultaneous localization and mapping (VIO + robust pose graph + 3D mesh reconstruction + 3D semantic segmentation).
