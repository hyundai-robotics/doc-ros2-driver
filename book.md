
[__SOURCE](README.md)
# Hi6 & Hi7 控制器功能手册 - ROS2 驱动

目前，ROS2 兼容的控制器是 Hi6、Hi7 系列，支持控制器软件版本 **v70.00-00** 或更高版本。

- [源代码] [hdr_ros2_driver] [GitHub 仓库 ↗](https://github.com/hyundai-robotics/hdr_ros2_driver)
- [源代码] [hdr_description] [GitHub 仓库 ↗](https://github.com/hyundai-robotics/hdr_description)
- [源代码] [hdr_client_driver] [GitHub 仓库 ↗](https://github.com/hyundai-robotics/hdr_client_driver)
- [源代码] [hdr_simulation_gz] [GitHub 仓库 ↗](https://github.com/hyundai-robotics/hdr_simulation_gz)

</br>
[__SOURCE](0-about-this-manual/README.md)
# 关于手册
[__SOURCE](0-about-this-manual/precautions.md)
# 注意事项

{% include file="zh/precautions.md" %}
[__SOURCE](0-about-this-manual/safety-notice.md)
# 安全注意事项

{% include file="zh/safety-notice.md" %}
[__SOURCE](1-intro/README.md)
# 1. 概述

本手册提供了HD现代机器人(HDR) ROS2驱动程序的描述。

HDR ROS2驱动程序将HD现代机器人工业机器人控制器(Hi6、Hi7系列)与ROS2系统集成，以支持仿真环境和真实机器人控制功能。

![](../_assets/0_hdr_main.png)


### 前提条件
在使用HDR ROS2驱动程序之前，请确保检查以下项目：
- [支持的控制器](1-controller-models/README.md) - 兼容的Hi6、Hi7系列控制器软件版本
- [支持的机器人模型](2-robot-models/README.md) - 兼容的HD现代机器人模型
- [系统要求](3-requirements/README.md) - 硬件和软件要求
- [ROS2版本](4-ros2-version/README.md) - 支持的ROS2版本
- [机器人关节和链接名称](5-hdr-robot/README.md) - ROS2中的机器人关节和链接命名约定

### 安装和初始设置
在验证上述所有项目后，请按照以下步骤进行ROS2驱动程序的安装和初始设置：
- [库概述](../2-start/1-repo-overview/README.md) - HDR ROS2驱动程序库结构和架构概述
- [包安装](../2-start/2-installation/README.md) - HDR ROS2驱动程序的构建和安装方法
- [控制器和PC设置](../2-start/3-initial-setup/README.md) - 使用HDR ROS2驱动程序的初始设置方法
- [安装验证](../2-start/4-verifying/README.md) - 验证安装和设置是否正确完成

### 快速启动ROS2驱动程序
在完成上述所有安装和初始设置流程后，您可以启动HDR ROS2驱动程序并通过以下步骤开始机器人控制：

- [运行ROS2驱动程序](../10-running/README.md) - ROS2驱动程序的执行和机器人控制方法

⚠️ **请确保检查前提条件并完成所有安装和初始设置后再继续。**

⚠️ **目前，HD现代机器人ROS2驱动程序支持控制器软件版本*v70.00-00*或更高版本。**
[__SOURCE](1-intro/1-controller-models/README.md)
# 1.1 支持的控制器型号
HD Hyundai Robotics Hi6, Hi7 控制器型号正式支持 ROS 2 功能。

**控制器要求**：
- 软件版本：**70.00-00** 或更高
- 操作模式：**REMOTE mode**

> ⚠️ **注意：** HD Hyundai Robotics ROS2 驱动程序 **不支持** **Hi5, Hi5a** 控制器系列。

### 下一步

在确认控制器兼容性后，请检查 [支持的机器人型号](../2-robot-models/README.md) 以验证您的机器人是否受支持。
[__SOURCE](1-intro/2-robot-models/README.md)
# 1.2 支持的机器人型号

目前HD现代机器人驱动程序官方支持的机器人型号如下：

- ha006b
- hdf7_9
- hdf8_8
- hdr10l_19
- hdr20_17
- hdr50_22
- hdr220_26
- hh020
- hdr35_20

### 型号名称更改

{% hint style="warning" %}
机器人型号 `hdf7_9`、`hdf8_8`、`hdr20_17`、`hdr50_22`、`hdr220_26`、`hdr35_20` 是型号 `HH7`、`HH8`、`UH020`、`HH050`、`HS220`、`UH035` 的更名版本。
{% endhint %}

### 每个型号包含的内容

每个支持的机器人型号包括以下内容：

- **URDF**：带有碰撞网格的机器人URDF
- **Mesh**：用于可视化的3D模型
- **MoveIt2 配置**：带有型号特定软限制的运动规划设置
- **Gazebo 支持**：仿真集成支持

### 下一步

确认机器人型号后，请继续查看[系统要求](../3-requirements/README.md)以验证您的系统是否正确配置。
[__SOURCE](1-intro/3-requirements/README.md)
# 1.3 系统要求

此页面描述了运行 HD Hyundai Robotics ROS2 驱动程序所需的硬件和软件要求。

### 硬件要求

#### 机器人控制器
- **兼容控制器**: Hi6, Hi7 控制器系列
- **控制器软件版本**: **70.00-00** 或更高
- **操作模式**: 机器人必须设置为 **REMOTE** 模式
- **网络接口**: 以太网连接 (LAN1, LAN2 或 LAN3)

#### 开发 PC
- **操作系统**: Ubuntu 22.04 LTS 或 Ubuntu 24.04 LTS
- **内存**: 最少 8GB RAM（推荐 16GB 用于仿真）
- **网络**: 用于机器人通信的以太网接口
- **CPU**: 多核处理器（推荐 4 核或更多）


### 下一步

一旦您的系统满足所有要求，请检查 [支持的 ROS2 版本](../4-ros2-version/README.md)。
[__SOURCE](1-intro/4-ros2-version/README.md)
# 1.4 支持的 ROS2 版本

HD Hyundai Robotics ROS2 驱动程序支持在机器人控制器和仿真环境中经过测试和验证的特定 ROS2 发行版。

### 支持的 ROS2 发行版

- **ROS2 Humble Hawksbill** (Ubuntu 22.04 LTS)
- **ROS2 Jazzy Jalisco** (Ubuntu 24.04 LTS)

### 版本验证

安装后，验证您的 ROS2 设置：

```bash
# 来源 ROS2 环境
source /opt/ros/$ROS_DISTRO/setup.bash

# 检查 ROS2 版本
ros2 doctor
```

### 后续步骤

确认 ROS2 兼容性后，请继续阅读 [Getting Started](../../2-start/README.md) 进行安装。
[__SOURCE](1-intro/5-hdr-robot/README.md)
# 1.5 机器人关节和连杆名称

HD Hyundai Robotics 机器人遵循如下所示的 URDF 中的关节和连杆命名约定。


### 关节名称

|joint no|joint name </br>(URDF)|joint name </br>(TP)|
|:------:|:---:|:---:|
|1|j1|S|
|2|j2|H|
|3|j3|V|
|4|j4|R2|
|5|j5|B|
|6|j6|R1|


### 连杆名称

|link No|link Name|
|:------:|:---:|
|0|base_link|
|1|lower_frame_link|
|2|upper_frame_link|
|3|arm_link|
|4|wrist_body_link|
|5|wrist_holder_link|
|6|flange_link|


### 连杆关系

|link No|link Name|joint|parent link|joint type|note|
|:------:|:---:|:---:|:------:|:---:|:---:|
||world||||||
|0|base_link|world_joint|world|fixed|||
|1|lower_frame_link|j1|base_link|revolute||
|2|upper_frame_link|j2|lower_frame_link|revolute||
|3|arm_link|j3|upper_frame_link|revolute||
|4|wrist_body_link|j4|arm_link|revolute||
|5|wrist_holder_link|j5|wrist_body_link|revolute||
|6|flange_link|j6|wrist_holder_link|revolute||
||flange|flange_link-flange|flange_link|fixed|ROS-Industrial 标准坐标系|
||tool0|flange-tool0|flange|fixed|ROS-Industrial 标准坐标系|
[__SOURCE](2-start/README.md)
# 2. 入门

本节提供了 HD Hyundai Robotics ROS2 驱动程序的安装、配置和执行的逐步说明。请遵循本指南设置开发环境并与机器人建立通信。

### 安装和设置过程

1. [代码库概述](1-repo-overview/README.md) - 理解包结构和关系
2. [安装](2-installation/README.md) - 代码库克隆和构建
3. [初始设置](3-initial-setup/README.md) - 网络配置设置
4. [安装验证](4-verifying/README.md) - 安装测试
[__SOURCE](2-start/1-repo-overview/README.md)
# 2.1 仓库概述

HD Hyundai Robotics ROS2 驱动程序由多个相互连接的包组成，这些包共同提供机器人控制、仿真和运动规划功能。

### 仓库架构

```
HD Hyundai Robotics ROS2 Driver

hdr_ros2_driver            # 主仓库
   hdr_bringup             # 机器人集成和控制启动文件
   hdr_ros2_driver         # 核心通信驱动
   hdr_hardware_interface  # ros2_control 集成
   hdr_moveit_config       # MoveIt 配置
   hdr_msgs                # HD Robotics 自定义消息定义

hdr_client_driver          # C++ 客户端库

hdr_description            # 机器人 URDF 模型和网格

hdr_simulation_gz          # Gazebo 仿真集成
```

### 仓库内的包详情

- **[ROS2 驱动程序 (`hdr_ros2_driver`)](../../3-hdr_ros2_driver/README.md)** </br>
提供机器人控制、文件管理、I/O 操作和系统监控服务的主要 ROS2 节点

- **[HDR 客户端驱动程序 (`hdr_client_driver`)](../../7-hdr_client_driver/README.md)** </br>
实现与 HD Hyundai Robotics 控制器的 TCP/UDP 通信协议的 C++ 库

- **[ROS2 控制集成 (`hdr_hardware_interface`)](../../4-hdr_hardware_interface/README.md)** </br>
与标准 ROS2 控制框架集成的 ros2_control SystemInterface

- **[机器人描述 (`hdr_description`)](../../5-hdr_description/README.md)** </br>
支持的机器人模型的 URDF/XACRO、碰撞/视觉网格和 RViz 配置

- **[MoveIt2 配置 (`hdr_moveit_config`)](../../6-hdr_moveit_config/README.md)** </br>
特定于机器人模型的 MoveIt2 配置，包括 SRDF、软限制、运动学和运动规划设置

- **[Gazebo 仿真 (`hdr_simulation_gz`)](../../8-hdr_simulation_gz/README.md)** </br>
Gazebo Ignition 仿真集成

- **[自定义消息 (`hdr_msgs`)](../../9-hdr_msgs/README.md)** </br>
与 HD Hyundai Robotics 控制器通信的自定义 ROS2 服务和消息定义


### 下一步

1. 查看上述链接的各个包文档。
2. 前往 [安装](../2-installation/README.md) 来构建包。
3. 在 [初始设置](../3-initial-setup/README.md) 中配置机器人连接。
[__SOURCE](2-start/2-installation/README.md)
# 2.2 包构建和安装
本节涵盖 HD Hyundai Robotics ROS2 驱动程序的安装过程，包括仓库克隆、依赖项安装和包构建。

### 工作区设置

#### 创建 ROS2 工作区

```bash
# 创建工作区目录
mkdir -p ~/hdr_ws/src
cd ~/hdr_ws
```

#### 克隆源代码库

```bash
cd ~/hdr_ws/src

# HDR 核心驱动程序和客户端库
git clone https://github.com/hyundai-robotics/hdr_ros2_driver.git
git clone https://github.com/hyundai-robotics/hdr_client_driver.git

# HDR 描述包
git clone https://github.com/hyundai-robotics/hdr_description.git

# Gazebo 仿真
git clone https://github.com/hyundai-robotics/hdr_simulation_gz.git
```

### 依赖项安装

#### 安装 ROS2 依赖项

```bash
cd ~/hdr_ws

# 更新包数据库
rosdep update

# 安装 HDR 包的所有依赖项
rosdep install --from-paths src --ignore-src --rosdistro $ROS_DISTRO -y
```

### 构建过程

#### 标准构建

```bash
cd ~/hdr_ws

# 用优化构建所有包
colcon build --symlink-install --cmake-args=-DCMAKE_BUILD_TYPE=Release
```

#### 构建配置选项
```bash
# 带调试符号构建
colcon build --symlink-install --cmake-args=-DCMAKE_BUILD_TYPE=Debug
```

#### 环境设置

```bash
cd ~/hdr_ws
source install/setup.bash

echo "source ~/hdr_ws/install/setup.bash" >> ~/.bashrc
```

### 下一步

成功安装和构建包后：
1. 继续进行 [初始设置](../3-initial-setup/README.md) 以进行控制器和 PC 配置
2. 运行 [安装验证](../4-verifying/README.md) 测试
[__SOURCE](2-start/3-initial-setup/README.md)
# 2.3 控制器与PC通信设置

本指南涵盖了在开发PC上配置网络接口以与HD Hyundai Robotics机器人控制器进行通信。

### 前提条件
⚠️ 请在开始设置之前确认以下事项：
- **机器人控制器软件版本**：Hi6、Hi7系列控制器，软件版本 **70.00-00** 或更高

### 网络配置概述

PC必须配置为通过以太网与机器人控制器进行通信。默认配置使用192.168.1.x子网，控制器地址为192.168.1.150。

### 默认网络配置（使用LAN1）

| 组件 | 参数 | 默认值 |
|-----------|-----------|---------------|
| **PC IP地址** | 静态IP | 192.168.1.x（用户配置）|
| **机器人控制器IP** | 静态IP | 192.168.1.150 |
| **子网掩码** | 网络掩码 | 255.255.255.0 |
| **网关** | 默认网关 | 192.168.1.1  |

### 电缆连接

![](../../_assets/controller.png)

1. **找到机器人控制器以太网端口**
   - **Hi6-N 控制器**：主模块顶部的以太网端口
   - **Hi6-T 控制器**：控制器前面板上的以太网端口

2. **连接以太网电缆**
   - 使用Cat5e或Cat6以太网电缆
   - **建议**：使用LAN1（通常预配置为192.168.1.x）
   - LAN2、LAN3端口也可用，默认控制器IP不同：</br>
      LAN2: 192.168.4.150 → PC需配置为192.168.4.x范围 </br>
      LAN3: 192.168.3.150 → PC需配置为192.168.3.x范围

3. **验证物理连接**
   - 确保电缆连接牢固
   - 检查网络端口LED指示灯（如果可用）


### PC网络接口配置

![](../../_assets/LAN_com.png)

#### 使用网络管理器GUI

##### Ubuntu桌面 (GNOME)

1. **打开网络设置**
   - 点击右上角的网络图标
   - 选择“有线设置”或转到设置 → 网络

2. **配置有线连接**
   - 点击有线连接旁边的齿轮图标
   - 转到“IPv4”选项卡

3. **设置静态IP配置（使用LAN1）**
   - **方法**：手动
   - **地址**：192.168.1.100
   - **子网掩码**：255.255.255.0
   - **网关**：192.168.1.1

4. **应用设置**
   - 点击“应用”，然后断开再重新连接网络接口

![](../../_assets/ip_setup.png)

### 验证

#### 验证网络配置

```bash
# 测试网络连接
ping -c 4 192.168.1.150
```

![](../../_assets/ping_test.png)
[__SOURCE](2-start/4-verifying/README.md)
# 2.4 安装验证

本指南提供验证程序，以确认 HD Hyundai Robotics ROS2 驱动程序已正确安装、配置并准备好操作。

#### 机器人模式配置

HDR ROS2 驱动程序仅在机器人处于 **REMOTE** 模式时才能工作。

请在运行 ROS2 驱动程序之前，通过将教学挂件 (TP) 上的模式开关切换到 REMOTE 位置来将控制器设置为遥控模式。

![](../../_assets/tp_operate.png)


#### HDR ROS2 驱动程序执行测试

```bash
# 运行 HDR ROS2 驱动程序（确保机器人处于 REMOTE 模式）
ros2 launch hdr_bringup hdr_control.py \
  robot_model:=hdf7_7      # 输入机器人模型（默认：ha006b）


# 在另一个终端验证控制器管理器
ros2 control list_controllers

# 预期输出：
# joint_state_broadcaster[joint_state_broadcaster/JointStateBroadcaster] active
# joint_trajectory_controller[joint_trajectory_controller/JointTrajectoryController] active
```

#### 关节状态发布测试

```bash
# 验证关节状态是否正在发布
ros2 topic list | grep joint_states

# 监控关节状态
ros2 topic echo /joint_states --once

# 检查发布频率
ros2 topic hz /joint_states
```
[__SOURCE](3-hdr_ros2_driver/README.md)
# 3. ROS2 Driver (`hdr_ros2_driver`)

`hdr_ros2_driver` 包提供了与 HD Hyundai Robotics 的开放 API 接口的核心 ROS2 驱动程序。此驱动程序通过 REST API 使与机器人控制器的全面通信成为可能，支持机器人控制、监控、文件操作和系统管理的服务。

- [源代码] [hdr_ros2_driver] [GitHub 仓库 ↗](https://github.com/hyundai-robotics/hdr_ros2_driver)

### 主要特性

- **机器人状态发布**：通过 `/joint_states` 主题实时关节状态信息
- **运动控制**：通过 ROS2 动作进行关节轨迹控制
- **全面服务**：按功能组织的 30 多个服务端点

### 详细文档

- [启动](1-launch/README.md) - 驱动程序执行的启动文件
- [主题](2-topics/README.md) - 发布的机器人状态信息
- [动作](3-actions/README.md) - 关节轨迹执行和运动控制
- [服务](4-services/README.md) - API 服务参考
[__SOURCE](3-hdr_ros2_driver/1-launch/README.md)
# 3.1 HDR ROS2 Driver 启动

本节介绍如何启动 HDR ROS2 驱动程序。

### 基本启动

#### HDR ROS2 驱动程序启动
```bash
# 使用默认参数启动
ros2 launch hdr_ros2_driver hdr_ros2_driver_launch.py
```

这将使用以下配置启动驱动程序：
- 默认 IP：192.168.1.150
- 默认端口：8888

### 验证

启动后，验证驱动程序是否正在运行：

```bash
# 检查驱动节点是否处于活动状态
ros2 node list | grep hdr_ros2_driver

# 列出可用服务
ros2 service list | grep hdr_ros2_driver

# 测试基本连接
ros2 service call /hdr_ros2_driver/get/api_ver std_srvs/srv/Trigger
```

### 网络设置前提条件

在启动之前，请确保正确的网络配置：

1. **以太网连接**：通过 LAN1、LAN2 或 LAN3 将 PC 连接到机器人控制器
2. **控制器 IP**：默认 192.168.1.150（通过教学挂件可配置）
3. **PC IP**：设置为 192.168.1.x 范围（x ≠ 150）
4. **REMOTE 模式**：确保机器人控制器处于 REMOTE 模式

### 故障排除

#### 常见问题

1. **连接超时**
   - 验证机器人 IP 和端口：`ping 192.168.1.150`
   - 检查以太网电缆连接

2. **服务不可用**
   - 验证驱动程序成功启动
   - 检查 ROS2 环境是否已导入
   - 检查启动输出是否有错误信息
   - 确保机器人处于 REMOTE 模式
   - 验证控制器软件版本为 **70.00-00** 或更高
[__SOURCE](3-hdr_ros2_driver/2-topics/README.md)
# 3.2 提供的主题

### 概述

ROS2 驱动程序通过标准化的 ROS2 主题发布实时机器人数据。这些主题提供关节状态、机器人状态信息和用于监控和控制应用的诊断数据。

### 发布的主题

#### 关节状态信息

##### `/joint_states` (sensor_msgs/msg/JointState)
**描述**：实时关节位置数据

**消息字段**：
```yaml
std_msgs/Header header
  uint32 seq
  time stamp
  string frame_id
string[] name          # 与 URDF 匹配的关节名称
float64[] position     # 以弧度表示的关节位置
float64[] velocity     # 以弧度/秒表示的关节速度
float64[] effort       # 以扭矩表示的关节努力
```

**发布频率**：50 Hz（可通过 `publish_rate` 参数配置）
[__SOURCE](3-hdr_ros2_driver/3-actions/README.md)
# 3.3 可用操作

### 概述

ROS2驱动程序提供机器人关节轨迹控制的操作接口。操作使异步操作成为可能，并提供进度反馈和取消功能。

### 关节轨迹控制操作

#### `/joint_trajectory_controller/follow_joint_trajectory` (control_msgs/action/FollowJointTrajectory)

**描述**: 执行关节轨迹控制。

**action_goal**:
```yaml
trajectory_msgs/JointTrajectory trajectory
  std_msgs/Header header
  actionlib_msgs/GoalID goal_id
    time stamp
    string id
  control_msgs/FollowJointTrajectoryGoal goal
    trajectory_msgs/JointTrajectory trajectory
      std_msgs/Header header
      string[] joint_names
      trajectory_msgs/JointTrajectoryPoint[] points
    control_msgs/JointTolerance[] path_tolerance
      string name
      float64 position
      float64 velocity
      float64 acceleration
    control_msgs/JointTolerance[] goal_tolerance
      string name
      float64 position
      float64 velocity
      float64 acceleration
    duration goal_time_tolerance
```

**action_feedback**:
```yaml
std_msgs/Header header
string[] joint_names
trajectory_msgs/JointTrajectoryPoint desired
trajectory_msgs/JointTrajectoryPoint actual
trajectory_msgs/JointTrajectoryPoint error
```

**action_result**:
```yaml
std_msgs/Header header
actionlib_msgs/GoalStatus status
control_msgs/FollowJointTrajectoryResult result
```
[__SOURCE](3-hdr_ros2_driver/4-services/README.md)
# 3.4 ROS2 Driver Services

### 概述

The `hdr_ros2_driver` 提供与 HD Hyundai Robotics Hi6 控制器通信的各种 ROS2 服务。

### 服务类别

| 类别 | 描述 |
|----------|-------------|
| **[控制服务](1-control/README.md)** | 机器人控制、马达电源、紧急停止、坐标系统、I/O 管理 |
| **[任务管理](2-task/README.md)** | 变量分配、运动执行、程序控制 |
| **[文件管理](3-file/README.md)** | 文件上传/下载、目录操作 |
| **[PLC 通信](4-plc/README.md)** | PLC 继电器值控制 |
| **[控制台命令](5-console/README.md)** | 控制台命令执行、系统时间、日志管理 |
| **[项目管理](6-project/README.md)** | 作业信息、作业删除/重新加载 |
| **[版本信息](7-version/README.md)** | API 版本、系统版本查询 |

### 基本用法

#### 检查服务列表
```bash
# 列出所有 HDR 驱动服务
ros2 service list | grep hdr_ros2_driver
```

#### 常见服务调用
```bash
# 检查 API 版本
ros2 service call /hdr_ros2_driver/get/api_ver std_srvs/srv/Trigger

# 检查马达状态
ros2 service call /hdr_ros2_driver/robot/get/motor_state std_srvs/srv/Trigger

# 打开马达电源
ros2 service call /hdr_ros2_driver/robot/post/motor_power std_srvs/srv/Trigger
```
[__SOURCE](4-hdr_hardware_interface/README.md)
# 4. ROS2 Control Integration (`hdr_hardware_interface`)

### Overview

The `hdr_hardware_interface` package provides a `ros2_control` SystemInterface to connect HD Hyundai Robotics' Open API-based controllers with the ROS2 control framework. It maps joint position state and command interfaces to HTTP-based robot services, handling controller lifecycle and real-time pose tracking.

### Package Structure

| Directory                           | Description                                                                 |
| ----------------------------------- | ----------------------------------------------------------------------------|
| `include/`                          | C++ 头文件，包括 `HDRRobotHardware` 和工具助手               |
| `src/`                              | SystemInterface 逻辑实现                                     |
| `launch/`                           | 执行 `ros2_control` 接口的启动文件             |
| `config/`                           | 控制器和运动学设置的 YAML 配置文件   |
| `hdr_hardware_interface_plugin.xml` | 插件的元数据                                               |

---

### Usage

###### Launch HDR hardware interface with ros2_control

```bash
ros2 launch hdr_hardware_interface ros2_control.launch.py \
  robot_model:=hdf7_9 \
  openapi_ip:=192.168.1.150 \
  openapi_port:=8888
```

###### Plugin Configuration
要启用硬件接口，请将其包含在 URDF 或 xacro 的 `<ros2_control>` 中

```xml
<ros2_control name="HDRRobotHardware" type="system">
  <hardware>
    <plugin>hdr_hardware_interface/HDRRobotHardware</plugin>
    <param name="robot_model">ha006b</param>
    <param name="openapi_ip">192.168.1.150</param>
    <param name="openapi_port">8888</param>
  </hardware>
</ros2_control>
```

##### Configuration Options

| Parameter                      | Type   | Default                         | Description                                                                 |
|---------------------------|--------|----------------------------------|-----------------------------------------------------------------------------|
| `robot_model`             | string | `"ha006b"`                      | 机器人模型名称                               |
| `openapi_ip`              | string | `"192.168.1.150"`               | 机器人控制器的 HTTP API IP 地址                                  |
| `command_start_time`   | float  | `-1.0`                          | 命令执行时间 (-1.0 表示立即执行)             |
| `command_buffer_size`  | int    | `5`                             | 命令数据缓冲区大小                                 |
| `use_sim`                 | bool   | `false`                         | 启用使用 `gz_ros2_control/GazeboSimSystem` 插件的仿真模式，通常用于与 Ignition Gazebo 的集成<br>`use_sim_time` 参数也设置为 true，以便与仿真时间同步     |
| `use_mock_hardware`       | bool   | `false`                         | 启用使用 `mock_components/GenericSystem` 的模拟硬件接口，以便在没有机器人时进行测试   |
| `initial_positions_file`  | string | `""`                            | 可选的 YAML 文件，用于指定初始关节位置                       |
| `controllers_config_package` | string | `"hdr_hardware_interface"`     | 包含配置 YAML 的包名称                                       |
| `controllers_file`        | string | `"default_controllers.yaml"`   | 控制器配置 YAML 文件名                                     |
| `kinematics_file`         | string | `"default_kinematics.yaml"`    | 运动学插件配置 YAML 文件名                              |


##### Topics

| Topic Name                   | Message Type                   | Description                               |
| ---------------------------- | ------------------------------ | ----------------------------------------- |
| `/joint_states`              | sensor_msgs::msg::JointState | 发布当前关节状态，包括位置信息 |
| `/controller_manager/status` | lifecycle_msgs::msg::State   | ros2_control 管理器的生命周期状态 |

##### Actions

| Action Name                                            | Action Type                                   | Description                                |
| ------------------------------------------------------ | --------------------------------------------- | ------------------------------------------ |
| `/joint_trajectory_controller/follow_joint_trajectory` | control_msgs::action::FollowJointTrajectory | 通过 ROS2 动作执行关节轨迹命令 |

##### Services

| Service Name                                   | Service Type                                         | Description                         |
| ---------------------------------------------- | ---------------------------------------------------- | ----------------------------------- |
| `/controller_manager/list_controllers`         | controller_manager_msgs/srv/ListControllers        | 返回活动控制器的列表     |
| `/controller_manager/list_hardware_interfaces` | controller_manager_msgs/srv/ListHardwareInterfaces | 返回可用的关节命令和状态接口 |
| `/controller_manager/switch_controller`        | controller_manager_msgs/srv/SwitchController       | 激活或停用控制器  |
| `/controller_manager/load_controller`          | controller_manager_msgs/srv/LoadController         | 加载控制器             |
| `/controller_manager/unload_controller`        | controller_manager_msgs/srv/UnloadController       | 卸载指定的控制器。    |

---
[__SOURCE](5-hdr_description/README.md)
# 5. Robot URDF (`hdr_description`)

`hdr_description`  包含 HD 现代机器人在 ROS2 中的机器人 URDF、网格和可视化配置。该包提供了模拟、可视化和运动规划所需的基本 URDF/XACRO 定义。

[Source Code] [GitHub Repository ↗](https://github.com/hyundai-robotics/hdr_description)

### Key Features

- **机器人模型特定 URDF**：所有支持的机器人模型的 URDF/XACRO 文件
- **3D 网格**：用于准确模拟的碰撞和视觉网格
- **RViz 集成**：预配置的可视化设置
- **ros2_control 集成**：关节接口定义

### Package Structure

| Directory | Contents | Purpose |
|-----------|----------|----------|
| `urdf/` | 机器人 URDF 文件 | URDF/XACRO 定义 |
| `meshes/` | 3D 模型网格文件 | 碰撞和视觉表示 |
| `launch/` | 可视化启动文件 | RViz 显示配置 |
| `rviz/` | RViz 配置文件 | 显示设置和插件 |

### URDF Configuration

#### Main Files
- **`hdr.urdf.xacro`**：包含所有组件的顶层宏
- **`hdr.ros2_control.xacro`**：ros2_control 硬件接口宏

#### Robot-Specific Files
每个机器人模型在 `urdf/robots/` 下都有自己的目录：
- `ha006b.urdf.xacro`
- `hdf7_9.urdf.xacro`
- `hdf8_8.urdf.xacro`
- `hdr10l_19.urdf.xacro`
- `hdr20_17.urdf.xacro`
- `hdr50_22.urdf.xacro`
- `hdr220_26.urdf.xacro`
- `hh020.urdf.xacro`
- `hdr35_20.urdf.xacro`

### Usage Examples

#### Visualization in RViz
```bash
ros2 launch hdr_description display_robot.launch.py robot_model:=ha006b
```

#### Launch Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `robot_model` | string | `ha006b` | 要显示的机器人模型 |
| `description_package` | string | `hdr_description` | 包含 URDF 文件的包 |
| `description_file` | string | `hdr.urdf.xacro` | 主 URDF/XACRO 文件 |

### Mesh Quality

该包为每个机器人提供两种类型的网格：

#### Visual Meshes
- 高分辨率网格以实现真实的可视化
- 详细的表面纹理和材料
- 用于 RViz 和 Gazebo 中的视觉表示

#### Collision Meshes
- 简化的网格用于碰撞检测
- 针对计算效率进行了优化
- 由物理引擎和运动规划器使用

有关模型特定的详细信息，请参见 [Supported Robot Models](../1-intro/2-robot-models/README.md).
[__SOURCE](6-hdr_moveit_config/README.md)
# 6. MoveIt2 配置 (`hdr_moveit_config`)

`hdr_moveit_config` 包提供用于控制 HD Hyundai Robotics 机器人在实际和仿真环境中的 MoveIt2 配置包。该包包含特定于机器人的运动规划配置，具有 SRDF 定义、关节限制和控制器设置。

### 主要特性

- **特定于机器人的配置**：每个支持的机器人模型的单独 MoveIt2 设置
- **SRDF 定义**：带有规划组和姿态的语义机器人描述
- **关节限制管理**：安全操作的速度和加速度缩放
- **运动学集成**：正/反运动学求解器配置
- **控制器集成**：ros2_control 和轨迹执行设置

### 包组织

每个机器人模型都有自己独立的 MoveIt2 配置包：

- `ha006b_moveit_config/`
- `hdf7_9_moveit_config/`
- `hdf8_8_moveit_config/`
- `hdr10l_19_moveit_config/`
- `hdr20_17_moveit_config/`
- `hdr50_22_moveit_config/`
- `hdr220_26_moveit_config/`
- `hh020_moveit_config/`
- `hdr35_20_moveit_config/`

### 配置文件

每个机器人配置包括：

#### 核心配置
- **SRDF 文件**：带有规划组的语义机器人描述
- **joint_limits.yaml**：带有缩放因子的速度和加速度限制
- **kinematics.yaml**：运动学求解器插件配置
- **controllers.yaml**：ros2_control 轨迹控制器设置

#### 高级设置
- **ompl_planning.yaml**：OMPL 运动规划器配置
- **pilz_cartesian_limits.yaml**：Pilz 规划器的笛卡尔运动限制
- **sensors_3d.yaml**：3D 传感器集成（如适用）
- **initial_positions.yaml**：默认起始姿态

### 安全注意事项

#### 速度缩放
**≤ 0.5** 的缩放因子推荐用于稳定操作：

```yaml
default_velocity_scaling_factor: 0.5
default_acceleration_scaling_factor: 0.5
```

#### 关节限制
`joint_limits.yaml` 文件定义：
- 最大关节速度
- 最大关节加速度
- 软件位置限制
- 运动规划的缩放因子

### 启动

```bash
ros2 launch hdr_bringup hdr_moveit.launch.py robot_model:=ha006b
```

![](../_assets/hdr_moveit.png)

### 规划组

典型的 SRDF 规划组配置：

```xml
<group name="manipulator">
    <chain base_link="base_link" tip_link="link6"/>
</group>

<group_state name="home" group="manipulator">
    <joint name="j1" value="0"/>
    <joint name="j2" value="0"/>
    <joint name="j3" value="0"/>
    <joint name="j4" value="0"/>
    <joint name="j5" value="0"/>
    <joint name="j6" value="0"/>
</group_state>
```


### 定制

要修改运动规划行为：
1. 编辑 `joint_limits.yaml` 以设置速度/加速度限制（不能超过 URDF 中每个关节定义的最大速度）
2. 修改 `ompl_planning.yaml` 以设置特定于规划器的参数
3. 更新 SRDF 以添加新的规划组或姿态
4. 在 `controllers.yaml` 中调整控制器参数
[__SOURCE](7-hdr_client_driver/README.md)
# 7. HD Hyundai Robotics Client Driver

HDR 客户端驱动程序提供了一个全面的 C++ 库，用于通过 HTTP (Open API) 和 socket (TCP/UDP) 接口与 HD Hyundai Robotics 机器人控制器进行通信。该库抽象了这两种通信层，并提供了面向对象的接口用于机器人控制和监控、文件管理、实时命令执行以及与 ROS2 的集成。

[Source Code] [GitHub Repository ↗](https://github.com/hyundai-robotics/hdr_client_driver)

{% hint style="warning" %}
所有基于 REST API 的通信要求机器人处于 REMOTE 模式。
{% endhint %}

### Package Structure

| Directory | Description |
|-----------|-------------|
| `include/` | HDR 客户端驱动库的头文件 |
| `src/` | 客户端驱动函数的源实现 |
| `src/functions/` | 各种机器人控制器功能的 API 类别实现 |
| `examples/` | 演示如何使用驱动 API 的示例程序 |
[__SOURCE](7-hdr_client_driver/1-api-categories/README.md)
# 7.1 API 类别

HDR 客户端驱动程序支持以下 API 类别：

### 支持的 API 类别

HDR 客户端驱动程序提供以下 API 类别，对应于机器人控制器的各种功能：

- **[控制](1-control/README.md)** - 基本机器人控制操作
- **[机器人](2-robot/README.md)** - 机器人运动和状态管理
- **[项目](3-project/README.md)** - 项目和作业管理
- **[文件](4-file/README.md)** - 文件系统操作
- **[输入/输出](5-io/README.md)** - 输入/输出控制
- **[任务](6-task/README.md)** - 任务执行和变量管理
- **[其他](7-etc/README.md)** - 系统实用程序
[__SOURCE](7-hdr_client_driver/1-api-categories/1-control/README.md)
# 7.1.1 控制 API

### 概述

控制 API 类别提供基本的机器人控制操作，包括电机管理、坐标系处理和运动模式控制。这些 API 形成了所有机器人操作的基础。

### 可用的控制 API

| 功能 | 描述 |
|----------|-------------|
| `GetControlOpCnd` | 读取机器人控制器的执行条件配置（回放模式、最大倒退速度、用户坐标号） |
| `GetControlIosDio` | 读取特定数字 I/O 信号值（支持类型："di"、"dib"、"diw"、"dil"、"dif"、"do"、"dob"、"dow"、"dol"、"dof"） |
| `GetControlIosSio` | 查询特殊 I/O (SIO) 信号值（输入类型："si"、"sib" 等，输出类型："so"、"sob" 等） |
| `GetControlUcsNos` | 读取可用于运动编程的用户坐标系 (UCS) 数字列表 |
| `PostControlIosDio` | 设置数字输出 (DO) 信号值（类型、块编号、信号编号、值） |
| `PutControlOpCnd` | 更新操作条件参数（回放模式、反向运动最大速度、用户坐标系） |
[__SOURCE](7-hdr_client_driver/1-api-categories/2-robot/README.md)
# 7.1.2 机器人 API

### 概述

机器人 API 类别处理核心机器人操作，包括运动控制、位置管理、工具配置和安全系统。这些 API 提供了对机器人运动和状态监控的直接控制。

### 可用的机器人 APIs

| 功能 | 描述 |
|----------|-------------|
| `GetRobotMotorState` | 检查机器人伺服电机电源状态 (ON/OFF)，用于检查运动命令的准备情况 |
| `GetRobotPoCur` | 当前机器人姿态 (位置和方向)，具有多种选项 (作业索引、坐标系统等) |
| `GetRobotCurTool` | 检索当前选择工具的信息 (TCP 配置、重量等) |
| `GetRobotTools` | 检索系统中注册的所有工具列表 (TCP 偏移、重量等) |
| `GetRobotToolsT` | 通过工具编号查询特定工具的详细信息 (0-31) |
| `GetJointTrajBuffAvail` | 获取轨迹缓冲区的可用大小 |
| `PostRobotMotorPower` | 打开或关闭机器人电机电源 |
| `PostRobotOperation` | 开始或停止机器人程序执行 |
| `PostRobotToolNo` | 设置要使用的活动工具编号 (0-31) |
| `PostRobotCrdSys` | 指定用于运动和 I/O 的坐标系统 (-1: 默认, 0: 基础, 1: 工具, 2: 用户1, 3: 用户2) |
| `PostRobotEmergencyStop` | 为安全响应立即停止所有机器人运动 |
| `PostInitJointTrajectory` | 初始化关节轨迹缓冲区 |
| `PostInsertJointTrajectoryPoints` | 将关节轨迹点插入控制器缓冲区以执行运动 |
[__SOURCE](7-hdr_client_driver/1-api-categories/3-project/README.md)
# 7.1.3 项目 API

### 概述

项目 API 类别为 HD Hyundai Robotics 控制器提供项目和作业管理功能。这些 API 使得监控项目执行状态、查询作业信息和管理作业成为可能。

### 可用的项目 API

| 功能 | 描述 |
|----------|-------------|
| `GetProjectRgen` | 查询当前项目执行状态 (0: 未运行, 1: 运行中, 2: 暂停) |
| `GetProjectJobsInfo` | 检索项目中所有已注册作业的元数据 (名称, 路径, 修改状态) |
| `PostProjectReloadUpdateJobs` | 重新加载并同步外部修改的作业以更新内存作业状态 |
| `PostProjectDeleteJob` | 从项目路径中删除指定的作业文件 |
[__SOURCE](7-hdr_client_driver/1-api-categories/4-file/README.md)
# 7.1.4 文件 API

### 概述

文件 API 类别提供用于 HD 现代机器人控制器的文件系统操作。这些 API 允许远程文件管理、文件上传/下载和目录管理。

### 可用的文件 API

| 功能 | 描述 |
|------|-------|
| `GetFiles` | 检索指定路径下的文件和文件夹列表 |
| `GetFileInfo` | 查询文件或目录的元数据（大小、时间戳、类型） |
| `GetFileList` | 检索仅包括文件、仅包括目录或所有的过滤列表 |
| `GetFileExist` | 检查指定的文件或目录是否存在 |
| `PostRenameFile` | 将文件或目录从一个路径重命名或移动到另一个路径 |
| `PostMkdir` | 在指定路径下创建新目录 |
| `PostFiles` | 将本地文件上传到控制器的指定位置 |
| `PostDeleteFile` | 删除控制器上的文件或目录 |
[__SOURCE](7-hdr_client_driver/1-api-categories/5-io/README.md)
# 7.1.5 I/O API

### 概述

I/O API 类别为 HD Hyundai Robotics 控制器提供 PLC 通信功能。这些 API 允许查询和设置 Hi6、Hi7 PLC 中的继电器值。

### 可用的 I/O API

| 函数 | 描述 |
|----------|-------------|
| `GetRelayValue` | 使用 "FB{index}.{relay_type}" 格式或简单格式如 "M"、"S" 从 Hi6、Hi7 PLC 查询继电器值 |
| `SetRelayValue` | 在机器人控制器的内部 PLC 中设置特定的继电器值。支持各种数据类型后缀 |
[__SOURCE](7-hdr_client_driver/1-api-categories/6-task/README.md)
# 7.1.6 任务 API

### 概述

任务 API 类别为 HD 现代机器人控制器提供任务执行和变量管理功能。这些 API 允许变量赋值、等待状态释放、程序计数器控制、表达式评估以及直接运动命令执行。

### 可用的任务 API

| 功能 | 描述 |
|----------|-------------|
| `PostAssignVar` | 使用表达式或 JSON 值将变量分配给任务（支持本地/全局作用域和持久性） |
| `PostReleaseWait` | 将任务[0] 从等待状态释放以恢复暂停的任务 |
| `PostSetCurPcIdx` | 手动设置任务[0] 的程序计数器（PC）索引（对调试或跳转到特定逻辑很有用） |
| `PostSolveExpr` | 在任务作用域内评估表达式（支持数学、逻辑和变量访问） |
| `PostExecuteMove` | 在机器人任务中执行直接运动命令（L、P、SP 等） |
[__SOURCE](7-hdr_client_driver/1-api-categories/7-etc/README.md)
# 7.1.7 杂项 API

### 概述

杂项 API 类别为 HD 现代机器人控制器提供额外的实用程序和系统管理功能。这些 API 包括系统时间管理和日志查询功能。

### 可用的杂项 API

| 功能 | 描述 |
|------|------|
| `GetDateTime` | 从机器人控制器查询当前系统日期和时间（年、月、日、小时、分钟、秒） |
| `PutDateTime` | 在机器人控制器上设置系统日期和时间（包括输入验证） |
| `GetLogManager` | 查询控制器日志并带有过滤选项（条目计数、类别 E、W、N、S、O、I、P、H、C、M、ID 范围、时间戳范围） |
[__SOURCE](8-hdr_simulation_gz/README.md)
# 8. Gazebo Simulation (`hdr_simulation_gz`)

The `hdr_simulation_gz` package provides a ROS2 + Gazebo (Ignition) simulation environment for HD Hyundai Robotics industrial robots. This package enables development, testing, and validation of robotic applications without physical hardware.

[Source Code] [hdr_simulation_gz] [GitHub Repository ↗](https://github.com/hyundai-robotics/hdr_simulation_gz)

### Key Features

- **Gazebo Integration**: Ignition Gazebo模拟支持
- **Physics Simulation**: 真实的机器人动态和碰撞检测
- **MoveIt2 Compatibility**: 在模拟环境中的运动规划
- **ros2_control Integration**: 使用 `gz_ros2_control/GazeboSimSystem` 插件

### Package Structure

| Directory | Contents | Purpose |
|-----------|----------|----------|
| `launch/` | 模拟启动文件 | 机器人生成和控制器设置 |
| `config/` | 控制器配置文件 | ros2_control YAML 文件 |

### Launch Files

#### Robot Spawning
```bash
# 使用 ros2_control 在 Gazebo 中生成机器人
ros2 launch hdr_simulation_gz hdr_gz_spawn.launch.py robot_model:=ha006b
```

#### MoveIt2 Integration
```bash
# 使用 MoveIt2 运动规划运行模拟
ros2 launch hdr_simulation_gz hdr_gz_moveit.launch.py robot_model:=hdr50_22
```

### Configuration Options

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `robot_model` | string | `ha006b` | 要模拟的机器人模型 |
| `use_sim` | bool | `true` | 启用 Gazebo 模拟模式 |
| `runtime_config_package` | string | `hdr_simulation_gz` | 控制器配置包 |
| `controllers_file` | string | `hdr_controllers.yaml` | 控制器配置文件 |
| `description_package` | string | `hdr_description` | URDF 包名称 |
| `description_file` | string | `hdr.urdf.xacro` | 机器人描述文件 |
| `initial_positions_file` | string | `initial_positions.yaml` | 初始关节位置 |
| `kinematics_file` | string | `kinematics.yaml` | 运动学求解器配置 |


### Future Improvements
- 传感器和工具模拟支持
- 世界和示例场景支持
[__SOURCE](9-hdr_msgs/README.md)
# 9. HD Hyundai Robotics ROS2 消息

### 概述

`hdr_msgs` 包定义了用于 HD Hyundai Robotics 软件栈的自定义 ROS2 消息类型。

### ROS2 消息

| 消息类型                | 描述                                                 |
|-----------------------|-------------------------------------------------------|
| `srv/DateTime.srv`    | 获取或设置机器人控制器的系统时间。输入包括完整的日期/时间字段（年、月、日、小时、分钟、秒）。 |
| `srv/Emergency.srv`   | 使用步骤参数（step_no, stop_at, stop_mode）测试紧急停止逻辑。用于仿真/测试场景。 |
| `srv/ExecuteCmd.srv`  | 作为字符串行列表执行控制台命令，具有可配置的执行间隔。对于原始低级命令如 rl.stop 很有用。 |
| `srv/ExecuteMove.srv` | 使用基于字符串的语句执行机器人移动命令。示例：“move L,spd=1sec,tool=1 [0, 0, 0, 0, 90, 0]”。 task_no标识任务索引（通常是 0）。 |
| `srv/FileList.srv`    | 查询机器人上的目录内容。可以通过布尔值过滤以包含文件或目录。 |
| `srv/FilePath.srv`    | 发送或查询文件路径以进行读取、删除或存在性检查等操作。 |
| `srv/FileRename.srv`  | 重命名或移动机器人控制器文件系统中的文件。 |
| `srv/FileSend.srv`    | 将文件从本地计算机上传到机器人控制器。需要源路径和目标路径。 |
| `srv/IoplcGet.srv`    | 读取 PLC 内存（例如，继电器、M、S、R）。支持直接寻址和基于名称的信号寻址。 |
| `srv/IoplcPost.srv`   | 使用符号名称如 M、S、R 或 FBx.y 写入 PLC 内存（继电器）。 |
| `srv/IoRequest.srv`   | 用于访问数字、串行或用户 I/O。类型字段指定 I/O 类型，如 'di'、'do'、'si' 或 'so'。 blk_no 和 sig_no 指定块和信号索引。“val” 字段在设置 I/O 值时使用，并在读取操作中忽略。 |
| `srv/JointTrajecotryPoints.srv` | 提供执行运动的轨迹点 |
| `srv/LogManager.srv`  | 使用类别（E、W 等）、ID 范围和时间戳过滤器查询日志条目。 |
| `srv/Number.srv`      | 通用服务，用于发送/接收整数。用于工具编号、坐标系统、索引设置等。 |
| `srv/OpCnd.srv`       | 读取或写入操作条件，如播放模式或用户坐标系统。 |
| `srv/PoseCur.srv`     | 根据内部配置获取当前机器人姿态（位置 + 定向），可在关节空间或工作空间中获取。 |
| `srv/ProgramCnt.srv`  | 设置程序执行指针（pno、sno、fno 等），以在任务逻辑中移动到特定位置。 |
| `srv/ProgramVar.srv`  | 读取或分配变量。可以指定范围（局部/全局）、表达式和持久性。 |
[__SOURCE](10-running/README.md)
# 10. ROS2 驱动执行与机器人控制

### 概述

本部分提供了使用 ROS2 驱动程序操作 HD 现代机器人机器人全面的指南。

HD 现代机器人 ROS2 系统提供以下控制方法：

- **MoveIt2 集成**：运动规划与执行
- **ros2_control**：硬件接口控制
- **ROS2 服务**：控制器 API 访问

### 下一步

- [MoveIt2 启动程序](1-launch-moveit2/README.md)
- [直接 ros2_control 控制](2-launch-ros2_control/README.md)
[__SOURCE](10-running/1-launch-moveit2/README.md)
# 10.1 使用 MoveIt2 运作

### 概述

使用 MoveIt2 运行 HD Hyundai Robotics 机器人的基本程序。

### 启动前准备

#### 硬件准备
- 开启机器人控制器并设置为远程模式
- 确保紧急停止按钮可达
- 验证网络连接（ping 192.168.1.150）
- 确认工作空间没有障碍物

#### 软件准备
- 设置 ROS2 环境：`source ~/ros2_ws/install/setup.bash`
- 验证机器人模型

### 基本启动程序

#### 1. 启动 MoveIt2
```bash
# 基本 MoveIt2 启动
ros2 launch hdr_moveit_config hdr_moveit.launch.py robot_model:=ha006b

# 使用指定 IP 地址启动
ros2 launch hdr_moveit_config hdr_moveit.launch.py \
    robot_model:=ha006b \
    robot_ip:=192.168.1.150
```

#### 2. 验证连接状态
```bash
# 检查关节状态
ros2 topic echo /joint_states --once

# 检查 MoveIt2 服务
ros2 service list | grep move_group
```

### 支持的机器人模型

- ha006b
- hdf7_9
- hdf8_8
- hdr10l_19
- hdr20_17
- hdr50_22
- hdr220_26
- hh020
- hdr35_20

### 安全注意事项

#### 紧急停止
- 始终保持硬件紧急停止按钮可达

#### 安全关机
1. 停止所有运动
2. 将机器人移动到安全位置
3. 终止 MoveIt2 节点
4. 关闭机器人控制器电源

### 常见故障排除

**连接问题**
- 验证网络连接：`ping 192.168.1.150`
- 确认机器人控制器处于远程模式

**当控制器无法启动时：**
- 验证机器人控制器处于远程模式
- 检查网络连接
- 确认机器人未处于紧急停止状态

**当关节状态未发布时：**
- 检查硬件接口连接状态
- 验证机器人控制器状态

**轨迹执行失败：**
- 检查关节限制
- 验证目标位置有效
- 检查控制器错误消息

#### 当机器人在电机开启和启动模式下不工作
**正常操作**
当同时启用 **Motor ON** 和 **Start Mode** 时，机器人正常运行。

**当机器人不工作**
如果在启用 **Motor ON** 时未激活 Start Mode，系统会生成错误 "外部命令操作已禁用 (E01554)。"
如果给出不可行的命令值（例如，超出物理限制），可能会发生轴超速错误，导致机器人停止。
在这种情况下，可以通过重新激活 **Motor ON + Start Mode** 来恢复系统。
[__SOURCE](10-running/2-launch-ros2_control/README.md)
# 10.2 ros2_control 系统执行

### 概述

解释 HD 现代机器人机器人的 ros2_control 系统的基本执行方法。

### 基本执行

#### 启动 ros2_control
```bash
# 基本启动
ros2 launch hdr_bringup hdr_control.launch.py robot_model:=ha006b

# 指定 IP 地址
ros2 launch hdr_bringup hdr_control.launch.py \
    robot_model:=ha006b \
    robot_ip:=192.168.1.150
```

### 控制器

#### 检查控制器状态
```bash
# 列出控制器
ros2 control list_controllers

# 检查硬件接口
ros2 control list_hardware_interfaces

# 检查关节状态
ros2 topic echo /joint_states
```

#### 激活/停用控制器
```bash
# 激活控制器
ros2 control switch_controllers --activate joint_trajectory_controller 

# 停用控制器
ros2 control switch_controllers --deactivate joint_trajectory_controller
```

### 默认控制器配置

ros2_control 提供以下控制器：

- **joint_state_broadcaster**: 发布关节状态
- **joint_trajectory_controller**: 轨迹跟踪控制

### 简单测试

#### 关节轨迹测试
```bash
# 简单关节移动测试
ros2 action send_goal /joint_trajectory_controller/follow_joint_trajectory \
    control_msgs/action/FollowJointTrajectory \
    "{
      trajectory: {
        joint_names: ['j1', 'j2', 'j3', 'j4', 'j5', 'j6'],
        points: [
          {
            positions: [0.0, 0.0, 0.0, 0.0, 0.0, 0.0],
            time_from_start: {sec: 2}
          }
        ]
      }
    }"
```

### 故障排除

#### 常见问题

**连接问题**
- 验证网络连接: `ping 192.168.1.150`
- 确认机器人控制器处于 REMOTE 模式

**当控制器无法启动时：**
- 验证机器人控制器处于 REMOTE 模式
- 检查网络连接
- 确认机器人不在紧急停止状态

**当关节状态未发布时：**
- 检查硬件接口连接状态
- 验证机器人控制器状态

**轨迹执行失败：**
- 检查关节限位
- 验证目标位置是否有效
- 检查控制器错误消息

#### 当机器人不在电机开启与启动模式下操作
**正常操作**
当同时启用 **电机开启** 和 **启动模式** 时，机器人正常运行。

**当机器人不操作时**
如果启用 **电机开启** 时未激活启动模式，系统会生成错误 "External Command Operation Disabled (E01554)。"
如果给出不可行的命令值（例如，超出物理限度），可能会导致轴超速错误，从而使机器人停止。
在这种情况下，可以通过重新激活 **电机开启 + 启动模式** 来恢复系统。

### 安全注意事项

- 在实际操作机器人时，始终保持紧急停止按钮可用
- 机器人出现意外行为时立即紧急停止
- 在首次使用时以低速进行测试