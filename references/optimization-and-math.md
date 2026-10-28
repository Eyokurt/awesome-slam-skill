# Optimization, Lie Theory & Calibration Reference Guide

SLAM backend estimation relies on non-linear least squares optimization over Riemannian manifolds, sparse linear algebra, and rigorous sensor calibration.

---

## 1. Lie Groups Cheat Sheet: $SO(3)$ and $SE(3)$

### 1.1 Special Orthogonal Group $SO(3)$
Represents 3D rotations:
- **Group Elements**: $R \in \mathbb{R}^{3 \times 3}, \quad R R^T = I, \quad \det(R) = +1$
- **Lie Algebra $\mathfrak{so}(3)$**: Skew-symmetric 3x3 matrices parameterized by $\boldsymbol{\omega} \in \mathbb{R}^3$:
  $$[\boldsymbol{\omega}]_\times = \begin{bmatrix} 0 & -\omega_3 & \omega_2 \\ \omega_3 & 0 & -\omega_1 \\ -\omega_2 & \omega_1 & 0 \end{bmatrix}$$
- **Logarithmic Map**:
  $$\theta = \arccos\left(\frac{\operatorname{tr}(R) - 1}{2}\right), \quad [\mathbf{a}]_\times = \frac{R - R^T}{2 \sin(\theta)}, \quad \boldsymbol{\omega} = \theta \mathbf{a}$$
- **Adjoint Representation**:
  $$\operatorname{Ad}_R = R, \quad \text{such that} \quad [R \boldsymbol{\omega}]_\times = R [\boldsymbol{\omega}]_\times R^T$$

### 1.2 Special Euclidean Group $SE(3)$
Represents 3D rigid body transformations:
- **Group Element**:
  $$T = \begin{bmatrix} R & \mathbf{t} \\ \mathbf{0}^T & 1 \end{bmatrix} \in \mathbb{R}^{4 \times 4}$$
- **Lie Algebra $\mathfrak{se}(3)$**: Twist vectors $\boldsymbol{\xi} = [\boldsymbol{\rho}, \boldsymbol{\phi}]^T \in \mathbb{R}^6$ ($\boldsymbol{\rho}$: linear translation velocity, $\boldsymbol{\phi}$: angular velocity):
  $$[\boldsymbol{\xi}]_\wedge = \begin{bmatrix} [\boldsymbol{\phi}]_\times & \boldsymbol{\rho} \\ \mathbf{0}^T & 0 \end{bmatrix}$$
- **Adjoint Matrix $\operatorname{Ad}_T \in \mathbb{R}^{6 \times 6}$**:
  $$\operatorname{Ad}_T = \begin{bmatrix} R & [\mathbf{t}]_\times R \\ \mathbf{0} & R \end{bmatrix}$$

---

## 2. Non-Linear Least Squares Solvers

Given cost function $F(\mathbf{x}) = \frac{1}{2} \|\mathbf{f}(\mathbf{x})\|^2$:

### 2.1 Gauss-Newton (GN)
Approximate Hessian via first derivatives: $H \approx J^T J$:
$$(J^T J) \Delta \mathbf{x} = - J^T \mathbf{f}(\mathbf{x})$$
- *Pros*: Fast quadratic convergence near the local minimum without evaluating second derivatives.
- *Cons*: Fails if $J^T J$ is singular or non-positive-definite.

### 2.2 Levenberg-Marquardt (LM)
Interpolates dynamically between Gauss-Newton and Gradient Descent via damping parameter $\lambda$:
$$(J^T J + \lambda D) \Delta \mathbf{x} = - J^T \mathbf{f}(\mathbf{x})$$
- If step decreases residual: accept step, decrease $\lambda$ (behave more like Gauss-Newton).
- If step increases residual: reject step, increase $\lambda$ (behave more like Gradient Descent).

### 2.3 Robust M-Estimators (Outlier Rejection)
Replaces squared error with robust kernel $\rho(s)$ to suppress heavy-tailed outlier residuals:
- **Huber Kernel**:
  $$\rho(s) = \begin{cases} s & s \le k^2 \\ 2k\sqrt{s} - k^2 & s > k^2 \end{cases}$$
- **Cauchy Kernel**:
  $$\rho(s) = c^2 \ln\left(1 + \frac{s}{c^2}\right)$$
- *Implementation*: Scale information matrix by weight $w(s) = \rho'(s)$.

---

## 3. Factor Graph Frameworks Comparison

| Framework | Language | Primary Architecture | Highlights |
| :--- | :--- | :--- | :--- |
| **[GTSAM](https://github.com/borglab/gtsam)** | C++ / Python bindings | Factor Graphs + Bayes Tree (iSAM2) | **iSAM2** (incremental Smoothing and Mapping) updates only affected variables on the Bayes Tree in near $O(1)$ time. Excellent Lie group support. |
| **[g2o](https://github.com/RainerKuemmerle/g2o)** | C++ | Hyper-graph optimization | Extremely fast block solver; standard backend for ORB-SLAM series and many academic pipelines. |
| **[Ceres Solver](https://github.com/ceres-solver/ceres-solver)** | C++ | Non-linear least squares | Developed by Google. Industry-standard automatic differentiation (Dual Numbers / Jet types) and loss functions. |
| **[miniSAM](https://github.com/dongjing3309/minisam)** | C++ / Python | Lightweight factor graph | 10x smaller footprint than GTSAM; ideal for resource-constrained robotics. |

---

## 4. Calibration Toolkits & Procedures

- **[Kalibr](https://github.com/ethz-asl/kalibr)**:
  - Visual-Inertial calibration of camera intrinsics, camera-camera extrinsics, and camera-to-IMU spatial-temporal calibration.
  - Models continuous-time B-splines to estimate inter-sensor time delays down to sub-millisecond precision.
- **[kalibr_allan](https://github.com/rpng/kalibr_allan)** / **[imu_tk](https://github.com/Kyle-ak/imu_tk)**:
  - Allan variance analysis on long static IMU logs (2–6 hours) to determine:
    - Gyroscope / Accelerometer White Noise (Noise Density $N$).
    - Bias Instability (Random Walk $K$).
- **[LI-Calib](https://github.com/APRIL-ZJU/lidar_IMU_calib)**:
  - Targetless continuous-time batch estimation for LiDAR-IMU spatial extrinsics and temporal synchronization.
