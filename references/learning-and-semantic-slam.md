# Learning-Based & Semantic SLAM Reference Guide

This reference outlines the integration of deep learning, neural scene representations, and semantic understanding with classical SLAM pipelines.

---

## 1. Deep Feature Detectors & Descriptors

Classical hand-crafted features (ORB, SIFT, SURF) suffer in low-texture, repetitive, or drastically varying illumination conditions.

| Architecture | Inputs | Key Characteristics | Paper & Reference |
| :--- | :--- | :--- | :--- |
| **SuperPoint** | Single grayscale image | Self-supervised CNN outputting interest points and 256-D descriptors at full resolution; operates at $>30\text{ fps}$ on GPU. | DeTone et al. (CVPR 2018) |
| **Key.Net** | Single grayscale image | Combines shallow handcrafted filters with learned CNN representations for robust keypoint detection under geometric changes. | Barroso-Laguna et al. |
| **FCGF (Fully Convolutional Geometric Features)** | 3D Point Clouds | Computes 32-dimensional rotation-invariant geometric descriptors on 3D sparse voxels (Minkowski Engine). | Choy et al. (ICCV 2019) |
| **Deep Image Retrieval (DIR)** | Image queries | Global ResNet/VGG descriptors with generalized mean (GeM) pooling for large-scale visual loop closure. | Gordo et al. / Naver |

---

## 2. Dynamic Object Filtering & Semantic SLAM

Standard SLAM makes the **static world assumption**: all observed features belong to stationary rigid geometry. Moving objects (pedestrians, vehicles, moving robots) violate this, causing catastrophic trajectory drift.

### 2.1 Pipeline for Dynamic Object Rejection:
```
[Input RGB-D / Stereo Frame]
          │
          ├──► [Mask R-CNN / YOLOv8-Seg] ──► Pixel Semantic Mask (Person, Car, Bicycle)
          │                                           │
          ├──► [Sparse Optical Flow / Epipolar Test] ──┤
          │                                           ▼
          ▼                               [Dynamic Probability Scoring]
[Feature Extraction] ── (Filter Out Dynamic Points) ──► [Clean Static Features]
                                                              │
                                                              ▼
                                                   [Pose Tracking & Mapping]
```

### 2.2 Leading Semantic SLAM Frameworks
- **[DS-SLAM](https://github.com/ivipsourcecode/DS-SLAM)**:
  - Fuses SegNet semantic segmentation with moving consistency checks to filter out dynamic feature points from ORB-SLAM2.
  - Builds an octree semantic map of the static background in real time.
- **[SuMa++](https://github.com/PRBonn/semantic_suma)**:
  - High-performance LiDAR-based semantic SLAM using RangeNet++ on spherical projection images.
  - Dynamically weights LiDAR surfel points according to semantic class consistency to eradicate ghosts caused by passing cars.
- **[Pop-up SLAM](https://github.com/shichaoy/pop_up_slam)**:
  - Recovers 3D plane models from single monocular images in low-texture indoor environments using deep monocular plane estimation.

---

## 3. Deep Learning for Depth & Odometry

- **[Depth-VO-Feat](https://github.com/Huangying-Zhan/Depth-VO-Feat)**:
  - Unsupervised joint learning of monocular depth estimation and visual odometry using deep feature reconstruction loss.
- **[DF-VO (Depth & Flow for VO)](https://github.com/Huangying-Zhan/DF-VO)**:
  - Combines learned single-view depth with learned optical flow to produce scale-consistent monocular visual odometry.
- **[DeepV2D](https://github.com/princeton-vl/DeepV2D)**:
  - Alternates between deep optical flow-based pose estimation and depth map refinement via plane sweep volumes.
- **[OverlapNet](https://github.com/PRBonn/OverlapNet)**:
  - Siamese neural network for 3D LiDAR loop closure that predicts overlap percentage and relative yaw angle from range/normal/depth images.

---

## 4. Modern Frontier: Neural Radiance Fields & 3D Gaussian Splatting in SLAM

While not part of classical 2018–2021 lists, modern SLAM has migrated toward implicit and explicit continuous representations:
1. **NeRF-based SLAM** (e.g. iMAP, NICE-SLAM):
   - Replaces discrete voxel/surfel maps with MLP neural fields optimizing photometric rendering loss.
2. **3D Gaussian Splatting SLAM** (e.g. SplaTAM, MonoGS):
   - Uses explicit 3D Gaussian primitives optimized directly via differentiable tile-based rasterization.
   - Provides real-time tracking ($>30\text{ fps}$) and high-fidelity photorealistic novel-view synthesis.
