# Awesome SLAM Skill (`awesome-slam`)

[![Antigravity Skill](https://img.shields.io/badge/Antigravity-Skill-blue.svg)](https://github.com/Eyokurt/awesome-slam-skill)
[![License: CC0-1.0](https://img.shields.io/badge/License-CC0_1.0-lightgrey.svg)](LICENSE)
[![Offline Archive](https://img.shields.io/badge/Offline%20Papers-111%20PDFs%20(~519MB)-brightgreen.svg)](references/papers-catalog.md)

An expert engineering skill and architectural knowledge base for **Simultaneous Localization and Mapping (SLAM)**, **Visual Odometry (VO)**, **Visual-Inertial Odometry (VIO)**, and **LiDAR-Inertial Odometry (LIO)**.

This skill equips AI coding assistants and robotic engineers with authoritative decision matrices, mathematical foundations (Lie theory, factor graphs), sensor calibration workflows, and an offline, curated repository of **111 peer-reviewed research papers and technical documents**.

---

> **Quick Links:**
> - 📘 **[Main Skill Instructions (SKILL.md)](SKILL.md)**
> - 📚 **[Curated Papers Catalog - 111 Papers (PAPERS_CATALOG.md)](PAPERS_CATALOG.md)**
> - 🔗 **[Complete SLAM Repositories & Resource Index (AWESOME_LIST.md)](AWESOME_LIST.md)**

---

## 🎯 Target Application Domains

This skill provides domain-specific pipelines, algorithm selection, and debugging recipes across major robotics and computer vision industries:

### 1. Autonomous Driving & Ground Vehicles (AV / ADAS)
- **Use Cases**: Highway and urban localization, GPS-denied tunnel traversal, lane-level mapping, and dynamic object filtering.
- **Sensor Suites**: Multi-LiDAR (spinning / solid-state) + Stereo Cameras + High-grade IMU + Wheel Odometry + RTK-GPS.
- **Recommended Pipelines**:
  - `FAST-LIO2` / `LIO-SAM`: High-speed, tightly-coupled LiDAR-inertial pose estimation.
  - `SuMa++` / `DS-SLAM`: Semantic surfel and octree mapping with moving vehicle/pedestrian removal.
  - `VINS-Fusion`: Multi-sensor fusion supporting GPS fusion in large-scale road networks.

### 2. Unmanned Aerial Vehicles (UAVs / Drones / Micro-Robotics)
- **Use Cases**: Agile autonomous flight, indoor warehouse drone inspection, search-and-rescue in collapsed buildings, forest canopy navigation.
- **Constraints**: Strict payload limits, limited embedded compute (e.g. Raspberry Pi, Jetson Orin Nano, STM32 FCU), high-dynamic aggressive maneuvers.
- **Recommended Pipelines**:
  - `SVO (Semi-Direct Visual Odometry)`: Low-latency tracking ($>100\text{ fps}$) on minimal CPU power.
  - `ROVIO` / `OpenVINS`: Robust photometric and geometric filtering resilient to rapid roll-pitch maneuvers.
  - `FAST-LIO`: Solid-state Livox LiDAR odometry on lightweight quadrotors.

### 3. Augmented Reality (AR), Virtual Reality (VR) & Spatial Computing
- **Use Cases**: 6-DoF Head and controller tracking (Motion-to-Photon latency $<20\text{ ms}$), room mesh scanning, plane detection for virtual object placement, persistent relocalization across multiple user sessions.
- **Platforms**: Mobile devices (iOS ARKit, Android ARCore), XR headsets (Vision Pro, Meta Quest).
- **Recommended Pipelines**:
  - `ORB-SLAM3`: Atlas multi-map system for instant room relocalization and seamless multi-session mapping.
  - `Kimera`: Metric-semantic 3D mesh reconstruction in real-time.
  - `Pop-up SLAM` / `PlanarSLAM`: Structural plane detection for low-texture indoor walls and tables.

### 4. Warehouse & Industrial Logistics (AGVs / AMRs / Forklifts)
- **Use Cases**: Pallet transport, dense fulfillment center navigation, docking, shelf inspection.
- **Constraints**: Highly repetitive symmetrical aisles, changing floor inventory, mixed human-robot traffic.
- **Recommended Pipelines**:
  - `Cartographer`: High-reliability 2D LiDAR submap optimization and grid mapping.
  - `LeGO-LOAM`: Ground-plane segmented 3D LiDAR odometry for uneven warehouse ramps and outdoor loading docks.
  - `Scan Context`: Geometry-based LiDAR loop closure in textureless, repetitive warehouse corridors.

### 5. Industrial Inspection, Surveying & Digital Twins (BIM)
- **Use Cases**: High-fidelity architectural 3D scanning, bridge and tunnel inspection, construction progress tracking.
- **Recommended Pipelines**:
  - `DSO (Direct Sparse Odometry)`: Photometrically calibrated direct pixel reconstruction without feature extraction bias.
  - `OpenSfM` / `OpenGR`: Structure-from-Motion pipelines and global point cloud registration.
  - `NeRF-SLAM` / `Gaussian Splatting SLAM`: Modern continuous photorealistic 3D novel-view synthesis.

### 6. Underground, Mining & Challenging GPS-Denied Environments
- **Use Cases**: Subterranean cave mapping, dark underground mines, smoke-filled industrial disaster sites.
- **Constraints**: Complete darkness, airborne dust/particles, geometrically degenerate tubular tunnels.
- **Recommended Pipelines**:
  - Tightly coupled LIO (`FAST-LIO`, `LIO-SAM`) combined with thermal imaging or radar.
  - Degeneracy detection algorithms monitoring minimum eigenvalues of the Hessian matrix.

### 7. Medical Robotics & Computer-Assisted Intervention
- **Use Cases**: Endoscopic 3D organ reconstruction, surgical tool localization, minimally invasive surgery.
- **Constraints**: Deformable non-rigid tissues, specular liquid reflections, extremely small camera baseline.
- **Recommended Pipelines**:
  - Monocular direct odometry with photometric deformation compensation.
  - Learning-based depth completion models (`Depth-VO-Feat`, `DF-VO`).

---

## 🛠️ Core Capabilities of the Skill

```
┌────────────────────────────────────────────────────────────────────────┐
│                        awesome-slam Skill Core                         │
├─────────────────────────┬──────────────────────┬───────────────────────┤
│    Decision Matrices    │ Mathematical Engine  │ Engineering Workflows │
├─────────────────────────┼──────────────────────┼───────────────────────┤
│ • Sensor Suite Choice   │ • Lie Groups SO(3)   │ • Spatial Calibration │
│ • Modality Trade-offs   │ • SE(3) Manifolds    │ • Temporal Sync (IMU) │
│ • Failure Mode Analysis │ • Factor Graph Opt   │ • Allan Variance      │
│ • Compute Benchmarking  │ • Schur Complement   │ • Tracking Recovery   │
└─────────────────────────┴──────────────────────┴───────────────────────┘
```

1. **System Design & Algorithm Selection**:
   - Compares feature-based (ORB-SLAM), direct (DSO), semi-direct (SVO), visual-inertial (VINS), and LiDAR (LOAM/LIO) systems.
2. **Mathematical Formulation & Cheat Sheets**:
   - Exact formulations for $SO(3), SE(3)$ exponential/logarithmic maps, adjoint representations, and left/right perturbation models.
   - Non-linear solvers: Gauss-Newton, Levenberg-Marquardt, Huber/Cauchy robust loss functions, and marginalization.
3. **Sensor Calibration & Synchronization Runbooks**:
   - Camera intrinsic models (Pinhole, Kannala-Brandt / Equidistant fisheye).
   - Camera-IMU spatio-temporal calibration procedures with **Kalibr**.
   - IMU Allan variance analysis (noise density and bias random walk).
4. **Offline Academic Library**:
   - 111 peer-reviewed research papers and technical documents organized by domain into local subdirectories.

---

## 📂 Repository & Skill Structure

```
awesome-slam/
├── SKILL.md                          # Main skill instructions, decision matrices & math foundations
├── README.md                         # Repository documentation and domain overview
├── references/                       # In-depth technical reference modules
│   ├── visual-slam.md                # Feature-based vs Direct vs Semi-direct visual SLAM
│   ├── visual-inertial-slam.md       # IMU preintegration, sliding window, MSCKF vs VINS
│   ├── lidar-slam.md                 # Point-to-plane ICP, LOAM family, Scan Context loop closing
│   ├── optimization-and-math.md      # Lie theory, g2o, GTSAM, Ceres, and calibration toolkits
│   ├── learning-and-semantic-slam.md # SuperPoint, dynamic masking, NeRF / 3D Gaussian Splatting
│   └── papers-catalog.md             # Complete tabular index of the 111 downloaded papers
└── papers/                           # 111 Curated PDF documents (~519 MB total)
    ├── 01_Hot_SLAM_Repos/            # Meta-lists and ecosystem overviews (6 PDFs)
    ├── 02_Visual_SLAM/               # Monocular, Stereo, RGB-D papers (20 PDFs)
    ├── 03_Visual_Inertial_SLAM/      # VIO and sensor fusion papers (23 PDFs)
    ├── 04_LIDAR_based_SLAM/          # LiDAR SLAM and LIO papers (7 PDFs)
    ├── 05_Learning_based_SLAM/       # Deep features and semantic SLAM papers (29 PDFs)
    ├── 06_Mobile_End_SLAM/           # Mobile AR and embedded SLAM papers (2 PDFs)
    ├── 07_Datasets/                  # Benchmark and dataset publications (2 PDFs)
    ├── 08_Tutorials/                 # Lie algebra, robotics math, and tutorials (17 PDFs)
    ├── 09_Surveys/                   # Authoritative SLAM survey papers (2 PDFs)
    └── 10_Misc/                      # Supplementary SLAM publications (3 PDFs)
```

---

## 🚀 How to Install & Use in Antigravity

### Option 1: Global Installation (Recommended)
Place the `awesome-slam` directory inside your personal Antigravity config directory:
```powershell
# Windows
Copy-Item -Recurse awesome-slam "$env:USERPROFILE\.gemini\config\skills\"

# Linux / macOS
cp -r awesome-slam ~/.gemini/config/skills/
```

### Option 2: Project-Specific (Workspace) Installation
Drop the directory inside your project's `.agents/skills/` folder:
```powershell
mkdir -p .agents/skills
cp -r awesome-slam .agents/skills/
```

### Triggering the Skill in Prompts
Antigravity will automatically discover and activate this skill when you prompt:
- *"Which SLAM pipeline should I choose for an indoor delivery robot with an RGB-D camera and low-cost IMU?"*
- *"Derive the right Jacobian of SO(3) for camera pose perturbation."*
- *"Help me debug tracking loss in VINS-Mono during rapid pure yaw rotation."*
- *"How do I formulate the Schur complement for marginalizing old keyframes in a sliding window optimizer?"*
- *"Show me the paper and architecture for FAST-LIO2."*

---

## 📜 License & Acknowledgments

- **Repository License**: [Creative Commons Zero v1.0 Universal (CC0 1.0)](LICENSE) Public Domain Dedication for the curated collection, documentation, and skill modules.
- **Upstream Attribution**: Derived from `SilenceOverflow/Awesome-SLAM` (curated by Youjie Xia, MIT License).
- **Academic Attribution**: All research papers and documents in the `papers/` directory belong to their respective authors and institutions (arXiv preprints, IEEE, CVF, Robotics: Science and Systems, ACM).
