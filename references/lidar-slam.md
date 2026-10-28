# LiDAR-Based SLAM & Odometry Reference Guide

LiDAR (Light Detection and Ranging) provides direct 3D range measurements independent of environmental lighting. This reference covers 2D/3D LiDAR odometry, tightly-coupled LiDAR-Inertial Odometry (LIO), scan matching, and loop closure.

---

## 1. Algorithmic Foundations: Scan Matching & Registration

### 1.1 ICP (Iterative Closest Point)
Finds the rigid transformation $T = [R \mid \mathbf{t}]$ that aligns source point cloud $\mathcal{P}$ to target $\mathcal{Q}$:
$$T^* = \arg\min_{R, \mathbf{t}} \sum_{i} \|(R \mathbf{p}_i + \mathbf{t}) - \mathbf{q}_i\|^2$$
- **Point-to-Plane ICP**: Instead of point-to-point distance, minimize distance along the surface normal $\mathbf{n}_i$ of the target surface:
  $$E_{plane} = \sum_{i} \left( \left((R \mathbf{p}_i + \mathbf{t}) - \mathbf{q}_i\right) \cdot \mathbf{n}_i \right)^2$$
  *Advantage*: Converges much faster with fewer iterations, especially on planar structures (walls, floors, roads).

### 1.2 NDT (Normal Distributions Transform)
Partitions space into a 3D voxel grid. Each voxel models local point distributions as a 3D Gaussian $(\boldsymbol{\mu}_i, \Sigma_i)$. Source points are aligned by maximizing the likelihood of fitting into the Gaussian mixture.
*Advantage*: Very fast for large outdoor scenes without requiring nearest-neighbor search for every point.

### 1.3 Feature Extraction in LiDAR: Edge vs Planar Points
Modern LOAM-based methods extract geometrical features directly based on local point roughness / curvature $c$:
$$c = \frac{1}{|\mathcal{S}| \cdot \|\mathbf{p}_i\|} \left\| \sum_{j \in \mathcal{S}, j \neq i} (\mathbf{p}_i - \mathbf{p}_j) \right\|$$
- High curvature $c > c_{thresh}$ $\implies$ **Edge / Corner features** (sharp corners, tree trunks, poles).
- Low curvature $c < c_{thresh}$ $\implies$ **Planar features** (flat ground, road, building facades).
- Matching edge points to lines and planar points to planes reduces compute by $>90\%$ compared to dense ICP.

---

## 2. Evolution of the LOAM Family

```
[LOAM (Zhang & Singh, 2014)]
  │  • Split into 10Hz Odometry & 1Hz Mapping
  │  • Point-to-line & Point-to-plane residual formulation
  ▼
[LeGO-LOAM (Shan & Englot, 2018)]
  │  • Ground-plane segmentation via range image projection
  │  • 2-step Levenberg-Marquardt optimization (z, pitch, roll first; x, y, yaw second)
  │  • Embedded platform efficiency (saves 60% CPU)
  ▼
[LIO-SAM (Shan et al., 2020)]
  │  • Tightly-coupled LiDAR-Inertial Odometry via Factor Graph (GTSAM)
  │  • IMU preintegration provides high-frequency motion undistortion
  │  • Scan-to-local-map registration + GPS / loop closure integration
  ▼
[FAST-LIO2 (Xu et al., HKU, 2022)]
  │  • Eliminates feature extraction; operates directly on raw points
  │  • Incremental kd-tree (ikd-tree) for dynamic point insertion and deletion
  │  • Iterated Extended Kalman Filter (IEKF) on manifold
  │  • >50 Hz odometry on solid-state (Livox) and spinning (Velodyne/Ouster) LiDARs
```

---

## 3. Leading Frameworks Comparison

| Framework | Sensor Inputs | Backend Solver | Feature Method | Real-time Rate | Primary Use Case |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **[FAST-LIO](https://github.com/hku-mars/FAST_LIO)** | 3D LiDAR + IMU | Iterated EKF on $SE(3)$ | Direct raw points (ikd-tree) | $>50\text{ Hz}$ | Micro-aerial vehicles, handheld scanners, solid-state LiDARs |
| **[LIO-SAM](https://github.com/TixiaoShan/LIO-SAM)** | 3D LiDAR + IMU (+ GPS) | Factor Graph (GTSAM) | Edge + Planar features | $10\text{–}20\text{ Hz}$ | Ground autonomous vehicles, campus mapping |
| **[LeGO-LOAM](https://github.com/RobustFieldAutonomyLab/LeGO-LOAM)** | 3D LiDAR (+ IMU optional) | Gauss-Newton 2-step | Segmented ground + edges | $10\text{ Hz}$ | Low-power embedded UGV navigation on variable terrain |
| **[Cartographer](https://github.com/cartographer-project/cartographer)** | 2D / 3D LiDAR + IMU | Branch-and-bound scan matching + Ceres | Probability Grid / Submaps | Real-time | Indoor industrial robotics, 2D floor plans |
| **[SuMa / SuMa++](https://github.com/PRBonn/semantic_suma)** | 3D LiDAR (+ RangeNet++) | Gauss-Newton on Surfel Map | Range image spherical projection | $15\text{–}25\text{ Hz}$ | Long-term urban autonomous driving with dynamic object removal |

---

## 4. Loop Closure in LiDAR SLAM: Scan Context

Traditional vision uses visual Bag-of-Words (DBoW2), which fails in LiDAR due to lack of visual texture.

**[Scan Context](https://github.com/irapkaist/SC-LeGO-LOAM)** (Kim & Kim):
1. **Spatial Representation**: Bin the point cloud into a 2D matrix of azimuth ($N_s$ sectors) and radial distance ($N_r$ rings).
2. **Value Representation**: Each bin stores the maximum height ($z$-value) among points falling into that bin:
   $$I(r, \theta) = \max_{p \in \mathcal{P}_{r,\theta}} (p_z)$$
3. **Rotational Invariance**: Shift columns of the matrix to identify yaw rotation.
4. **Fast Retrieval**: Compute a 1D Ring Key descriptor for $O(1)$ kd-tree candidate searching, then compute column distance for the best match.

---

## 5. Critical Engineering Guidelines

1. **Motion Distortion Removal (Deskewing)**:
   - Mechanical spinning LiDARs rotate continuously during robot motion; points collected at the beginning of a sweep are offset from points collected at the end.
   - *Fix*: Use high-frequency IMU linear velocity and angular rate to interpolate the exact 6-DoF sensor pose for every individual point timestamp, transforming all points into the sweep-start frame.
2. **Degeneracy Detection**:
   - In long straight tunnels, corridors, or highways, point-to-plane normals are parallel; motion along the longitudinal axis becomes unobservable ($J^T J$ has near-zero eigenvalues).
   - *Fix*: Monitor the minimum eigenvalue $\lambda_{\min}(J^T \Sigma^{-1} J)$. If below threshold, constrain the degenerate direction using wheel odometry or IMU acceleration prior.
