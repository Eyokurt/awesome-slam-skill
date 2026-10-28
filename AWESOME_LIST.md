# Awesome-SLAM [![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome)
A curated list of SLAM resources

## Stay Tuned for Constant Updates

> [!TIP]
> **Offline PDF Archive Available:** All associated research papers, mathematical tutorials, and benchmarks referenced across this repository have been downloaded locally into [`papers/`](papers/) (111 PDFs, ~519 MB).
> You can browse the full categorized index in [**PAPERS_CATALOG.md**](PAPERS_CATALOG.md) or use the direct `[📄 Local PDF]` links attached below.


> Last updated: Mar. 14th, 2021. 

The repo is maintained by [Youjie Xia](https://github.com/YoujieXia). The repo mainly summarizes the awesome repositories relevant to SLAM/VO on GitHub, including those on the PC end, the mobile end and some learner-friendly tutorials. 

Regrading awesome SLAM papers, please refer to [**Awesome-SLAM-Papers**](https://github.com/YoujieXia/Awesome-SLAM-Papers).

If you want to know more about dependencies/packages of SLAM systems, please refer to [Installing Dependencies on Ubuntu 16.04 LTS towards SLAM Projects (Updating)](Misc/2018-03-10-Installing-Dependencies-on-Ubuntu-towards-SLAM-Projects.md).

If you think this repo is useful, please ***watch***, ***star*** or ***fork*** it!

Welcome to contribute to this repo, if you are interested in SLAM! Feel free to creat a pull request or contact me.


> Note: Name Format - `repository name: one-sentence introduction` (with link to the corresponding repo)

------

## Table of Contents

- [1. Hot SLAM Repos on GitHub](#HotRepos)
- [2. Visual SLAM](#VSLAM)
	- [2.1 Framework](#VFramework)
	- [2.2 Monocular](#VMono)
	- [2.3 Stereo](#VStereo)
	- [2.4 RGBD](#VRGBD)
	- [2.5 Others](#VOthers)
- [3. Visual Inertial SLAM](#VISLAM)
	- [3.1 Framework](#VIFramework)
	- [3.2 Monocular](#VIMono)
	- [3.3 Stereo](#VIStereo)
	- [3.4 RGBD](#VIRGBD)
	- [3.5 Others](#VIOthers)
- [4. LIDAR based SLAM](#LIDARSLAM)
	- [4.1 Framework](#LFramework)
	- [4.2 Others](#LOthers)
- [5. Learning based SLAM](#LSLAM)
	- [5.1 Survey](#LSurvey)
	- [5.2 Others](#LOthers5)
	- [5.3 Deep Features](#DeepFeat)
	- [5.4 Semantic SLAM](#Semantic)
- [6. Mobile End SLAM](#MSLAM)
	- [6.1 Visual SLAM](#MV)
	- [6.2 Visual Inertial SLAM](#MVI)
	- [6.3 Augmented Reality](#MAR)
	- [6.4 Others](#MOthers)
- [7. Datasets](#Datasets)
- [8. Tutorials](#Tutorials)
	- [8.1 3D Vision](#3DVision)
	- [8.2 Robotics](#Robotics)
	- [8.3 Lie Algebra and Lie Groups](#Lie)
	- [8.4 Optimization Techniques](#Opt)
	- [8.5 Calibration](#Calibr)
	- [8.6 RANSAC](#RANSAC)
- [9. Selected Blogs](#Blogs)
- [10. Research Groups](#Groups)
- [11. Community](#Community)
- [12. Additional Curated SLAM Papers Archive (Awesome-SLAM-Papers)](#PapersArchive)
- [📑 **Comprehensive Offline PDF Catalog (111 Papers / 519 MB)**](PAPERS_CATALOG.md)

------
<a name="HotRepos"></a>
## 1. Hot SLAM Repos on GitHub
- [Awesome-SLAM: Resources and Resource Collections of SLAM](https://github.com/YoujieXia/Awesome-SLAM)
- [awesome-slam: A curated list of awesome SLAM tutorials, projects and communities.](https://github.com/kanster/awesome-slam) — [📄 **Local PDF** (5.8MB)](papers/01_Hot_SLAM_Repos/awesome-slam_A_curated_list_of_awesome-slam_A_curated_list_of_awesome_SLAM_tutori.pdf)
- [SLAM: learning SLAM,curse,paper and others](https://github.com/liulinbo/slam)
- [A list of current SLAM (Simultaneous Localization and Mapping) / VO (Visual Odometry) algorithms](https://github.com/kafendt/List-of-SLAM-VO-algorithms) — [📄 **Local PDF** (0.2MB)](papers/01_Hot_SLAM_Repos/A_list_of_current_SLAM_(Simult_A_list_of_current_SLAM_(Simultaneous_Localization.pdf)
- [awesome-visual-slam: The list of vision-based SLAM / Visual Odometry open source, blogs, and papers](https://github.com/tzutalin/awesome-visual-slam) — [📄 **Local PDF** (5.6MB)](papers/01_Hot_SLAM_Repos/awesome-visual-slam_The_list_o_awesome-visual-slam_The_list_of_vision-based_SLAM.pdf)
- [Lee-SLAM-source: SLAM 开发学习资源与经验分享](https://github.com/AlbertSlam/Lee-SLAM-source)
    * 📄 [**PDF: Current trends in SLAM** (5.8MB)](papers/01_Hot_SLAM_Repos/Lee-SLAM-source_SLAM_开发学习资源与经验_Lee-SLAM-source_SLAM_开发学习资源与经验分享_-_Current_trends.pdf)
    * 📄 [**PDF: The scaling problem** (15.5MB)](papers/01_Hot_SLAM_Repos/Lee-SLAM-source_SLAM_开发学习资源与经验_Lee-SLAM-source_SLAM_开发学习资源与经验分享_-_The_scaling_pro.pdf)
    * 📄 [**PDF: slamtute1--The Essential Algorithms** (0.5MB)](papers/01_Hot_SLAM_Repos/Lee-SLAM-source_SLAM_开发学习资源与经验_Lee-SLAM-source_SLAM_开发学习资源与经验分享_-_slamtute1--The.pdf)
- [awesome-SLAM-list](https://github.com/OpenSLAM/awesome-SLAM-list)
- [VIO-Resources](https://github.com/hhmaizi/VIO-Resources/blob/master/resources4vio)

------
<a name="VSLAM"></a>
## 2. Visual SLAM
<a name="VFramework"></a>
### 2.1 Framework 
- [OpenVSLAM: A Versatile Visual SLAM Framework](https://github.com/OpenVSLAM-Community/openvslam)
    * 📄 [**PDF: ProSLAM** (0.9MB)](papers/02_Visual_SLAM/OpenVSLAM_A_Versatile_Visual_S_OpenVSLAM_A_Versatile_Visual_SLAM_Framework_-_ProS.pdf)
    * 📄 [**PDF: ORB-SLAM2** (4.0MB)](papers/02_Visual_SLAM/OpenVSLAM_A_Versatile_Visual_S_OpenVSLAM_A_Versatile_Visual_SLAM_Framework_-_ORB-.pdf)
    * 📄 [**PDF: <img src="https://raw.githubusercontent.com/stella-cv/docs/main/docs/img/teaser.png" width="640px">** (4.6MB)](papers/02_Visual_SLAM/OpenVSLAM_A_Versatile_Visual_S_OpenVSLAM_A_Versatile_Visual_SLAM_Framework_-_img.pdf)
    * 📄 [**PDF: UcoSLAM** (4.2MB)](papers/02_Visual_SLAM/OpenVSLAM_A_Versatile_Visual_S_OpenVSLAM_A_Versatile_Visual_SLAM_Framework_-_UcoS.pdf)
- [OpenSfM: Open source Structure-from-Motion pipeline](https://github.com/mapillary/OpenSfM)
- [GSLAM (A General SLAM Framework and BenchMark)](https://github.com/zdzhaoyong/GSLAM)
- [ScaViSLAM](https://github.com/strasdat/ScaViSLAM)

<a name="VMono"></a>
### 2.2 Monocular
- [ORB_SLAM: A Versatile and Accurate Monocular SLAM](https://github.com/raulmur/ORB_SLAM) — [📄 **Local PDF** (1.1MB)](papers/02_Visual_SLAM/ORB_SLAM_A_Versatile_and_Accur_ORB_SLAM_A_Versatile_and_Accurate_Monocular_SLAM_-.pdf)
- [LSD-SLAM: Large-Scale Direct Monocular SLAM](https://github.com/tum-vision/lsd_slam)
- [DSO: Direct Sparse Odometry](https://github.com/JakobEngel/dso)
- [LDSO: Direct Sparse Odometry with Loop Closure](https://github.com/tum-vision/LDSO)
- [SVO: Semi-direct Visual Odometry](https://github.com/uzh-rpg/rpg_svo) — [📄 **Local PDF** (1.4MB)](papers/02_Visual_SLAM/SVO_Semi-direct_Visual_Odometr_SVO_Semi-direct_Visual_Odometry.pdf)
- [PTAM: Parallel Tracking and Mapping](https://github.com/Oxford-PTAM/PTAM-GPL)
- [LPVO: Line and Plane based Visual Odometry](https://github.com/PyojinKim/LPVO)
- [LCSD_SLAM: Loosely-Coupled Semi-Direct Monocular SLAM](https://github.com/sunghoon031/LCSD_SLAM) — [📄 **Local PDF** (0.1MB)](papers/02_Visual_SLAM/LCSD_SLAM_Loosely-Coupled_Semi_LCSD_SLAM_Loosely-Coupled_Semi-Direct_Monocular_SL.pdf)
- [CCM-SLAM: Robust and Efficient Centralized Collaborative Monocular SLAM for Robotic Teams](https://github.com/VIS4ROB-lab/ccm_slam) — [📄 **Local PDF** (11.1MB)](papers/02_Visual_SLAM/CCM-SLAM_Robust_and_Efficient_CCM-SLAM_Robust_and_Efficient_Centralized_Collabor.pdf)

<a name="VStereo"></a>
### 2.3 Stereo
- [ORB_SLAM2](https://github.com/raulmur/ORB_SLAM2)
- [ORBSLAM2_with_pointcloud_map](https://github.com/gaoxiang12/ORBSLAM2_with_pointcloud_map)
- [PL-SLAM: a Stereo SLAM System through the Combination of Points and Line Segments](https://github.com/rubengooj/pl-slam) — [📄 **Local PDF** (3.3MB)](papers/02_Visual_SLAM/PL-SLAM_a_Stereo_SLAM_System_t_PL-SLAM_a_Stereo_SLAM_System_through_the_Combinati.pdf)
- [StVO-PL: Stereo Visual Odometry by combining point and line segment features](https://github.com/rubengooj/StVO-PL)
- [PL-SVO](https://github.com/rubengooj/pl-svo)
- [stereo-dso: Direct Sparse Odometry with Stereo Cameras](https://github.com/JiatianWu/stereo-dso)
- [S-PTAM: Stereo Parallel Tracking and Mapping](https://github.com/lrse/sptam), Python implementation: [stereo_ptam](https://github.com/uoip/stereo_ptam)
- [Robust Stereo Visual Odometry](https://github.com/famoreno/stereo-vo)
- [OV²SLAM: A Fully Online and Versatile Visual SLAM for Real-Time Applications](https://github.com/ov2slam/ov2slam) — [📄 **Local PDF** (1.9MB)](papers/02_Visual_SLAM/OV²SLAM_A_Fully_Online_and_Ver_OV²SLAM_A_Fully_Online_and_Versatile_Visual_SLAM_f.pdf)

<a name="VRGBD"></a>
### 2.4 RGBD
- [Dense Visual Odometry and SLAM](https://github.com/tum-vision/dvo_slam)
- [DVO](https://github.com/tum-vision/dvo):Dense Visual Odometry
- [PlanarSLAM](https://github.com/yanyan-li/PlanarSLAM)
    * 📄 [**PDF: RGB-D** (1.4MB)](papers/02_Visual_SLAM/PlanarSLAM_PlanarSLAM_-_RGB-D.pdf)
    * 📄 [**PDF: Monocular** (4.1MB)](papers/02_Visual_SLAM/PlanarSLAM_PlanarSLAM_-_Monocular.pdf)
- [badslam](https://github.com/ETH3D/badslam): Bundle Adjusted Direct RGB-D SLAM
- [RESLAM](https://github.com/fabianschenk/RESLAM): A real-time robust edge-based SLAM system — [📄 **Local PDF** (9.7MB)](papers/02_Visual_SLAM/RESLAM_RESLAM_-_pdf.pdf)
- [VDO-SLAM](https://github.com/halajun/VDO_SLAM): A Visual Dynamic Object-aware SLAM System
    * 📄 [**PDF: VDO-SLAM_VDO-SLAM_(arXiv_2007.13993).pdf** (3.0MB)](papers/02_Visual_SLAM/VDO-SLAM_VDO-SLAM_(arXiv_2007.13993).pdf)
    * 📄 [**PDF: VDO-SLAM_VDO-SLAM_(arXiv_2002.08584).pdf** (8.5MB)](papers/02_Visual_SLAM/VDO-SLAM_VDO-SLAM_(arXiv_2002.08584).pdf)
    * 📄 [**PDF: VDO-SLAM_VDO-SLAM_(arXiv_2005.11052).pdf** (6.1MB)](papers/02_Visual_SLAM/VDO-SLAM_VDO-SLAM_(arXiv_2005.11052).pdf)
- [REVO](https://github.com/fabianschenk/REVO): Robust Edge-based Visual Odometry 

<a name="VOthers"></a>
### 2.5 Others
- [CubeSLAM](https://github.com/shichaoy/cube_slam): Monocular 3D Object Detection and SLAM — [📄 **Local PDF** (2.8MB)](papers/02_Visual_SLAM/CubeSLAM_CubeSLAM_-_PDF.pdf)
- [se2lam](https://github.com/izhengfan/se2lam): Visual-Odometric On-SE(2) Localization and Mapping
- [se2clam](https://github.com/izhengfan/se2clam): SE(2)-Constrained Localization and Mapping by Fusing Odometry and Vision
- [BreezySLAM](https://github.com/simondlevy/BreezySLAM): Simple, efficient, open-source package for Simultaneous Localization and Mapping in Python, Matlab, Java, and C++
- [MultiCol-SLAM](https://github.com/urbste/MultiCol-SLAM): a multi-fisheye camera SLAM — [📄 **Local PDF** (1.9MB)](papers/02_Visual_SLAM/MultiCol-SLAM_MultiCol-SLAM_-_Paper.pdf)
- [Event-based Stereo Visual Odometry](https://github.com/HKUST-Aerial-Robotics/ESVO)
    * 📄 [**PDF: Event-based Stereo Visual Odometry** (5.0MB)](papers/02_Visual_SLAM/Event-based_Stereo_Visual_Odom_Event-based_Stereo_Visual_Odometry_-_Event-based_S.pdf)
    * 📄 [**PDF: Semi-dense 3D Reconstruction with a Stereo Event Camera** (1.8MB)](papers/02_Visual_SLAM/Event-based_Stereo_Visual_Odom_Event-based_Stereo_Visual_Odometry_-_Semi-dense_3D.pdf)

------
<a name="VISLAM"></a>
## 3. Visual Inertial SLAM
<a name="VIFramework"></a>
### 3.1 Framework 
- [maplab](https://github.com/ethz-asl/maplab): An open visual-inertial mapping framework. — [📄 **Local PDF** (5.9MB)](papers/03_Visual_Inertial_SLAM/maplab_maplab_-_Paper.pdf)
- [ORB-SLAM3](https://github.com/UZ-SLAMLab/ORB_SLAM3): An Accurate Open-Source Library for Visual, Visual-Inertial and Multi-Map SLAM — [📄 **Local PDF** (1.6MB)](papers/03_Visual_Inertial_SLAM/ORB-SLAM3_ORB-SLAM3_-_PDF.pdf)
- [VINS-Fusion](https://github.com/HKUST-Aerial-Robotics/VINS-Fusion): An optimization-based multi-sensor state estimator
- [Kimera](https://github.com/MIT-SPARK/Kimera): an open-source library for real-time metric-semantic localization and mapping
    * 📄 [**PDF: **Incremental Visual-Inertial 3D Mesh Generation with Structural Regularities**** (3.1MB)](papers/03_Visual_Inertial_SLAM/Kimera_Kimera_-_Incremental_Visual-Inertial_3D_Mesh_Gener.pdf)
    * 📄 [**PDF: **3D Dynamic Scene Graphs: Actionable Spatial Perception with Places, Objects, and Humans**** (7.7MB)](papers/03_Visual_Inertial_SLAM/Kimera_Kimera_-_3D_Dynamic_Scene_Graphs_Actionable_Spatia.pdf)
    * 📄 [**PDF: **Kimera: from SLAM to Spatial Perception with 3D Dynamic Scene Graphs**** (44.7MB)](papers/03_Visual_Inertial_SLAM/Kimera_Kimera_-_Kimera_from_SLAM_to_Spatial_Perception_wi.pdf)
- [OpenVINS](https://github.com/rpng/open_vins): An open source platform for visual-inertial navigation research

<a name="VIMono"></a>
### 3.2 Monocular
- [OKVIS](https://github.com/ethz-asl/okvis_ros): Open Keyframe-based Visual-Inertial SLAM (ROS Version)
- [ROVIO](https://github.com/ethz-asl/rovio): Robust Visual Inertial Odometry
- [R-VIO](https://github.com/rpng/R-VIO): Robocentric Visual-Inertial Odometry
- [LARVIO](https://github.com/PetWorm/LARVIO): A lightweight, accurate and robust monocular visual inertial odometry based on Multi-State Constraint Kalman Filter — [📄 **Local PDF** (0.7MB)](papers/03_Visual_Inertial_SLAM/LARVIO_LARVIO_-_Mingyang_Li.pdf)
- [msckf_mono](https://github.com/daniilidis-group/msckf_mono) — [📄 **Local PDF** (4.3MB)](papers/03_Visual_Inertial_SLAM/msckf_mono_Zhu_Event-Based_Visual_Inertial_CVPR_2017_paper.pdf)
- LearnVIORB: Visual Inertial SLAM based on ORB-SLAM2 [(ROS Version)](https://github.com/jingpang/LearnVIORB), [LearnViORB_NOROS (Non-ROS Version)](https://github.com/OpenSLAM/LearnViORB_NOROS/tree/master/master/LearnVIORB_NOROS)
- [PVIO](https://github.com/zju3dv/PVIO): Robust and Efficient Visual-Inertial Odometry with Multi-plane Priors — [📄 **Local PDF** (0.8MB)](papers/03_Visual_Inertial_SLAM/PVIO_PVIO_-_Robust_and_Efficient_Visual-Inertial_Odomet.pdf)
- [PL-VIO](https://github.com/HeYijia/PL-VIO): monocular visual inertial system with point and line features
- [PL-VINS](https://github.com/cnqiangfu/PL-VINS): Real-Time Monocular Visual-Inertial SLAM with Point and Line Features — [📄 **Local PDF** (4.9MB)](papers/03_Visual_Inertial_SLAM/PL-VINS_PL-VINS_-_PL-VINS.pdf)
- [Adaptive Line and Point Feature-based Visual Inertial Odometry for Robust Localization in Indoor Environments](https://github.com/ankh88324/ALVIO)
- [REBiVO](https://github.com/JuanTarrio/rebvo): Realtime Edge Based Inertial Visual Odometry for a Monocular Camera
- [Co-VINS](https://github.com/qintonguav/Co-VINS): Collaborative Localization for Multiple Monocular Visual-Inertial Systems — [📄 **Local PDF** (2.5MB)](papers/03_Visual_Inertial_SLAM/Co-VINS_Co-VINS_-_Technical_report.pdf)

<a name="VIStereo"></a>
### 3.3 Stereo
- [msckf_vio](https://github.com/KumarRobotics/msckf_vio): Robust Stereo Visual Inertial Odometry for Fast Autonomous Flight — [📄 **Local PDF** (4.1MB)](papers/03_Visual_Inertial_SLAM/msckf_vio_msckf_vio_-_https_arxiv.org_abs_1712.00036.pdf)
- [OKVIS](https://github.com/ethz-asl/okvis): Open Keyframe-based Visual-Inertial SLAM
- [Basalt](https://gitlab.com/VladyslavUsenko/basalt): Visual-Inertial Mapping with Non-Linear Factor Recovery
- [ICE-BA](https://github.com/baidu/ICE-BA): Incremental, Consistent and Efficient Bundle Adjustment for Visual-Inertial SLAM — [📄 **Local PDF** (2.6MB)](papers/03_Visual_Inertial_SLAM/ICE-BA_ICE-BA_-_PDF.pdf)
- [ORBSLAM_DWO](https://github.com/JzHuai0108/ORB_SLAM): stereo + inertial input based on ORB_SLAM
- [VI-Stereo-DSO](https://github.com/RonaldSun/VI-Stereo-DSO)
- [Semi-Dense Direct Visual Inertial Odometry](https://github.com/KumarRobotics/sdd_vio)
- [LearnVIORBnorosgai2](https://github.com/ZuoJiaxing/LearnVIORBnorosgai2): Visual Inertial SLAM based on ORB-SLAM2 (Non-ROS Version)
- [ygz-stereo-inertial](https://github.com/gaoxiang12/ygz-stereo-inertial): a stereo-inertial visual odometry

<a name="VIRGBD"></a>
### 3.4 RGBD

<a name="VIOthers"></a>
### 3.5 Others
- [X Inertial-aided Visual Odometry](https://github.com/ucla-vision/xivo)
    * 📄 [**PDF: X_Inertial-aided_Visual_Odomet_X_Inertial-aided_Visual_Odometry_(arXiv_1807.11130.pdf** (3.4MB)](papers/03_Visual_Inertial_SLAM/X_Inertial-aided_Visual_Odomet_X_Inertial-aided_Visual_Odometry_(arXiv_1807.11130.pdf)
    * 📄 [**PDF: X_Inertial-aided_Visual_Odomet_X_Inertial-aided_Visual_Odometry.pdf** (1.1MB)](papers/03_Visual_Inertial_SLAM/X_Inertial-aided_Visual_Odomet_X_Inertial-aided_Visual_Odometry.pdf)

------
<a name="LIDARSLAM"></a>
## 4. LIDAR based SLAM
<a name="LFramework"></a>
### 4.1 Framework
- [Cartographer](https://github.com/cartographer-project/cartographer)
- [LOAM-Livox](https://github.com/hku-mars/loam_livox): A robust LiDAR Odometry and Mapping (LOAM) package for Livox-LiDAR
    * 📄 [**PDF: A fast, complete, point cloud based loop closure for LiDAR odometry and mapping** (6.1MB)](papers/04_LIDAR_based_SLAM/LOAM-Livox_LOAM-Livox_-_A_fast,_complete,_point_cloud_based_l.pdf)
    * 📄 [**PDF: Loam_livox: A fast, robust, high-precision LiDAR odometry and mapping package for LiDARs of small FoV** (7.3MB)](papers/04_LIDAR_based_SLAM/LOAM-Livox_LOAM-Livox_-_Loam_livox_A_fast,_robust,_high-preci.pdf)

<a name="LOthers"></a>
### 4.2 Others
- [FAST-LIO](https://github.com/hku-mars/FAST_LIO)
    * 📄 [**PDF: Bubble Planner** (6.5MB)](papers/04_LIDAR_based_SLAM/FAST-LIO_FAST-LIO_-_Bubble_Planner.pdf)
    * 📄 [**PDF: FAST-LIO: A Fast, Robust LiDAR-inertial Odometry Package by Tightly-Coupled Iterated Kalman Filter** (4.9MB)](papers/04_LIDAR_based_SLAM/FAST-LIO_FAST-LIO_-_FAST-LIO_A_Fast,_Robust_LiDAR-inertial.pdf)
- [LOL](https://github.com/RozDavid/LOL): Lidar-only Odometry and Localization in 3D point cloud maps — [📄 **Local PDF** (2.2MB)](papers/04_LIDAR_based_SLAM/LOL_LOL_-_arXiv.pdf)
- [PyICP SLAM](https://github.com/gisbi-kim/PyICP-SLAM): Full-python LiDAR SLAM using ICP and Scan Context
- [LIO-SAM](https://github.com/TixiaoShan/LIO-SAM): Tightly-coupled Lidar Inertial Odometry via Smoothing and Mapping
- [LeGO-LOAM](https://github.com/RobustFieldAutonomyLab/LeGO-LOAM): Lightweight and Ground-Optimized Lidar Odometry and Mapping on Variable Terrain
- [hdl_graph_slam](https://github.com/koide3/hdl_graph_slam): 3D LIDAR-based Graph SLAM
- [A-LOAM](https://github.com/HKUST-Aerial-Robotics/A-LOAM): Advanced implementation of LOAM
- [LIO-mapping: A Tightly Coupled 3D Lidar and Inertial Odometry and Mapping Approach](https://github.com/hyye/lio-mapping)
- [SC-LeGO-LOAM](https://github.com/irapkaist/SC-LeGO-LOAM): LiDAR SLAM: Scan Context + LeGO-LOAM
- [Fast LOAM](https://github.com/wh200720041/floam): Fast and Optimized Lidar Odometry And Mapping for indoor/outdoor localization
- [SuMa](https://github.com/jbehley/SuMa): Surfel-based Mapping using 3D Laser Range Data
- [LINS](https://github.com/ChaoqinRobotics/LINS---LiDAR-inertial-SLAM): LiDAR-inertial-SLAM
- [ISCLOAM](https://github.com/wh200720041/iscloam): Intensity Scan Context based full SLAM implementation for autonomous driving — [📄 **Local PDF** (1.5MB)](papers/04_LIDAR_based_SLAM/ISCLOAM_ISCLOAM_-_paper.pdf)
- [MULLS](https://github.com/YuePanEdward/MULLS): Versatile LiDAR SLAM via Multi-metric Linear Least Square — [📄 **Local PDF** (4.3MB)](papers/04_LIDAR_based_SLAM/MULLS_MULLS_-_[Preprint_Paper.pdf)

------
<a name="LSLAM"></a>
## 5. Learning based SLAM
The SLAM algorithms using conventional methods are listed above by default. The section is to list SLAM algos using learning based methods.

<a name="LSurvey"></a>
### 5.1 Survey
- [A collection of deep learning based localization models](https://github.com/changhao-chen/deep-learning-localization-mapping)
- [3D-Reconstruction-with-Deep-Learning-Methods](https://github.com/natowi/3D-Reconstruction-with-Deep-Learning-Methods)
    * 📄 [**PDF: 3D-Reconstruction-with-Deep-Le_3D-Reconstruction-with-Deep-Learning-Methods_(arXi.pdf** (5.3MB)](papers/05_Learning_based_SLAM/3D-Reconstruction-with-Deep-Le_3D-Reconstruction-with-Deep-Learning-Methods_(arXi.pdf)
    * 📄 [**PDF: 3D-Reconstruction-with-Deep-Le_3D-Reconstruction-with-Deep-Learning-Methods.pdf** (2.4MB)](papers/05_Learning_based_SLAM/3D-Reconstruction-with-Deep-Le_3D-Reconstruction-with-Deep-Learning-Methods.pdf)

<a name="LOthers5"></a>
### 5.2 Others
- [TLIO](https://github.com/CathIAS/TLIO): Tight Learned Inertial Odometry
- [Unsupervised Learning of Monocular Depth Estimation and Visual Odometry with Deep Feature Reconstruction](https://github.com/Huangying-Zhan/Depth-VO-Feat)
- [SuperPoint + ORB_SLAM2](https://github.com/KinglittleQ/SuperPoint_SLAM)
- [VINet](https://github.com/HTLife/VINet): Visual-Inertial Odometry as a Sequence-to-Sequence Learning Problem
- [DeepSFM](https://github.com/weixk2015/DeepSFM): Structure From Motion Via Deep Bundle Adjustment — [📄 **Local PDF** (2.1MB)](papers/05_Learning_based_SLAM/DeepSFM_DeepSFM_-_paper.pdf)
- [Unsupervised Monocular Visual-inertial Odometry Network](https://github.com/Ironbrotherstyle/UnVIO)
- [Semantic SLAM](https://github.com/hridaybavle/semantic_slam)
- [CNN-DSO](https://github.com/muskie82/CNN-DSO): Direct Sparse Odometry with CNN Depth Prediction — [📄 **Local PDF** (0.9MB)](papers/05_Learning_based_SLAM/CNN-DSO_CNN-DSO_-_CNN-SVO_paper.pdf)
- [CNN-SVO](https://github.com/yan99033/CNN-SVO)
- [KFNet](https://github.com/zlthinker/KFNet): Learning Temporal Camera Relocalization using Kalman Filtering
- [Unsupervised Depth Completion from Visual Inertial Odometry](https://github.com/alexklwong/unsupervised-depth-completion-visual-inertial-odometry) — [📄 **Local PDF** (8.1MB)](papers/05_Learning_based_SLAM/Unsupervised_Depth_Completion_Unsupervised_Depth_Completion_from_Visual_Inertial.pdf)
- [The Perfect Match](https://github.com/zgojcic/3DSmoothNet): 3D Point Cloud Matching with Smoothed Densities
- [Beyond Photometric Loss for Self-Supervised Ego-Motion Estimation](https://github.com/hlzz/DeepMatchVO) — [📄 **Local PDF** (9.3MB)](papers/05_Learning_based_SLAM/Beyond_Photometric_Loss_for_Se_Beyond_Photometric_Loss_for_Self-Supervised_Ego-Mo.pdf)
- [M^3SNet](https://github.com/whubaichuan/M3VSNet): Unsupervised Multi-metric Multi-view Stereo Network
- [Deep EKF VIO](https://github.com/lichunshang/deep_ekf_vio)
- [Active Neural SLAM](https://github.com/devendrachaplot/Neural-SLAM)
- [DeepFactors](https://github.com/jczarnowski/DeepFactors) — [📄 **Local PDF** (3.3MB)](papers/05_Learning_based_SLAM/DeepFactors_DeepFactors_-_DeepFactors_Real-Time_Probabilistic.pdf)
- [OverlapNet](https://github.com/PRBonn/OverlapNet): Loop Closing for 3D LiDAR-based SLAM
- [SO-Net](https://github.com/lijx10/SO-Net): Self-Organizing Network for Point Cloud Analysis
- [Geometry-Aware Learning of Maps for Camera Localization](https://github.com/NVlabs/geomapnet)
- [DeepV2D](https://github.com/princeton-vl/DeepV2D): Video to Depth with Differentiable Structure from Motion — [📄 **Local PDF** (7.8MB)](papers/05_Learning_based_SLAM/DeepV2D_DeepV2D_-_DeepV2D_Video_to_Depth_with_Differentiab.pdf)
- [PVN3D](https://github.com/ethnhe/PVN3D): A Deep Point-wise 3D Keypoints Voting Network for 6DoF Pose Estimation
    * 📄 [**PDF: PDF** (1.9MB)](papers/05_Learning_based_SLAM/PVN3D_PVN3D_-_PDF.pdf)
    * 📄 [**PDF: **FFB6D**** (1.7MB)](papers/05_Learning_based_SLAM/PVN3D_PVN3D_-_FFB6D.pdf)
    * 📄 [**PDF: PVN3D** (5.4MB)](papers/05_Learning_based_SLAM/PVN3D_PVN3D_-_PVN3D.pdf)
- [DeepMVS](https://github.com/phuang17/DeepMVS): Learning Multi-View Stereopsis
- [Epipolar Transformers](https://github.com/yihui-he/epipolar-transformers)
    * 📄 [**PDF: Epipolar Transformers** (6.7MB)](papers/05_Learning_based_SLAM/Epipolar_Transformers_Epipolar_Transformers_-_Epipolar_Transformers.pdf)
    * 📄 [**PDF: 3D Hand Shape and Pose from Images in the Wild** (3.7MB)](papers/05_Learning_based_SLAM/Epipolar_Transformers_Epipolar_Transformers_-_3D_Hand_Shape_and_Pose_fro.pdf)
    * 📄 [**PDF: Learning to Estimate 3D Hand Pose from Single RGB Images** (0.8MB)](papers/05_Learning_based_SLAM/Epipolar_Transformers_Epipolar_Transformers_-_Learning_to_Estimate_3D_Ha.pdf)
- [DF-VO](https://github.com/Huangying-Zhan/DF-VO): Depth and Flow for Visual Odometry
    * 📄 [**PDF: Visual Odometry Revisited: What Should Be Learnt?** (2.7MB)](papers/05_Learning_based_SLAM/DF-VO_DF-VO_-_Visual_Odometry_Revisited_What_Should_Be_L.pdf)
    * 📄 [**PDF: DF-VO: What Should Be Learnt for Visual Odometry?** (6.0MB)](papers/05_Learning_based_SLAM/DF-VO_DF-VO_-_DF-VO_What_Should_Be_Learnt_for_Visual_Odo.pdf)
- [DeepTAM](https://github.com/lmb-freiburg/deeptam): Deep Tracking and Mapping

<a name="DeepFeat"></a>
### 5.3 Deep Features
- [GCNv2 SLAM](https://github.com/jiexiong2016/GCNv2_SLAM): Real-time SLAM system with deep features — [📄 **Local PDF** (3.1MB)](papers/05_Learning_based_SLAM/GCNv2_SLAM_GCNv2_SLAM_-_GCNv2_Efficient_Correspondence_Predic.pdf)
- [FCGF](https://github.com/chrischoy/FCGF): Fully Convolutional Geometric Features: Fast and accurate 3D features for registration and correspondence
    * 📄 [**PDF: Deep Global Registration, CVPR'20 Oral** (2.8MB)](papers/05_Learning_based_SLAM/FCGF_FCGF_-_Deep_Global_Registration,_CVPR'20_Oral.pdf)
    * 📄 [**PDF: Learning multiview 3D point cloud registration, CVPR'20** (8.6MB)](papers/05_Learning_based_SLAM/FCGF_FCGF_-_Learning_multiview_3D_point_cloud_registrat.pdf)
- [Deep Image Retrieval](https://github.com/naver/deep-image-retrieval)
    * 📄 [**PDF: End-to-end Learning of Deep Visual Representations for Image Retrieval** (7.6MB)](papers/05_Learning_based_SLAM/Deep_Image_Retrieval_Deep_Image_Retrieval_-_End-to-end_Learning_of_Deep.pdf)
    * 📄 [**PDF: Learning with Average Precision: Training Image Retrieval with a Listwise Loss** (8.4MB)](papers/05_Learning_based_SLAM/Deep_Image_Retrieval_Deep_Image_Retrieval_-_Learning_with_Average_Preci.pdf)
    * 📄 [**PDF: Fine-tuning CNN Image Retrieval with No Human Annotation** (7.4MB)](papers/05_Learning_based_SLAM/Deep_Image_Retrieval_Deep_Image_Retrieval_-_Fine-tuning_CNN_Image_Retri.pdf)
    * 📄 [**PDF: Particular object retrieval with integral max-pooling of CNN activations** (9.5MB)](papers/05_Learning_based_SLAM/Deep_Image_Retrieval_Deep_Image_Retrieval_-_Particular_object_retrieval.pdf)
- [Key.Net](https://github.com/axelBarroso/Key.Net): Keypoint Detection by Handcrafted and Learned CNN Filters

<a name="Semantic"></a>
### 5.4 Semantic SLAM
- [SuMa++](https://github.com/PRBonn/semantic_suma): Efficient LiDAR-based Semantic SLAM — [📄 **Local PDF** (14.7MB)](papers/05_Learning_based_SLAM/SuMa++_SuMa++_-_paper.pdf)
- [DS-SLAM](https://github.com/ivipsourcecode/DS-SLAM) — [📄 **Local PDF** (1.7MB)](papers/05_Learning_based_SLAM/DS-SLAM_DS-SLAM_(arXiv_1809.08379).pdf)
- [Probabilistic Data Association via Mixture Models for Robust Semantic SLAM](https://github.com/MarineRoboticsGroup/mixtures_semantic_slam) — [📄 **Local PDF** (4.1MB)](papers/05_Learning_based_SLAM/Probabilistic_Data_Association_Probabilistic_Data_Association_via_Mixture_Models.pdf)
- [SIVO](https://github.com/navganti/SIVO): Semantically Informed Visual Odometry and Mapping
    * 📄 [**PDF: here** (1.8MB)](papers/05_Learning_based_SLAM/SIVO_SIVO_-_here.pdf)
    * 📄 [**PDF: PDF** (6.7MB)](papers/05_Learning_based_SLAM/SIVO_SIVO_-_PDF.pdf)
- [orbslam_semantic_nav_ros, RGBD](https://github.com/MRwangmaomao/semantic_slam_nav_ros)
- [Pop-up SLAM](https://github.com/shichaoy/pop_up_slam): Semantic Monocular Plane SLAM for Low-texture Environments — [📄 **Local PDF** (3.0MB)](papers/05_Learning_based_SLAM/Pop-up_SLAM_Pop-up_SLAM_-_PDF.pdf)
- [Semantic SLAM using ROS, ORB SLAM, PSPNet101](https://github.com/1989Ryan/Semantic_SLAM)

------
<a name="MobileSLAM"></a>
## 6. Mobile End SLAM
The SLAM algorithms running on PC end are listed above by default. The section is to list references and resources for SLAM algo dev on mobile end.

<a name="MV"></a>
### 6.1 Visual SLAM
- [ORB_SLAM-iOS](https://github.com/ygx2011/ORB_SLAM-IOS)
- [ORB_SLAM2-iOS](https://github.com/ygx2011/ORB_SLAM2-IOS)
- [MobileSLAM](https://github.com/xorthat/MobileSLAM): LSD SLAM on Mobile Phone
- [SLAM_AR_Android](https://github.com/Martin20150405/SLAM_AR_Android)

<a name="MVI"></a>
### 6.2 Visual Inertial SLAM
- [VINS-Mobile](https://github.com/HKUST-Aerial-Robotics/VINS-Mobile): Monocular Visual-Inertial State Estimator on Mobile Phones
    * 📄 [**PDF: technical report** (3.9MB)](papers/06_Mobile_End_SLAM/VINS-Mobile_VINS-Mobile_-_technical_report.pdf)
    * 📄 [**PDF: **Monocular Visual-Inertial State Estimation for Mobile Augmented Reality**** (18.2MB)](papers/06_Mobile_End_SLAM/VINS-Mobile_VINS-Mobile_-_Monocular_Visual-Inertial_State_Esti.pdf)

<a name="MAR"></a>
### 6.3 Augmented Reality
- [Awesome-ARKit](https://github.com/olucurious/Awesome-ARKit)
- [Awesome-ARCore](https://github.com/olucurious/Awesome-ARCore)
- [MixedRealityToolkit-Unity](https://github.com/microsoft/MixedRealityToolkit-Unity)
- [arcore-android-sdk](https://github.com/google-ar/arcore-android-sdk)
- [OpenARK](https://github.com/augcog/OpenARK)
- [opencv-markerless-AR-Mobile](https://github.com/meiroo/opencv-markerless-AR-Mobile)

#### 6.3.1 Depth Image API with iPhone 7 Plus (or newer)
- [DepthAPISampleForiOS11](https://github.com/fromkk/DepthAPISampleForiOS11)
- [AVDepthCamera](https://github.com/faceowener/AVDepthCamera)
- [ios11-depth-map-test](https://github.com/xiangcong/ios11-depth-map-test)
- [ARCore Depth Lab](https://github.com/googlesamples/arcore-depth-lab): Depth API Samples for Unity
- [AR-Depth](https://github.com/facebookresearch/AR-Depth): Fast Depth Densification for Occlusion-Aware Augmented Reality
- [AR-Depth-cpp](https://github.com/muskie82/AR-Depth-cpp): C++ implementation of Fast Depth Densification for Occlusion-aware Augmented Reality (SIGGRAPH-Asia 2018)

<a name="MOthers"></a>
### 6.4 Others
- [Microsoft Computer Vision API](https://github.com/microsoft/Cognitive-Vision-Android): Android Client Library & Sample
- [GPUImage](https://github.com/BradLarson/GPUImage): An open source iOS framework for GPU-based image and video processing

------
<a name="Datasets"></a>
## 7. Datasets
- [Awesome SLAM Datasets](https://github.com/youngguncho/awesome-slam-datasets) — [📄 **Local PDF** (0.5MB)](papers/07_Datasets/Awesome_SLAM_Datasets_Awesome_SLAM_Datasets_-_[Paper.pdf)
- [Awesome Robotics Datasets](https://github.com/sunglok/awesome-robotics-datasets): A collection of useful datasets for robotics and computer vision


- [TUM - Monocular Visual Odometry Dataset](https://vision.cs.tum.edu/data/datasets/mono-dataset), [[code](https://github.com/tum-vision/mono_dataset_code)]
- [ADVIO](https://github.com/AaltoVision/ADVIO): An Authentic Dataset for Visual-Inertial Odometry — [📄 **Local PDF** (4.2MB)](papers/07_Datasets/ADVIO_ADVIO_(arXiv_1807.09828).pdf)

------
<a name="Tutorials"></a>
## 8. Tutorials

- 视觉SLAM十四讲/14 lectures on visual SLAM，[English Version](https://github.com/gaoxiang12/slambook-en)，[中文版](https://github.com/gaoxiang12/slambook)
- [Practice of the SlamBook](https://github.com/leftthomas/SlamBook)
- [GraphSLAM_tutorials_code](https://github.com/HeYijia/GraphSLAM_tutorials_code)
- [SLAM 开发学习资源与经验分享](https://github.com/AlbertSlam/Lee-SLAM-source)
    * 📄 [**PDF: Current trends in SLAM** (5.8MB)](papers/01_Hot_SLAM_Repos/Lee-SLAM-source_SLAM_开发学习资源与经验_Lee-SLAM-source_SLAM_开发学习资源与经验分享_-_Current_trends.pdf)
    * 📄 [**PDF: The scaling problem** (15.5MB)](papers/01_Hot_SLAM_Repos/Lee-SLAM-source_SLAM_开发学习资源与经验_Lee-SLAM-source_SLAM_开发学习资源与经验分享_-_The_scaling_pro.pdf)
    * 📄 [**PDF: slamtute1--The Essential Algorithms** (0.5MB)](papers/01_Hot_SLAM_Repos/Lee-SLAM-source_SLAM_开发学习资源与经验_Lee-SLAM-source_SLAM_开发学习资源与经验分享_-_slamtute1--The.pdf)
- [Visual SLAM/VIO 算法笔记](https://blog.csdn.net/MulinB/article/details/53421864)

<a name="3DVision"></a>
### 8.1 3D Vision
- [An Invitation to 3D Vision: A Tutorial for Everyone](https://github.com/sunglok/3dv_tutorial) — [📄 **Local PDF** (4.0MB)](papers/08_Tutorials/An_Invitation_to_3D_Vision_A_T_An_Invitation_to_3D_Vision_A_Tutorial_for_Everyone.pdf)
- [Computer Vision/Geometric Fundamentals of SLAM](Misc/Geometric-Fundamentals-of-SLAM.md)

#### 8.1.1 Libs
- [opengv](https://github.com/laurentkneip/opengv)
- [Geometry Central](https://github.com/nmwsharp/geometry-central)
- [vilib](https://github.com/uzh-rpg/vilib): CUDA Visual Library by RPG — [📄 **Local PDF** (3.0MB)](papers/08_Tutorials/vilib_vilib_-_IROS_2020_paper.pdf)
- [Vitis Vision Library](https://github.com/Xilinx/Vitis_Libraries/tree/master/vision)
- [OpenGR: A C++ library for 3D Global Registration](https://github.com/STORM-IRIT/OpenGR)
- [OpenCP](https://github.com/norishigefukushima/OpenCP): Computational photography library. The code is parallelized by using SIMD intrinsics and multi-threading.


<a name="Robotics"></a>
### 8.2 Robotics
- [RoboticSystemsBook](https://github.com/krishauser/RoboticSystemsBook)
- [MATLABRobotics](https://github.com/AtsushiSakai/MATLABRobotics): MATLAB sample codes for mobile robot navigation
- [Kindr](https://github.com/ANYbotics/kindr): Kinematics and Dynamics for Robotics — [📄 **Local PDF** (0.6MB)](papers/08_Tutorials/Kindr_Kindr_-_cheat_sheet.pdf)
- [Sensor Fusion in ROS](https://github.com/methylDragon/ros-sensor-fusion-tutorial): An in-depth step-by-step tutorial for implementing sensor fusion with robot_localization
- [fuse](https://github.com/locusrobotics/fuse): The fuse stack provides a general architecture for performing sensor fusion live on a robot. Some possible applications include state estimation, localization, mapping, and calibration.
- [GPU Computing in Robotics](https://github.com/JanuszBedkowski/gpu_computing_in_robotics)

<a name="Lie"></a>
### 8.3 Lie Algebra and Lie Groups
- [Lie groups for Computer Vision](http://ethaneade.com/lie_groups.pdf) — [📄 **Local PDF** (0.1MB)](papers/08_Tutorials/Lie_groups_for_Computer_Vision_lie_groups.pdf)
- [Lie groups for 2D and 3D Transformations](http://ethaneade.com/lie.pdf) — [📄 **Local PDF** (0.3MB)](papers/08_Tutorials/Lie_groups_for_2D_and_3D_Trans_Lie_groups_for_2D_and_3D_Transformations.pdf)
- [Hermite Splines in Lie Groups as Products of Geodesics](http://ethaneade.com/lie_spline.pdf) — [📄 **Local PDF** (0.1MB)](papers/08_Tutorials/Hermite_Splines_in_Lie_Groups_Hermite_Splines_in_Lie_Groups_as_Products_of_Geode.pdf)
- [LieTransformer](https://github.com/anonymous-code-0/lie-transformer)

#### 8.3.1 Libs
- [Sophus](https://github.com/strasdat/Sophus): C++ implementation of Lie Groups using Eigen
- [manif](https://github.com/artivis/manif): A small C++11 header-only library for Lie theory
    * 📄 [**PDF: manif_manif_(arXiv_1410.1465).pdf** (0.5MB)](papers/08_Tutorials/manif_manif_(arXiv_1410.1465).pdf)
    * 📄 [**PDF: manif_manif_(arXiv_2312.07555).pdf** (0.6MB)](papers/08_Tutorials/manif_manif_(arXiv_2312.07555).pdf)
    * 📄 [**PDF: reference paper** (1.5MB)](papers/08_Tutorials/manif_manif_-_reference_paper.pdf)

<a name="Opt"></a>
### 8.4 Optimization Techniques 
- [Gauss-Newton/Levenberg-Marquardt Optimization](http://ethaneade.com/optimization.pdf) — [📄 **Local PDF** (0.1MB)](papers/08_Tutorials/Gauss-Newton_Levenberg-Marquar_Gauss-Newton_Levenberg-Marquardt_Optimization.pdf)
- [How a Kalman filter works, in pictures](http://www.bzarg.com/p/how-a-kalman-filter-works-in-pictures/)
- [卡爾曼濾波 (Kalman Filter)](http://silverwind1982.pixnet.net/blog/post/167680859)
- [翻譯 Understanding the Basis of the Kalman Filter Via a Simple and Intuitive Derivation](http://silverwind1982.pixnet.net/blog/post/171132644)

#### 8.4.1 Libs
- [ceres-solver](https://github.com/ceres-solver/ceres-solver): A large scale non-linear optimization library
- [g2o](https://github.com/RainerKuemmerle/g2o): A General Framework for Graph Optimization — [📄 **Local PDF** (1.0MB)](papers/08_Tutorials/g2o_g2o_-_g2o_A_General_Framework_for_Graph_Optimizati.pdf)
- [GTSAM](https://github.com/borglab/gtsam): Georgia Tech Smoothing and Mapping Library
    * 📄 [**PDF: GTSAM_p06.pdf** (1.7MB)](papers/08_Tutorials/GTSAM_p06.pdf)
    * 📄 [**PDF: GTSAM_Dellaert17fnt.pdf** (23.0MB)](papers/08_Tutorials/GTSAM_Dellaert17fnt.pdf)
	- [miniSAM](https://github.com/dongjing3309/minisam): A general and flexible factor graph non-linear least square optimization framework — [📄 **Local PDF** (0.9MB)](papers/08_Tutorials/miniSAM_miniSAM_(arXiv_1909.00903).pdf)
	- [AprilSAM](https://github.com/xipengwang/AprilSAM): Real-time Smoothing and Mapping
	- [GTSAM Tutorial Examples](https://github.com/dongjing3309/gtsam-examples)
- [AMGCL](https://github.com/ddemidov/amgcl): C++ library for solving large sparse linear systems with algebraic multigrid method — [📄 **Local PDF** (3.9MB)](papers/08_Tutorials/AMGCL_AMGCL_-_arxiv.pdf)
- [Armadillo](https://gitlab.com/conradsnicta/armadillo-code): fast C++ library for linear algebra & scientific computing
- [IFOPT](https://github.com/ethz-adrl/ifopt): An Eigen-based, light-weight C++ Interface to Nonlinear Programming Solvers (Ipopt, Snopt)
- [LBFGS++](https://github.com/yixuan/LBFGSpp): A header-only C++ library for L-BFGS and L-BFGS-B algorithms
- [OptimLib](https://github.com/kthohr/optim): a lightweight C++ library of numerical optimization methods for nonlinear functions — [📄 **Local PDF** (10.6MB)](papers/08_Tutorials/OptimLib_OptimLib_-_here.pdf)
- [PoseLib](https://github.com/vlarsson/PoseLib): a collection of minimal solvers for camera pose estimation
- [fpm](https://github.com/MikeLankamp/fpm): C++ header-only fixed-point math library

<a name="Calibr"></a>
### 8.5 Calibration
#### 8.5.1 Libs
- [kalibr](https://github.com/rpng/kalibr_allan): The Kalibr visual-inertial calibration toolbox
	- [kalibr_allan](https://github.com/rpng/kalibr_allan): IMU Allan standard deviation charts for use with Kalibr and inertial kalman filters
- [Accurate geometric camera calibration with generic camera models](https://github.com/puzzlepaint/camera_calibration)
- [LI-Calib](https://github.com/APRIL-ZJU/lidar_IMU_calib): Targetless Calibration of LiDAR-IMU System Based on Continuous-time Batch Estimation — [📄 **Local PDF** (3.8MB)](papers/08_Tutorials/LI-Calib_LI-Calib_-_[arxiv.pdf)
- [Online Photometric Calibration](https://github.com/tum-vision/online_photometric_calibration)
- [IMU-TK](https://github.com/Kyle-ak/imu_tk): Inertial Measurement Unit ToolKit
- [crisp](https://github.com/hovren/crisp): Camera-to-IMU calibration and synchronization toolbox
- [VersaVIS](https://github.com/ethz-asl/versavis): An Open Versatile Multi-Camera Visual-Inertial Sensor Suite

<a name="RANSAC"></a>
### 8.6 RANSAC
- [RansacLib](https://github.com/tsattler/RansacLib): Template-based implementation of RANSAC and its variants in C++


------
<a name="Blogs"></a>
## 9. Selected Blogs
- [The Future of Real-Time SLAM and Deep Learning vs SLAM](http://www.computervisionblog.com/2016/01/why-slam-matters-future-of-real-time.html)
- [IMU Data Fusing: Complementary, Kalman, and Mahony Filter](http://www.olliw.eu/2013/imu-data-fusing/)

------
<a name="Groups"></a>
## 10. Research Groups
TBA

------
<a name="Community"></a>
## 11. Community
- [PaoPaoRobot - 泡泡机器人](https://github.com/PaoPaoRobot)
- [OpenSLAM.org](https://github.com/OpenSLAM-org)
- [OpenVSLAM-Community](https://github.com/OpenVSLAM-Community)

------
<a name="PapersArchive"></a>
## 12. Additional Curated SLAM Papers Archive (Awesome-SLAM-Papers)
The following seminal SLAM papers were curated from [Awesome-SLAM-Papers](https://github.com/YoujieXia/Awesome-SLAM-Papers) and downloaded locally into [`papers/`](papers/):

### 3. Visual-Inertial SLAM & Odometry
- **A General Optimization-based Framework for Local Odometry Estimation with Multiple Sensors** — [📄 **Local PDF** (3.2MB)](papers/03_Visual_Inertial_SLAM/A_General_Optimization-based_F_A_General_Optimization-based_Framework_for_Local_O.pdf) | [Original Source](https://arxiv.org/pdf/1901.03638.pdf)
- **A General Optimization-based Framework for Global Pose Estimation with Multiple Sensors** — [📄 **Local PDF** (5.0MB)](papers/03_Visual_Inertial_SLAM/A_General_Optimization-based_F_A_General_Optimization-based_Framework_for_Global.pdf) | [Original Source](https://arxiv.org/pdf/1901.03642.pdf)
- **Information Sparsification in Visual-Inertial Odometry** — [📄 **Local PDF** (3.7MB)](papers/03_Visual_Inertial_SLAM/Information_Sparsification_in_Information_Sparsification_in_Visual-Inertial_Odom.pdf) | [Original Source](http://www.cs.cmu.edu/~kaess/pub/Hsiung18iros.pdf)
- **Visual-Inertial Monocular SLAM with Map Reuse** — [📄 **Local PDF** (0.6MB)](papers/03_Visual_Inertial_SLAM/Visual-Inertial_Monocular_SLAM_Visual-Inertial_Monocular_SLAM_with_Map_Reuse.pdf) | [Original Source](https://arxiv.org/pdf/1610.05949.pdf)
- **On-Manifold Preintegration for Real-Time Visual-Inertial Odometry** — [📄 **Local PDF** (3.6MB)](papers/03_Visual_Inertial_SLAM/On-Manifold_Preintegration_for_On-Manifold_Preintegration_for_Real-Time_Visual-In.pdf) | [Original Source](https://arxiv.org/pdf/1512.02363.pdf)
- **VINS-Mono: A Robust and Versatile Monocular Visual-Inertial State Estimator** — [📄 **Local PDF** (4.2MB)](papers/03_Visual_Inertial_SLAM/VINS-Mono_A_Robust_and_Versati_VINS-Mono_A_Robust_and_Versatile_Monocular_Visual-.pdf) | [Original Source](https://arxiv.org/pdf/1708.03852.pdf)
- **Challenges in Monocular Visual Odometry: Photometric Calibration, Motion Bias and Rolling Shutter Effect** — [📄 **Local PDF** (5.5MB)](papers/03_Visual_Inertial_SLAM/Challenges_in_Monocular_Visual_Challenges_in_Monocular_Visual_Odometry_Photometri.pdf) | [Original Source](https://arxiv.org/pdf/1705.04300.pdf)
- **A Benchmark Comparison of Monocular Visual-Inertial Odometry Algorithms for Flying Robots** — [📄 **Local PDF** (0.4MB)](papers/03_Visual_Inertial_SLAM/A_Benchmark_Comparison_of_Mono_A_Benchmark_Comparison_of_Monocular_Visual-Inertia.pdf) | [Original Source](http://rpg.ifi.uzh.ch/docs/ICRA18_Delmerico.pdf)
- **The TUM VI Benchmark for Evaluating Visual-Inertial Odometry** — [📄 **Local PDF** (3.1MB)](papers/03_Visual_Inertial_SLAM/The_TUM_VI_Benchmark_for_Evalu_The_TUM_VI_Benchmark_for_Evaluating_Visual-Inertia.pdf) | [Original Source](https://arxiv.org/pdf/1804.06120.pdf)

### 9. Surveys & Overviews
- **Past, Present, and Future of Simultaneous Localization and Mapping: Toward the Robust-Perception Age** — [📄 **Local PDF** (0.8MB)](papers/09_Surveys/Past,_Present,_and_Future_of_S_Past,_Present,_and_Future_of_Simultaneous_Localiza.pdf) | [Original Source](http://rpg.ifi.uzh.ch/docs/TRO16_cadena.pdf)
- **Visual-Inertial Navigation: A Concise Review** — [📄 **Local PDF** (0.3MB)](papers/09_Surveys/Visual-Inertial_Navigation_A_C_Visual-Inertial_Navigation_A_Concise_Review.pdf) | [Original Source](https://arxiv.org/pdf/1906.02650.pdf)

### 10. Other SLAM Papers & Miscellaneous
- **Visual SLAM: Why Bundle Adjust?** — [📄 **Local PDF** (1.3MB)](papers/10_Misc/Visual_SLAM_Why_Bundle_Adjust_1902.03747.pdf) | [Original Source](https://arxiv.org/pdf/1902.03747.pdf)
- **GSLAM: A General SLAM Framework and Benchmark** — [📄 **Local PDF** (1.4MB)](papers/10_Misc/GSLAM_A_General_SLAM_Framework_GSLAM_A_General_SLAM_Framework_and_Benchmark.pdf) | [Original Source](https://arxiv.org/pdf/1902.07995.pdf)
- **Loosely-Coupled Semi-Direct Monocular SLAM** — [📄 **Local PDF** (1.4MB)](papers/10_Misc/Loosely-Coupled_Semi-Direct_Mo_Loosely-Coupled_Semi-Direct_Monocular_SLAM.pdf) | [Original Source](https://arxiv.org/pdf/1807.10073.pdf)
