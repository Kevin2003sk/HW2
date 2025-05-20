# HW2
homework2 of robot class


---

## 1. P1_robot_move —— 机器人基础运动控制

**主要内容：**
- 包含 `vel_pkg`（速度控制节点）和 `wpr_simulation2`（仿真环境）。
- 通过发布速度指令控制机器人运动。

**编译流程：**
```bash
cd P1_robot_move/ros2_ws
colcon build
source install/setup.bash
ros2 run vel_pkg vel_node
```

**实现效果：**
- 机器人可在仿真环境中根据速度指令前进、后退、转弯。
- 支持自定义速度参数，便于实验不同运动策略。

---

## 2. P2_opencv —— 基于OpenCV的图像处理

**主要内容：**
- `cv_pkg`：实现人脸检测、颜色识别、目标跟踪等功能（见 `src/` 下各 cpp 文件）。
- `pc_pkg`：点云数据处理与物体识别。
- 依赖 `wpr_simulation2` 提供仿真图像流。

**编译流程：**
```bash
cd P2_opencv
colcon build
source install/setup.bash
ros2 run cv_pkg cv_face_detect
# 或运行其他功能节点
```

**实现效果：**
- 实时检测摄像头画面中的人脸、颜色目标等。
- 可视化处理结果，支持仿真与真实数据。

---

## 3. P3_SLAM —— SLAM（同步定位与建图）

**主要内容：**
- `imu_pkg`、`lidar_pkg`：分别处理IMU和激光雷达数据。
- `slam_pkg`：集成SLAM算法，launch文件为 `slam.launch.py`。
- 依赖 `wpr_simulation2` 提供仿真传感器数据。

**编译流程：**
```bash
cd P3_SLAM/ros2_ws
colcon build
source install/setup.bash
ros2 launch slam_pkg slam.launch.py
```

**实现效果：**
- 机器人在仿真环境中自主运动并实时构建环境地图。
- 支持多传感器数据融合，提升定位与建图精度。

---

## 4. P4_NAV2 —— 基于Nav2的自主导航

**主要内容：**
- `wp_map_tools`：自定义导航点工具，含多种C++节点。
- `nav_pkg`：导航主包，含 `nav.launch.py`、`waypoint_nav.launch.py` 启动文件。
- 依赖 `wpr_simulation2`、`imu_pkg`、`lidar_pkg`、`slam_pkg` 等。

**编译流程：**
```bash
cd P4_NAV2/ros_ws
colcon build
source install/setup.bash
ros2 launch nav_pkg nav.launch.py
# 或
ros2 launch nav_pkg waypoint_nav.launch.py
```

**实现效果：**
- 机器人可在仿真地图中自主规划路径、避障并到达目标点。
- 支持多点导航、路径可视化、导航点编辑等高级功能。
