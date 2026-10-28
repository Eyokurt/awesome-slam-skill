# Visual SLAM Reference Guide

This reference details the algorithms, design principles, mathematical pipelines, and trade-offs of vision-only SLAM systems (Monocular, Stereo, RGB-D).

---

## 1. Algorithmic Paradigms: Feature-Based vs Direct vs Semi-Direct

### 1.1 Feature-Based Methods
- **Representatives**: **ORB-SLAM (1, 2, 3)**, **PTAM**, **OpenVSLAM**, **PL-SLAM**.
- **Principle**: Extract 2D salient keypoints (corners, edges) and local descriptors (ORB, BRIEF, SIFT), match them across frames, and minimize geometric reprojection error:
  $$E_{geom} = \sum_{i,j} \rho\left(\|\mathbf{p}_{ij} - \pi(R_j \mathbf{P}_i + \mathbf{t}_j)\|^2\right)$$
- **Pros**:
  - Robust against lighting variations and auto-exposure changes.
  - Large baselines supported; efficient Bag-of-Words (DBoW2/3) loop closing and relocalization.
- **Cons**:
  - Feature extraction and matching are computationally expensive.
  - Fails in textureless environments (blank walls, corridors, smooth terrain).

### 1.2 Direct Methods
- **Representatives**: **DSO (Direct Sparse Odometry)**, **LSD-SLAM**, **LDSO**.
- **Principle**: Skip feature detectors and descriptors entirely. Minimize photometric error directly on high-gradient pixel intensities:
  $$E_{photo} = \sum_{p \in \mathcal{N}_p} \left( (I_j[p'] - b_j) - \frac{t_j e^{a_j}}{t_i e^{a_i}} (I_i[p] - b_i) \right)^2$$
  where $a, b$ are affine photometric brightness parameters, and $t$ is exposure time.
- **Pros**:
  - Operates on weak gradients and textureless regions where corner detectors fail.
  - Builds semi-dense / dense point clouds without explicit matching.
- **Cons**:
  - Highly sensitive to rolling shutter distortion and uncalibrated photometric auto-exposure.
  - Requires small inter-frame motion (small baseline); narrow basin of convergence.

### 1.3 Semi-Direct Methods
- **Representatives**: **SVO (Semi-Direct Visual Odometry)**, **PL-SVO**, **LCSD_SLAM**.
- **Principle**: Uses direct image alignment (sparse photometric minimization) for high-rate frame-to-frame tracking, coupled with feature-based bundle adjustment on keyframes for global structure refinement.
- **Pros**: Extremely fast ($>100\text{ fps}$ on embedded CPU); minimal latency for agile quadrotor control.
- **Cons**: Prone to tracking failure on sudden fast rotations; limited relocalization without external loop closer.

---

## 2. Sensor Configurations & Camera Models

### 2.1 Monocular SLAM
- **Scale Ambiguity**: Pure monocular vision cannot determine metric scale (a toy car close up is mathematically indistinguishable from a real car far away).
- **Initialization**: Requires moving the camera to establish an initial baseline and parallax before triangulating the first map:
  - Planar scenes: Compute Homography Matrix $H$.
  - Non-planar scenes: Compute Essential Matrix $E = [t]_\times R$.
  - ORB-SLAM evaluates both $H$ and $E$ in parallel and selects based on a score metric.
- **Scale Drift**: Accumulates non-metric drift over time; loop closing requires $Sim(3)$ (7-DoF) optimization rather than $SE(3)$ (6-DoF).

### 2.2 Stereo SLAM
- **Metric Scale**: Known rigid baseline $b$ enables instant metric depth recovery without parallax delay:
  $$Z = \frac{f \cdot b}{d}, \quad d = u_L - u_R \quad (\text{disparity})$$
- **Close vs Far Points**:
  - Points with $d > d_{thresh}$ are treated as stereo points (depth directly available).
  - Distant points ($d \approx 0$) cannot be measured metrically; they are tracked as monocular points to constrain rotation.

### 2.3 RGB-D SLAM
- **Hardware**: Structured light (e.g. Kinect v1, RealSense) or Time-of-Flight (ToF).
- **Advantages**: Direct per-pixel metric depth up to 5–6 meters; works in pitch darkness.
- **Limitations**: Infrared noise outdoor in bright sunlight; reflection / absorption on glass and black surfaces.

---

## 3. Leading Open-Source Visual SLAM Frameworks

| Repository | Authors / Lab | Key Capabilities & Highlights |
| :--- | :--- | :--- |
| **[ORB-SLAM3](https://github.com/UZ-SLAMLab/ORB_SLAM3)** | Campos, Mur-Artal et al. (Univ. Zaragoza) | Gold-standard for visual/inertial/multi-map SLAM. Pin-hole and fisheye (Kannala-Brandt) support; Atlas multi-map system for seamless relocalization. |
| **[DSO](https://github.com/JakobEngel/dso)** | Engel et al. (TUM / Intel) | Direct Sparse Odometry with full photometric calibration, affine brightness transfer, and joint optimization of camera motion and geometry. |
| **[SVO](https://github.com/uzh-rpg/rpg_svo)** | Forster et al. (UZH RPG) | Semi-direct tracking for micro-aerial vehicles. High-speed optical flow with subpixel accuracy. |
| **[OpenVSLAM](https://github.com/OpenVSLAM-Community/openvslam)** | Sumikura et al. | Versatile modern C++ Visual SLAM framework supporting perspective, fisheye, and equirectangular 360° cameras with Socket.IO web visualizer. |
| **[PL-SLAM](https://github.com/rubengooj/pl-slam)** | Gomez-Ojeda et al. (Univ. Malaga) | Fuses point features (ORB) with line segments (LSD / Line3D) for indoor environments where point features are scarce. |
| **[CubeSLAM](https://github.com/shichaoy/cube_slam)** | Yang & Scherer (CMU) | Generates 3D bounding object cuboids from 2D object detections to build object-level semantic maps. |
| **[VDO-SLAM](https://github.com/halajun/VDO_SLAM)** | Zhang et al. | Visual Dynamic Object-aware SLAM. Tracks camera ego-motion while simultaneously estimating the 6-DoF motion of multiple dynamic objects. |

---

## 4. Key Troubleshooting & Debugging Patterns

1. **Failure on Rapid Shutter Movements**:
   - Cause: Standard rolling shutter cameras expose lines sequentially, causing shear under fast yaw.
   - Solution: Use global shutter cameras; or integrate IMU to predict intra-frame distortion.
2. **Degenerate Planar Scenes**:
   - Cause: Trying to calculate Essential matrix on a planar wall causes mathematical degeneracy.
   - Solution: Use automatic switching between Homography and Essential matrix decomposition (e.g., ORB-SLAM initialization logic).
3. **Loop Closure False Positives**:
   - Cause: Perceptual aliasing in repetitive structures (identical windows, office cubicles).
   - Solution: Enforce geometric consistency checks (RANSAC PnP / epipolar geometry) on top of Bag-of-Words similarity scores before triggering full pose-graph bundle adjustment.
