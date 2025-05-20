![9d56ac49bb8959c66eca293fd99ca8f3](https://github.com/user-attachments/assets/cb5968e6-1f3a-4bd0-9485-0d39ec468b4c)# HW2
## homework2 of robot class
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
...
```

**实现效果：**
### 以速度1m/s运动
![56d5440221dd153d44d7b2d6bfa2acd2](https://github.com/user-attachments/assets/67eb4d0f-5dfa-4785-be71-0ee8cb31cc4c)
![54cfc5a6d39ded1a85033cece4fab955](https://github.com/user-attachments/assets/e740d73e-d72e-4a92-9e5f-21c93987916e)


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
...
```

**实现效果：**
### 实际位置：
![78f103e30e1e59b618afbd5545743dc1](https://github.com/user-attachments/assets/ef25b375-1ef2-4b06-83ea-9c98f7b84522)
### 
### 机器人视角：
![9d56ac49bb8959c66eca293fd99ca8f3](https://github.com/user-attachments/assets/7675aa89-6e9f-4930-a92c-aaf2f0bd04e0)
### 让橙色球运动后，机器人视角同时运动
![712a7556593b799d4db151157dd918ca](https://github.com/user-attachments/assets/97fb7687-e338-4451-ae87-57327486ee50)

### 实时跟踪橙色球的位置：
![9495d9afca4208ce92e346b500fbdd09](https://github.com/user-attachments/assets/e50098a4-7aac-4d6d-9d6e-6df2aa1b424f)

### 人脸检测跟踪：
![29c27188433a93e3c01a8f9f026885a5](https://github.com/user-attachments/assets/3a4d3831-2656-4622-92f0-3ca05e098166)

### 点云实现桌子上物体定位：
![497832d5bc3b27505b675a346b092934](https://github.com/user-attachments/assets/9b27123c-12e4-45c0-9e2b-202129a6180c)


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
...
```

**实现效果：**
### 机器人建图过程：
![d08c10dba42f716aa39f02cafa8c338d](https://github.com/user-attachments/assets/7e18ce74-db0a-44ff-b5ee-653226d58c44)
![acfb82d8fee3d69c5f35da71abd3d432](https://github.com/user-attachments/assets/65f6b3ef-3c17-47a3-8509-6fda8217ef44)


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
...
```

**实现效果：**
### 根据起点终点规划路径：
![522dc55aa0c98f6cc8a234122899ea19](https://github.com/user-attachments/assets/e9c7eabf-dd14-4ba1-9dae-fd0a5c310e7c)
### 开始根据规划的路径自动导航：
![0bb7379e9dc63cbfc2a72cff3dadfe7b](https://github.com/user-attachments/assets/3c7b7dfd-b0f3-4bf3-8447-9316309203fc)
### 设置多个点位：
![035f77a61c3da2a8758199e0707e9a45](https://github.com/user-attachments/assets/5b984cb8-3d84-4e25-b85e-26ecf6919d5a)
![90e33d8c5b808b71420bc7224310f468](https://github.com/user-attachments/assets/5cdab2ed-f544-43ab-937f-ef582260c7ac)

