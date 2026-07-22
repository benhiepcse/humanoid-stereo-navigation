# 🤖 Project — Humanoid Stereo Navigation

---

# 📖 Overview

Humanoid Stereo Navigation is a robotics project that enables a humanoid robot to
perceive its surrounding environment using a stereo camera system and navigate
autonomously toward a target while avoiding obstacles.

This project is the first integration between **Robot Perception** and
**Robot Control**, combining Computer Vision, Depth Estimation, Navigation,
Motion Planning, and Robot Simulation into a complete robotics pipeline.

The robot estimates scene depth from stereo images, reconstructs the
three-dimensional environment, detects obstacles, identifies traversable areas,
plans a collision-free path, and executes movement commands inside a simulated
environment.

Unlike previous projects that focused only on perception, this project transforms
visual information into real robot motion, serving as the bridge between
"seeing" and "acting".

<p align="center">
    <img src="humanoid_stereo_camera.png" width="900">
</p>

---

# 🎯 Project Goal

Build a complete humanoid navigation system capable of

• 🎥 Perceiving the environment using Stereo Vision

• 📏 Estimating depth information

• ☁️ Generating Point Clouds

• 🚧 Detecting obstacles

• 🟢 Identifying free navigation space

• 🗺️ Planning collision-free paths

• 🦿 Controlling humanoid movement

• 🏃 Navigating safely inside Gazebo simulation

---

# 🔄 System Workflow

```text
                    ┌──────────────────────┐
                    │   Stereo Camera      │
                    └──────────┬───────────┘
                               │
                               ▼
                  ┌──────────────────────────┐
                  │ Camera Calibration       │
                  └──────────┬───────────────┘
                             │
                             ▼
                  ┌──────────────────────────┐
                  │ Stereo Rectification     │
                  └──────────┬───────────────┘
                             │
                             ▼
                  ┌──────────────────────────┐
                  │ Depth Estimation         │
                  └──────────┬───────────────┘
                             │
                             ▼
                  ┌──────────────────────────┐
                  │ Point Cloud Generation   │
                  └──────────┬───────────────┘
                             │
                             ▼
                  ┌──────────────────────────┐
                  │ Obstacle Detection       │
                  └──────────┬───────────────┘
                             │
                             ▼
                  ┌──────────────────────────┐
                  │ Free Space Detection     │
                  └──────────┬───────────────┘
                             │
                             ▼
                  ┌──────────────────────────┐
                  │ Local Environment Map    │
                  └──────────┬───────────────┘
                             │
                             ▼
                  ┌──────────────────────────┐
                  │ Path Planning            │
                  └──────────┬───────────────┘
                             │
                             ▼
                  ┌──────────────────────────┐
                  │ Motion Controller        │
                  └──────────┬───────────────┘
                             │
                             ▼
                  ┌──────────────────────────┐
                  │ Gazebo Simulation        │
                  └──────────────────────────┘
```

---

# Data Flow

```text
Stereo Images
      │
      ▼
Depth Map
      │
      ▼
Point Cloud
      │
      ▼
Obstacle Map
      │
      ▼
Free Space
      │
      ▼
Navigation Goal
      │
      ▼
Motion Command
      │
      ▼
Humanoid Robot
```

---

# Module Architecture

```text
                 PERCEPTION (Vision)

 Stereo Camera
        │
        ▼
 Camera Calibration
        │
        ▼
 Stereo Matching
        │
        ▼
 Depth Estimation
        │
        ▼
 Point Cloud
        │
        ▼
 Obstacle Detection
        │
        ▼
 Free Space Detection
        │
        ▼
 Navigation Goal
        │
        ├──────────────────────────────┐
        │                              │
        ▼                              ▼

====================================================
        Shared Navigation Interface
====================================================

        ▲                              ▲
        │                              │

                 CONTROL (Robotics)

 Robot State
        │
        ▼
 Localization
        │
        ▼
 Path Planning
        │
        ▼
 Trajectory Generation
        │
        ▼
 Walking Controller
        │
        ▼
 Velocity Command
        │
        ▼
 Gazebo Simulation
```

---

# Input

```text
Stereo Left Image
Stereo Right Image

Robot Pose

Robot Velocity

IMU

Odometry
```

---

# Output

```text
Depth Map

Point Cloud

Obstacle Map

Free Space Map

Navigation Goal

Velocity Command

Robot Motion
```

---

# Expected Result

```text
The humanoid robot can

✓ Capture stereo images

✓ Estimate scene depth

✓ Build a 3D representation

✓ Detect surrounding obstacles

✓ Identify traversable areas

✓ Plan a collision-free path

✓ Walk safely toward the destination

✓ Complete navigation inside Gazebo simulation
```

---

# Learning Outcome

After completing this project, students will understand

• Stereo Vision

• Depth Estimation

• 3D Point Cloud Generation

• Obstacle Detection

• Local Mapping

• Robot Navigation

• Motion Planning

• Humanoid Walking Control

• ROS2 Integration

• Gazebo Simulation

---

# Project Position in Roadmap

```text
Project 1
Camera Calibration
        │
        ▼
Project 2
Stereo Depth Estimation
        │
        ▼
Project 3
Point Cloud Processing
        │
        ▼
========================================
Project 4
Humanoid Stereo Navigation
========================================
        │
        ▼
Project 5
Visual Servoing

        │
        ▼
Project 6
Object Grasping

        │
        ▼
Project 7
Embodied AI Robot
```

# 👥 Task Distribution

```text
===============================================================
                 PROJECT 4 - HUMANOID STEREO NAVIGATION
===============================================================

                  Total Tasks : 14
        Vision (Hiệp) : 7 Tasks
 Control & Navigation (Thông) : 7 Tasks

===============================================================
```

# Hiệp (Vision & Perception)

```text
+------+---------------------------------------------+------------------------------+
| Task | Module                                      | Output                       |
+------+---------------------------------------------+------------------------------+
|  1   | Stereo Camera Driver                        | Left / Right Images          |
|  2   | Camera Calibration & Rectification          | Calibration Parameters       |
|  3   | Depth Estimation                            | Depth Map                    |
|  4   | Point Cloud Generation                      | Point Cloud                  |
|  5   | Obstacle Detection                          | Obstacle List                |
|  6   | Free Space Detection                        | Free Space Map               |
|  7   | Navigation Goal Generator                   | Navigation Goal              |
+------+---------------------------------------------+------------------------------+
```

Output

```text
Stereo Camera
      │
      ▼
Depth Map
      │
      ▼
Point Cloud
      │
      ▼
Obstacle List
      │
      ▼
Free Space Map
      │
      ▼
Navigation Goal
```

---

# Thông (Control & Navigation)

```text
+------+---------------------------------------------+------------------------------+
| Task | Module                                      | Output                       |
+------+---------------------------------------------+------------------------------+
|  8   | Robot State Estimation                      | Robot State                  |
|  9   | Localization (TF2)                          | Robot Pose                   |
| 10   | Path Planning                               | Global Path                  |
| 11   | Trajectory Generation                       | Robot Trajectory             |
| 12   | Walking Controller                          | Velocity Command             |
| 13   | ROS2 Navigation Node                        | Robot Command                |
| 14   | Gazebo Simulation                           | Robot Motion                 |
+------+---------------------------------------------+------------------------------+
```

Output

```text
Robot State
      │
      ▼
Localization
      │
      ▼
Global Path
      │
      ▼
Trajectory
      │
      ▼
Velocity Command
      │
      ▼
Robot Motion
```

---

# Shared Interface

```text
                 Hiệp (Vision)

Stereo Camera
      │
      ▼
Depth Estimation
      │
      ▼
Point Cloud
      │
      ▼
Obstacle Detection
      │
      ▼
Free Space Detection
      │
      ▼
Navigation Goal
      │
      │
      ├───────────────────────────────┐
      │                               │
      ▼                               ▼

==========================================================
                SHARED INTERFACE
==========================================================

Point Cloud
Obstacle List
Free Space Map
Navigation Goal

==========================================================
      ▲                               ▲
      │                               │
      └───────────────────────────────┘
      │

             Thông (Control)

Robot State
      │
      ▼
Localization
      │
      ▼
Path Planning
      │
      ▼
Trajectory Generation
      │
      ▼
Walking Controller
      │
      ▼
Gazebo Simulation
```

---

# Task Summary

```text
+-------------------------+-------+
| Vision Tasks            |   7   |
+-------------------------+-------+
| Control Tasks           |   7   |
+-------------------------+-------+
| Total Modules           |  14   |
+-------------------------+-------+
| Shared Interface        |   4   |
+-------------------------+-------+

Shared Data

• Point Cloud
• Obstacle List
• Free Space Map
• Navigation Goal
```

# 📂 Folder Architecture

```text
Humanoid-Stereo-Navigation/
|
├── CMakeLists.txt
├── LICENSE
├── README.md
├── assets
│   ├── chessboard
│   ├── icons
│   ├── meshes
│   └── textures
├── config
│   ├── camera.yaml
│   ├── gazebo.yaml
│   ├── navigation.yaml
│   ├── robot.yaml
│   └── stereo.yaml
├── data
│   ├── calibration_result
│   ├── logs
│   ├── map
│   └── trajectory
├── datasets
│   ├── calibration
│   │   ├── left
│   │   └── right
│   ├── maps
│   └── stereo_images
│       ├── left
│       └── right
├── docs
│   ├── architecture
│   ├── diagrams
│   ├── presentations
│   │   └── README.md
│   ├── references
│   │   └── README.md
│   └── reports
├── images
│   ├── banner.png
│   ├── depth_map.png
│   ├── disparity_map.png
│   ├── final_result.png
│   ├── folder_architecture.png
│   ├── free_space_map.png
│   ├── gazebo_simulation.png
│   ├── humanoid_stereo_camera.png
│   ├── navigation_path.png
│   ├── obstacle_map.png
│   ├── point_cloud.png
│   ├── project_overview.png
│   ├── robot_motion.png
│   ├── rviz_visualization.png
│   ├── stereo_input.png
│   └── system_workflow.png
├── include
│   ├── control
│   │   ├── GazeboSimulation.h
│   │   ├── Localization.h
│   │   ├── NavigationNode.h
│   │   ├── PathPlanner.h
│   │   ├── RobotStateEstimator.h
│   │   ├── TrajectoryGenerator.h
│   │   └── WalkingController.h
│   ├── interfaces
│   │   ├── FreeSpaceMap.h
│   │   ├── NavigationGoal.h
│   │   ├── ObstacleList.h
│   │   ├── PointCloudData.h
│   │   └── RobotState.h
│   ├── utils
│   │   ├── FileManager.h
│   │   ├── Logger.h
│   │   └── Timer.h
│   └── vision
│       ├── CameraCalibration.h
│       ├── DepthEstimator.h
│       ├── FreeSpaceDetector.h
│       ├── NavigationGoalGenerator.h
│       ├── ObstacleDetector.h
│       ├── PointCloudGenerator.h
│       └── StereoCameraDriver.h
├── launch
│   ├── gazebo.launch.py
│   ├── navigation.launch.py
│   └── stereo.launch.py
├── models
│   ├── environment
│   ├── furniture
│   ├── humanoid_robot
│   └── obstacles
├── outputs
│   ├── depth
│   ├── disparity
│   ├── free_space
│   ├── logs
│   ├── obstacle_map
│   ├── path
│   ├── pointcloud
│   ├── screenshots
│   └── videos
├── package.xml
├── requirements.txt
├── rviz
│   ├── navigation.rviz
│   ├── pointcloud.rviz
│   └── stereo.rviz
├── scripts
│   ├── calibration.py
│   ├── clean_outputs.sh
│   ├── launch_all.sh
│   ├── run_navigation.sh
│   └── stereo_capture.py
├── src
│   ├── control
│   │   ├── GazeboSimulation.cpp
│   │   ├── Localization.cpp
│   │   ├── NavigationNode.cpp
│   │   ├── PathPlanner.cpp
│   │   ├── RobotStateEstimator.cpp
│   │   ├── TrajectoryGenerator.cpp
│   │   └── WalkingController.cpp
│   ├── main.cpp
│   ├── utils
│   │   ├── FileManager.cpp
│   │   ├── Logger.cpp
│   │   └── Timer.cpp
│   └── vision
│       ├── CameraCalibration.cpp
│       ├── DepthEstimator.cpp
│       ├── FreeSpaceDetector.cpp
│       ├── NavigationGoalGenerator.cpp
│       ├── ObstacleDetector.cpp
│       ├── PointCloudGenerator.cpp
│       └── StereoCameraDriver.cpp
├── tests
│   ├── control
│   ├── integration
│   └── vision
├── tools
│   ├── dataset_downloader.py
│   ├── image_converter.py
│   └── pcd_viewer.py
└── worlds
    ├── indoor.world
    ├── office.world
    └── warehouse.world
```

---

# 📂 Folder Responsibility

| Folder | Owner | Responsibility |
|---------|-------|----------------|
| assets/ | Both | Chessboard (Hiệp), Icons/Meshes/Textures (Thông) |
| config/ | Both | Camera/Stereo (Hiệp), Navigation/Robot/Gazebo (Thông) |
| data/ | Both | Calibration Result (Hiệp), Logs/Map/Trajectory (Thông) |
| datasets/ | Hiệp | Stereo images, Calibration images |
| docs/ | Both | Architecture, Diagrams, Reports |
| images/ | Both | Documentation images and screenshots |
| include/control/ | Thông | Control module headers |
| include/interfaces/ | Both | Shared interfaces |
| include/utils/ | Both | Utility headers |
| include/vision/ | Hiệp | Vision module headers |
| launch/ | Thông | ROS2 launch files |
| models/ | Thông | Robot and environment models |
| outputs/ | Both | Vision outputs (Hiệp), Navigation outputs (Thông) |
| rviz/ | Thông | RViz configuration |
| scripts/ | Both | Calibration (Hiệp), Navigation scripts (Thông) |
| src/control/ | Thông | Control implementation |
| src/utils/ | Both | Utility implementation |
| src/vision/ | Hiệp | Vision implementation |
| tests/ | Both | Vision, Control and Integration tests |
| tools/ | Hiệp | Dataset/Image/PCD tools |
| worlds/ | Thông | Gazebo worlds |

---

# 👥 Folder Ownership

```text
==============================================================
                    PROJECT OWNERSHIP
==============================================================

                    🎥 Hiệp (Vision & Perception)

    assets/chessboard/

    datasets/
    data/calibration_result/

    include/vision/
    src/vision/

    outputs/depth/
    outputs/disparity/
    outputs/pointcloud/
    outputs/obstacle_map/
    outputs/free_space/

    scripts/calibration.py
    scripts/stereo_capture.py

    tests/vision/

    tools/

--------------------------------------------------------------

                  🎮 Thông (Control & Navigation)

    assets/meshes/
    assets/textures/

    data/logs/
    data/map/
    data/trajectory/

    include/control/
    src/control/

    launch/
    models/
    rviz/
    worlds/

    outputs/path/
    outputs/screenshots/
    outputs/videos/

    scripts/run_navigation.sh
    scripts/launch_all.sh

    tests/control/

--------------------------------------------------------------

                        🤝 Shared

    config/
    docs/
    images/

    include/interfaces/
    include/utils/

    src/utils/

    outputs/logs/

    tests/integration/

    scripts/clean_outputs.sh

    CMakeLists.txt
    package.xml
    requirements.txt

    LICENSE
    README.md

==============================================================
```

# 👨‍💻 Development Responsibility

| Member | Main Responsibility |
|---------|---------------------|
| Hiệp | Stereo Vision, Depth Estimation, Point Cloud, Obstacle Detection, Free Space Detection |
| Thông | Robot Localization, Navigation, Motion Planning, Walking Control, Gazebo Simulation |
| Shared | Interfaces, Documentation, Configuration, Testing |