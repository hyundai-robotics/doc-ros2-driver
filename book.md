
[__SOURCE](README.md)
# Hi6 & Hi7 控制器功能手册 - ROS2 驱动程序

目前，兼容 ROS2 的控制器是 Hi6 系列，支持从控制器软件版本 **v60.34-00** 或更高版本。</br>
版本 **v60.34-00** 计划于 2026年第2季度正式发布。在正式发布之前，请避免使用 HD 现代机器人公司的 ROS2 驱动程序。 </br>
⚠️ **Hi7 型号计划发布，具体支持时间表尚未 finalized。我们将在正式发布日程确定后通过官方公告提供进一步的细节。请牢记这一点。**
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

本手册提供了 HD 现代机器人 (HDR) ROS2 驱动程序的说明。

HDR ROS2 驱动程序将 HD 现代机器人工业机器人控制器 (Hi6、Hi7 系列) 与 ROS2 系统集成，以支持仿真环境和实际机器人控制功能。

![hdr_main](../_assets/0_hdr_main.png)

### 先决条件
在使用 HDR ROS2 驱动程序之前，请确保检查以下项目：
- [支持的控制器](1-controller-models/README.md) - 兼容的 Hi6、Hi7 系列控制器
- [支持的机器人模型](2-robot-models/README.md) - 兼容的 HD 现代机器人模型
- [系统要求](3-requirements/README.md) - 硬件和软件要求
- [ROS2 版本](4-ros2-version/README.md) - 支持的 ROS2 版本
- [机器人关节和链接名称](5-hdr-robot/README.md) - ROS2 中的机器人关节和链接命名约定

### 安装和初始设置
在验证所有上述项目后，请按照以下步骤进行 ROS2 驱动程序的安装和初始设置：
- [代码库概述](1-repo-overview/README.md) - HDR ROS2 驱动程序代码库结构和架构概述
- [软件包安装](2-installation/README.md) - HDR ROS2 驱动程序的构建和安装方法
- [控制器和 PC 设置](3-initial-setup/README.md) - 使用 HDR ROS2 驱动程序的初始设置方法
- [安装验证](4-verifying/README.md) - 验证安装和设置是否正确完成

### 使用 ROS2 驱动程序的快速入门
在完成上述所有安装和初始设置过程后，您可以启动 HDR ROS2 驱动程序并通过以下程序开始机器人控制：

- [运行 ROS2 驱动程序](10-running/README.md) - ROS2 驱动程序执行和机器人控制方法

⚠️ **请确保检查先决条件并完成所有安装和初始设置后再继续。**

⚠️ **目前，HD 现代机器人 ROS2 驱动程序支持控制器软件版本 *v60.34-00* 或更高版本。</br> *v60.34-00* 版本计划于 2026 年第二季度正式发布，请在正式发布之前避免使用 ROS2 驱动程序。**
[__SOURCE](1-intro/1-controller-models/README.md)
# 1.1 支持的控制器模型
官方支持 ROS2 功能的 HD 现代机器人 Hi6 控制器模型如下：

- Hi6-N10
- Hi6-N20
- Hi6-N00(HK)
- Hi6-N00-60(HK)
- Hi6-N30(HK)
- Hi6-N80(HK)
- Hi6-T15

**控制器要求**：
- 软件版本：**60.32-00** 或更高（计划于十月发布）
- 操作模式：**REMOTE mode**

Hi7 控制器系列，包括未来的型号和支持计划，一旦最终确定，将立即在此列表中更新。

> ⚠️ **注意：** HD 现代机器人 ROS2 驱动程序**不支持** **Hi5** 控制器系列。

### 下一步

确认控制器兼容性后，请检查 [支持的机器人模型](../2-robot-models/README.md) 以验证您的机器人是否受到支持。
[__SOURCE](1-intro/2-robot-models/README.md)
# 1.2 支持的机器人型号

HD 현대 로보틱스 드라이버当前官方支持的机器人型号如下：

- ha006b
- hdf7_9
- hdf8_8
- hdr10l_19
- hdr20_17
- hdr50_22
- hdr220_26
- hh020
- hdr35_20

### 型号名称变更

> ❗ **注意:** 机器人型号 `hdf7_9`、`hdf8_8`、`hdr20_17`、`hdr50_22`、`hdr220_26`、`hdr35_20` 分别是型号 `HH7`、`HH8`、`UH020`、`HH050`、`HS220`、`UH035` 的重命名版本。

### 每个型号包含的内容

每个支持的机器人型号包括以下内容：

- **URDF**: 带碰撞网格的机器人URDF
- **Mesh**: 用于可视化的3D模型
- **MoveIt2配置**: 带有型号特定软限制的运动规划设置
- **Gazebo支持**: 仿真集成支持

### 下一步

确认机器人型号后，请继续检查 [系统要求](../3-requirements/README.md)，以验证您的系统是否正确配置。
[__SOURCE](1-intro/3-requirements/README.md)
# 1.3 系统要求

本页描述了运行 HD 现代机器人 ROS2 驱动程序的硬件和软件要求。

### 硬件要求

#### 机器人控制器
- **兼容控制器**: Hi6-N10, Hi6-N20, Hi6-N00(HK), Hi6-N00-60(HK), Hi6-N30(HK), Hi6-N80(HK), Hi6-T15
- **控制器软件版本**: **60.32-00** 或更高
- **操作模式**: 机器人必须设置为 **REMOTE** 模式
- **网络接口**: 以太网连接 (LAN1, LAN2 或 LAN3)

#### 开发PC
- **操作系统**: Ubuntu 22.04 LTS 或 Ubuntu 24.04 LTS
- **内存**: 最低 8GB RAM (建议 16GB 以进行仿真)
- **网络**: 以太网接口用于机器人通信
- **CPU**: 多核处理器 (建议 4 核或更多)

### 下一步

一旦您的系统满足所有要求，请检查 [支持的 ROS2 版本](../4-ros2-version/README.md)。
[__SOURCE](1-intro/4-ros2-version/README.md)
# 1.4 支持的 ROS2 版本

HD 现代机器人 ROS2 驱动程序支持在机器人控制器和仿真环境中经过测试和验证的特定 ROS2 发行版。

### 支持的 ROS2 发行版

- **ROS2 Humble Hawksbill** (Ubuntu 22.04 LTS)
- **ROS2 Jazzy Jalisco** (Ubuntu 24.04 LTS)

### 版本验证

安装后，验证您的 ROS2 设置：

```bash
# Source ROS2 environment
source /opt/ros/$ROS_DISTRO/setup.bash

# Check ROS2 version
ros2 doctor
```

### 后续步骤

在确认 ROS2 兼容性后，请继续查看 [Getting Started](../../1-start/README.md) 以进行安装。
[__SOURCE](1-intro/5-hdr-robot/README.md)
# 1.5 机器人关节和连接件名称

HD现代机器人遵循以下URDF中的关节和连接件命名约定。

### 关节名称

|关节编号|关节名称 </br>(URDF)|关节名称 </br>(TP)|
|:------:|:---:|:---:|
|1|j1|S|
|2|j2|H|
|3|j3|V|
|4|j4|R2|
|5|j5|B|
|6|j6|R1|


### 连接件名称

|连接件编号|连接件名称|
|:------:|:---:|
|0|base_link|
|1|lower_frame_link|
|2|upper_frame_link|
|3|arm_link|
|4|wrist_body_link|
|5|wrist_holder_link|
|6|flange_link|


### 连接件关系

|连接件编号|连接件名称|关节|父连接件|关节类型|备注|
|:------:|:---:|:---:|:------:|:---:|:---:|
||世界||||||
|0|base_link|world_joint|世界|固定|||
|1|lower_frame_link|j1|base_link|旋转||
|2|upper_frame_link|j2|lower_frame_link|旋转||
|3|arm_link|j3|upper_frame_link|旋转||
|4|wrist_body_link|j4|arm_link|旋转||
|5|wrist_holder_link|j5|wrist_body_link|旋转||
|6|flange_link|j6|wrist_holder_link|旋转||
||flange|flange_link-flange|flange_link|固定|ROS工业标准坐标系|
||tool0|flange-tool0|flange|固定|ROS工业标准坐标系|
[__SOURCE](2-start/README.md)
# 2. 入门

本节提供 HD 现代机器人 ROS2 驱动程序的安装、配置和执行的分步说明。请遵循本指南设置您的开发环境并与机器人建立通信。

### 安装和设置过程

1. [Repository Overview](1-repo-overview/README.md) - 理解包结构和关系
2. [Installation](2-installation/README.md) - 存储库克隆和构建
3. [Initial Setup](3-initial-setup/README.md) - 网络配置设置
4. [Verification](4-verifying/README.md) - 安装测试
[__SOURCE](2-start/1-repo-overview/README.md)
# 2.1 仓库概述

HD 现代汽车机器人 ROS2 驱动程序由多个互连的包组成，这些包共同提供机器人控制、仿真和运动规划功能。

### 仓库架构

```
HD 现代汽车机器人 ROS2 驱动程序

hdr_ros2_driver            # 主仓库
   hdr_bringup             # 机器人集成和控制启动文件
   hdr_ros2_driver         # 核心通信驱动
   hdr_hardware_interface  # ros2_control 集成
   hdr_moveit_config       # MoveIt 配置
   hdr_msgs                # HD 机器人自定义消息定义

hdr_client_driver          # C++ 客户端库

hdr_description            # 机器人 URDF 模型和网格

hdr_simulation_gz          # Gazebo 仿真集成
```

### 仓库内各包详细信息

- **[ROS2 驱动程序 (`hdr_ros2_driver`)](../../2-hdr_ros2_driver/README.md)** </br>
提供机器人控制、文件管理、I/O 操作和系统监控服务的主要 ROS2 节点

- **[HDR 客户端驱动程序 (`hdr_client_driver`)](../../6-hdr_client_driver/README.md)** </br>
实现与 HD 现代汽车机器人控制器的 TCP/UDP 通信协议的 C++ 库

- **[ROS2 控制集成 (`hdr_hardware_interface`)](../../3-hdr_hardware_interface/README.md)** </br>
与标准 ROS2 控制框架集成的 ros2_control SystemInterface

- **[机器人描述 (`hdr_description`)](../../4-hdr_description/README.md)** </br>
支持的机器人模型的 URDF/XACRO、碰撞/视觉网格和 RViz 配置

- **[MoveIt2 配置 (`hdr_moveit_config`)](../../5-hdr_moveit_config/README.md)** </br>
针对特定机器人模型的 MoveIt2 配置，包括 SRDF、软限制、运动学和运动规划设置

- **[Gazebo 仿真 (`hdr_simulation_gz`)](../../6-hdr_simulation_gz/README.md)** </br>
Gazebo Ignition 仿真集成

- **[自定义消息 (`hdr_msgs`)](../../7-hdr_msgs/README.md)** </br>
与 HD 现代汽车机器人控制器通信的自定义 ROS2 服务和消息定义


### 下一步

1. 查看上述链接的各个包文档。
2. 继续到 [Installation](../2-installation/README.md) 来构建软件包。
3. 在 [Initial Setup](../3-initial-setup/README.md) 中配置机器人连接。
[__SOURCE](2-start/2-installation/README.md)
# 2.2 包构建与安装
本节涵盖 HD Hyundai Robotics ROS2 驱动程序的安装过程，包括库克隆、依赖项安装和包构建。

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

# Gazebo 模拟
git clone https://github.com/hyundai-robotics/hdr_simulation_gz.git
```

### 依赖项安装

#### 安装 ROS2 依赖项

```bash
cd ~/hdr_ws

# 更新软件包数据库
rosdep update

# 安装 HDR 包的所有依赖项
rosdep install --from-paths src --ignore-src --rosdistro $ROS_DISTRO -y
```

### 构建过程

#### 标准构建

```bash
cd ~/hdr_ws

# 构建所有带优化的包
colcon build --symlink-install --cmake-args=-DCMAKE_BUILD_TYPE=Release
```
#### 构建配置选项
```bash
# 使用调试符号进行构建
colcon build --symlink-install --cmake-args=-DCMAKE_BUILD_TYPE=Debug
```

#### 环境设置

```bash
cd ~/hdr_ws
source install/setup.bash

echo "source ~/hdr_ws/install/setup.bash" >> ~/.bashrc
```

### 下一步

在成功安装和构建包后：
1. 继续进行 [初始设置](../3-initial-setup/README.md) 以配置控制器和PC
2. 运行 [安装验证](../4-verifying/README.md) 测试
[__SOURCE](2-start/3-initial-setup/README.md)
# 2.3 控制器与 PC 通信设置

本指南涵盖了您开发 PC 上网络接口的配置，以便与 HD Hyundai Robotics 机器人控制器进行通信。

### 前提条件
⚠️ 在开始设置之前，请验证以下内容：
- **机器人控制器软件版本**：Hi6、Hi7 系列控制器，软件版本为 **60.32-00** 或更高

### 网络配置概述

PC 必须配置为通过以太网与机器人控制器通信。默认配置使用 192.168.1.x 子网，控制器地址为 192.168.1.150。

### 默认网络配置（使用 LAN1）

| 组件 | 参数 | 默认值 |
|-----------|-----------|---------------|
| **PC IP 地址** | 静态 IP | 192.168.1.x (用户配置) |
| **机器人控制器 IP** | 静态 IP | 192.168.1.150 |
| **子网掩码** | 网络掩码 | 255.255.255.0 |
| **网关** | 默认网关 | 192.168.1.1  |

### 电缆连接

![controller](../../_assets/controller.png)

1. **找到机器人控制器以太网端口**
   - **Hi6-N 控制器**：主模块顶部的以太网端口
   - **Hi6-T 控制器**：控制器前面板的以太网端口

2. **连接以太网电缆**
   - 使用 Cat5e 或 Cat6 以太网电缆
   - **建议**：使用 LAN1（通常预配置为 192.168.1.x）
   - LAN2、LAN3 端口也可用，具有不同的默认控制器 IP： </br>
      LAN2: 192.168.4.150 → PC 需要配置为 192.168.4.x 范围 </br>
      LAN3: 192.168.3.150 → PC 需要配置为 192.168.3.x 范围

3. **验证物理连接**
   - 确保电缆连接牢固
   - 检查网络端口 LED 指示灯（如果可用）

### PC 网络接口配置

![LAN_com](../../_assets/LAN_com.png)

#### 使用网络管理器 GUI

##### Ubuntu 桌面 (GNOME)

1. **打开网络设置**
   - 点击右上角的网络图标
   - 选择“有线设置”或转到设置 → 网络

2. **配置有线连接**
   - 点击有线连接旁边的齿轮图标
   - 导航到“IPv4”标签

3. **设置静态IP配置（使用LAN1）**
   - **方法**：手动
   - **地址**：192.168.1.100
   - **子网掩码**：255.255.255.0
   - **网关**：192.168.1.1

4. **应用设置**
   - 点击“应用”，然后断开再重新连接网络接口

![ip_setup](../../_assets/ip_setup.png)

### 验证

#### 验证网络配置

```bash
# 测试网络连通性
ping -c 4 192.168.1.150
```

![ping_test](../../_assets/ping_test.png)
[__SOURCE](2-start/4-verifying/README.md)
# 2.4 安装验证

本指南提供验证程序，以确认 HD Hyundai Robotics ROS2 驱动程序已正确安装、配置并准备好操作。

#### 机器人模式配置

HDR ROS2 驱动程序仅在机器人处于 **REMOTE** 模式时操作。

在运行 ROS2 驱动程序之前，请通过将教导挂件 (TP) 上的模式开关切换到 REMOTE 位置来设置控制器为远程控制模式。

![ip_setup](../../_assets/tp_operate.png)

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
# 验证关节状态是否被发布
ros2 topic list | grep joint_states

# 监控关节状态
ros2 topic echo /joint_states --once

# 检查发布频率
ros2 topic hz /joint_states
```
[__SOURCE](3-hdr_ros2_driver/README.md)
# 3. ROS2 驱动程序 (`hdr_ros2_driver`)

`hdr_ros2_driver` 包提供了一个核心 ROS2 驱动程序，用于与 HD 现代机器人公司的开放 API 进行接口。这种驱动程序通过 REST API 实现与机器人控制器的全面通信，支持机器人控制、监控、文件操作和系统管理的服务。

### 关键特性

- **机器人状态发布**：通过 `/joint_states` 主题提供实时关节状态信息
- **运动控制**：通过 ROS2 动作进行关节轨迹控制
- **全面服务**：按功能组织的超过 30 个服务端点


### 详细文档

- [启动说明](1-launch/README.md) - 驱动程序执行的启动文件
- [配置参数](2-parameters/README.md) - 启动中可用的参数
- [提供的话题](3-topics/README.md) - 发布的机器人状态信息
- [可用的动作](4-actions/README.md) - 关节轨迹执行和运动控制
- [支持的 ROS2 服务](5-services/README.md) - API 服务参考
[__SOURCE](3-hdr_ros2_driver/1-launch/README.md)
# 3.1 HDR ROS2 驱动程序启动

本节介绍如何启动 HDR ROS2 驱动程序。

### 基本启动

#### HDR ROS2 驱动程序启动
```bash
# 使用默认参数启动
ros2 launch hdr_ros2_driver hdr_ros2_driver_launch.py
```

这将启动驱动程序，使用：
- 默认 IP：192.168.1.150
- 默认端口：8888

### 自定义配置

#### 自定义 IP 和端口
```bash
# 使用自定义网络设置启动
ros2 launch hdr_ros2_driver hdr_ros2_driver_launch.py \
  openapi_ip:=192.168.0.10 \
  openapi_port:=8080
```

### 启动参数

| 参数 | 类型 | 默认 | 描述 |
|------|------|------|------|
| `openapi_ip` | 字符串 | `192.168.1.150` | 机器人控制器服务器 IP 地址 |
| `openapi_port` | 整数 | `8888` | 控制器服务器端口编号 |
| `robot_model` | 字符串 | `ha006b` | 机器人型号名称 |

### 验证

启动后，验证驱动程序是否正在运行：

```bash
# 检查驱动程序节点是否活动
ros2 node list | grep hdr_ros2_driver

# 列出可用服务
ros2 service list | grep hdr_ros2_driver

# 测试基本连接
ros2 service call /hdr_ros2_driver/get/api_ver std_srvs/srv/Trigger
```

### 网络设置前提条件
在启动之前，请确保正确的网络配置：

1. **以太网连接**：通过LAN1、LAN2或LAN3将PC连接到机器人控制器
2. **控制器IP**：默认192.168.1.150（可通过教学挂件配置）
3. **PC IP**：设置为192.168.1.x范围（x ≠ 150）
4. **远程模式**：确保机器人控制器处于远程模式

### 故障排除

#### 常见问题

1. **连接超时**
   - 验证机器人IP和端口：`ping 192.168.1.150`
   - 检查以太网电缆连接

2. **服务不可用**
   - 验证驱动程序是否成功启动
   - 检查ROS2环境是否已被引入
   - 检查启动输出中的错误信息
   - 确保机器人处于远程模式
   - 验证控制器软件版本为**60.32-00**或更高
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
# 3.3 可用的操作

### 概述

ROS2 驱动程序提供了机器人关节轨迹控制的动作接口。动作允许异步操作，具有进度反馈和取消功能。

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
# 3.4 ROS2 驱动服务

### 概述

`hdr_ros2_driver` 提供多种 ROS2 服务用于与 HD 现代机器人 Hi6 控制器进行通信。

### 服务类别

| 类别 | 描述 |
|----------|-------------|
| **[控制服务](1-control/README.md)** | 机器人控制，电机电源，应急停止，坐标系统，I/O 管理 |
| **[任务管理](2-task/README.md)** | 变量赋值，运动执行，程序控制 |
| **[文件管理](3-file/README.md)** | 文件上传/下载，目录操作 |
| **[PLC 通信](4-plc/README.md)** | PLC 继电器值控制 |
| **[控制台命令](5-console/README.md)** | 控制台命令执行，系统时间，日志管理 |
| **[项目管理](6-project/README.md)** | 作业信息，作业删除/重载 |
| **[版本信息](7-version/README.md)** | API 版本，系统版本查询 |

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

# 检查电机状态
ros2 service call /hdr_ros2_driver/robot/get/motor_state std_srvs/srv/Trigger

# 打开电机电源
ros2 service call /hdr_ros2_driver/robot/post/motor_power std_srvs/srv/Trigger
```
[__SOURCE](4-hdr_hardware_interface/README.md)
# 4. ROS2 控制集成 (`hdr_hardware_interface`)

### 概述

`hdr_hardware_interface` 包提供 `ros2_control` SystemInterface，以将 HD 现代机器人基于开放 API 的控制器与 ROS2 控制框架连接。它将关节位置状态和命令接口映射到基于 HTTP 的机器人服务，处理控制器生命周期和实时姿态跟踪。

### 包结构

| 目录                               | 描述                                                                     |
| ---------------------------------- | ------------------------------------------------------------------------ |
| `include/`                         | 包含 `HDRRobotHardware` 和工具助手的 C++ 头文件                            |
| `src/`                             | SystemInterface 逻辑实现                                                |
| `launch/`                          | 用于执行 `ros2_control` 接口的启动文件                                   |
| `config/`                          | 控制器和运动学设置的 YAML 配置文件                                        |
| `hdr_hardware_interface_plugin.xml` | 插件库的元数据                                                           |

---

### 用法

###### 使用 ros2_control 启动 HDR 硬件接口

```bash
ros2 launch hdr_hardware_interface ros2_control.launch.py \
  robot_model:=hdf7_9 \
  openapi_ip:=192.168.1.150 \
  openapi_port:=8888
```

###### 插件配置
要启用硬件接口，请在 URDF 或 xacro 中包含它到 `<ros2_control>` 内

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

##### 配置选项

| 参数                         | 类型    | 默认                              | 描述                                                                   |
|---------------------------|---------|----------------------------------|------------------------------------------------------------------------|
| `robot_model`             | 字符串  | `"ha006b"`                       | 机器人型号名称                                                       |
| `openapi_ip`              | 字符串  | `"192.168.1.150"`                | 机器人控制器的 HTTP API IP 地址                                      |
| `command_start_time`   | 浮点数  | `-1.0`                           | 命令执行时间（-1.0 表示立即执行）                                      |
| `command_buffer_size`  | int    | ` (5)`                             | 命令数据缓冲区大小                                 |
| `use_sim`                 | bool   | `false`                         | 启用使用`gz_ros2_control/GazeboSimSystem`插件的仿真模式，通常用于与Ignition Gazebo的集成<br>`use_sim_time`参数也设置为true以与仿真时间同步     |
| `use_mock_hardware`       | bool   | `false`                         | 启用使用`mock_components/GenericSystem`的虚拟硬件接口，以在没有机器人的情况下进行测试   |
| `initial_positions_file`  | string | `""`                            | 可选的YAML文件，指定初始关节位置                       |
| `controllers_config_package` | string | `"hdr_hardware_interface"`     | 包含配置YAML的包名称                                       |
| `controllers_file`        | string | `"default_controllers.yaml"`   | 控制器配置YAML文件名                                     |
| `kinematics_file`         | string | `"default_kinematics.yaml"`    | 运动学插件配置YAML文件名                              |


##### Topics

| Topic Name                   | Message Type                   | Description                               |
| ---------------------------- | ------------------------------ | ----------------------------------------- |
| `/joint_states`              | sensor_msgs::msg::JointState | 发布当前关节状态，包括位置信息 |
| `/controller_manager/status` | lifecycle_msgs::msg::State   | ros2_control管理器的生命周期状态 |

##### Actions

| Action Name                                            | Action Type                                   | Description                                |
| ------------------------------------------------------ | --------------------------------------------- | ------------------------------------------ |
| `/joint_trajectory_controller/follow_joint_trajectory` | control_msgs::action::FollowJointTrajectory | 通过ROS2动作执行关节轨迹命令 |

##### Services

| Service Name                                   | Service Type                                         | Description                         |
| ---------------------------------------------- | ---------------------------------------------------- | ----------------------------------- |
| `/controller_manager/list_controllers`         | controller_manager_msgs/srv/ListControllers        | 返回活动控制器列表     |
| `/controller_manager/list_hardware_interfaces` | controller_manager_msgs/srv/ListHardwareInterfaces | 返回可用的关节命令和状态接口 |
| `/controller_manager/switch_controller`        | controller_manager_msgs/srv/SwitchController       | 激活或停用控制器  |
| `/controller_manager/load_controller`          | controller_manager_msgs/srv/LoadController         | 加载控制器             |
| `/controller_manager/unload_controller`        | controller_manager_msgs/srv/UnloadController       | 卸载指定的控制器。    |
[__SOURCE](5-hdr_description/README.md)
# 5. 机器人 URDF (`hdr_description`)

`hdr_description` 包含了 ROS2 中 HD 现代机器人机器人的机器人 URDF、网格和可视化配置。该软件包提供了模拟、可视化和运动规划所需的基本 URDF/XACRO 定义。

### 主要特性

- **特定机器人模型的 URDF**：所有支持的机器人模型的 URDF/XACRO 文件
- **3D 网格**：用于准确模拟的碰撞和视觉网格
- **RViz 集成**：预配置的可视化设置
- **ros2_control 集成**：关节接口定义

### 包结构

| 目录      | 内容                     | 目的                   |
|-----------|-------------------------|------------------------|
| `urdf/`   | 机器人 URDF 文件        | URDF/XACRO 定义       |
| `meshes/` | 3D 模型网格文件         | 碰撞和视觉表示       |
| `launch/` | 可视化启动文件          | RViz 显示配置          |
| `rviz/`   | RViz 配置文件           | 显示设置和插件        |

### URDF 配置

#### 主要文件
- **`hdr.urdf.xacro`**：包含所有组件的顶级宏
- **`hdr.ros2_control.xacro`**：ros2_control 硬件接口宏

#### 机器人特定文件
每个机器人模型在 `urdf/robots/` 下有自己的目录：
- `ha006b.urdf.xacro`
- `hdf7_9.urdf.xacro`
- `hdf8_8.urdf.xacro`
- `hdr10l_19.urdf.xacro`
- `hdr20_17.urdf.xacro`
- `hdr50_22.urdf.xacro`
- `hdr220_26.urdf.xacro`
- `hh020.urdf.xacro`
- `hdr35_20.urdf.xacro`

### 使用示例

#### 在 RViz 中可视化
```bash
ros2 launch hdr_description display_robot.launch.py robot_model:=ha006b
```

#### 启动参数

| 参数         | 类型    | 默认      | 描述                |
|--------------|---------|-----------|---------------------|
| `robot_model`| string  | `ha006b`  | 要显示的机器人模型 |
| `description_package` | string | `hdr_description` | 包含URDF文件的包 |
| `description_file` | string | `hdr.urdf.xacro` | 主URDF/XACRO文件 |

### 网格质量

该包为每个机器人提供两种类型的网格：

#### 视觉网格
- 高分辨率网格以实现真实的可视化
- 细致的表面纹理和材料
- 用于RViz和Gazebo中的视觉表示

#### 碰撞网格
- 简化的网格用于碰撞检测
- 针对计算效率进行了优化
- 被物理引擎和运动规划器使用

有关特定模型的详细信息，请参见 [支持的机器人模型](../0-intro/2-robot-models/README.md)。
[__SOURCE](6-hdr_moveit_config/README.md)
# 6. MoveIt2 配置 (`hdr_moveit_config`)

`hdr_moveit_config` 包提供了在实际和模拟环境中控制 HD Hyundai Robotics 机器人的 MoveIt2 配置包。该包包括特定于机器人的运动规划配置，带有 SRDF 定义、关节限制和控制器设置。

### 主要特性

- **特定机器人配置**：每个支持的机器人模型的个别 MoveIt2 设置
- **SRDF 定义**：带有规划组和姿势的语义机器人描述
- **关节限制管理**：安全操作的速度和加速度缩放
- **运动学集成**：正/逆运动学求解器配置
- **控制器集成**：ros2_control 和轨迹执行设置

### 包组织

每个机器人模型都有自己的 MoveIt2 配置包：

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
- **initial_positions.yaml**：默认起始姿势

### 安全考虑

#### 速度缩放
**≤ 0.5** 的缩放因子建议用于稳定操作：

```yaml
default_velocity_scaling_factor: 0.5
default_acceleration_scaling_factor: 0.5
```
#### 关节限制
文件 `joint_limits.yaml` 定义：
- 最大关节速度
- 最大关节加速度
- 软件位置限制
- 运动规划的缩放因子

### 启动

```bash
ros2 launch hdr_bringup hdr_moveit.launch.py robot_model:=ha006b
```

![hdr_moveit](../_assets/hdr_moveit.png)

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


### 自定义

要修改运动规划行为：
1. 编辑 `joint_limits.yaml` 以设置速度/加速度限制（不能超过 URDF 中每个关节定义的最大速度）
2. 修改 `ompl_planning.yaml` 以进行规划器特定设置
3. 更新 SRDF 以新增规划组或姿势
4. 调整 `controllers.yaml` 中的控制器参数
[__SOURCE](7-hdr_client_driver/README.md)
# 7. HD Hyundai Robotics 客户端驱动程序

HDR 客户端驱动程序提供了一个全面的 C++ 库，用于通过 HTTP (开放 API) 和套接字 (TCP/UDP) 接口与 HD Hyundai Robotics 机器人控制器进行通信。该库抽象了两个通信层，并提供面向对象的接口用于机器人控制和监控、文件管理、实时命令执行以及与 ROS2 的集成。

> ❗ 重要：所有基于 REST API 的通信要求机器人处于远程模式。

### 包结构

| 目录        | 描述                                   |
|-------------|----------------------------------------|
| `include/`  | HDR 客户端驱动库的头文件              |
| `src/`      | 客户端驱动函数的源实现                |
| `src/functions/` | 各种机器人控制器功能的 API 类别实现 |
| `examples/` | 演示如何使用驱动 API 的示例程序        |
[__SOURCE](7-hdr_client_driver/1-api-categories/README.md)
# 7.1 API类别

HDR客户端驱动程序支持以下API类别：

### 支持的API类别

HDR客户端驱动程序提供以下API类别，对应于机器人控制器的各种功能：

- **[控制](1-control/README.md)** - 基本机器人控制操作
- **[机器人](2-robot/README.md)** - 机器人运动和状态管理
- **[项目](3-project/README.md)** - 项目和任务管理
- **[文件](4-file/README.md)** - 文件系统操作
- **[输入/输出](5-io/README.md)** - 输入/输出控制
- **[任务](6-task/README.md)** - 任务执行和变量管理
- **[其他](7-etc/README.md)** - 系统实用工具
[__SOURCE](8-hdr_simulation_gz/README.md)
# 8. Gazebo模拟 (`hdr_simulation_gz`)

`hdr_simulation_gz`包为HD现代机器人工业机器人提供了一个ROS2 + Gazebo（Ignition）模拟环境。该包使得在没有物理硬件的情况下开发、测试和验证机器人应用成为可能。

### 主要特点

- **Gazebo集成**：支持Ignition Gazebo模拟
- **物理模拟**：逼真的机器人动态和碰撞检测
- **MoveIt2兼容性**：模拟环境中的运动规划
- **ros2_control集成**：使用`gz_ros2_control/GazeboSimSystem`插件

### 包结构

| 目录      | 内容                  | 目的                   |
|-----------|-----------------------|------------------------|
| `launch/` | 模拟启动文件          | 机器人生成和控制器设置 |
| `config/` | 控制器配置文件        | ros2_control YAML文件   |

### 启动文件

#### 机器人生成
```bash
# 在Gazebo中使用ros2_control生成机器人
ros2 launch hdr_simulation_gz hdr_gz_spawn.launch.py robot_model:=ha006b
```

#### MoveIt2集成
```bash
# 使用MoveIt2运动规划运行模拟
ros2 launch hdr_simulation_gz hdr_gz_moveit.launch.py robot_model:=hdr50_22
```

### 配置选项

| 参数                     | 类型   | 默认值      | 描述                     |
|-------------------------|--------|-------------|--------------------------|
| `robot_model`           | 字符串 | `ha006b`    | 要模拟的机器人模型      |
| `use_sim`              | 布尔值 | `true`      | 启用Gazebo模拟模式      |
| `runtime_config_package`| 字符串 | `hdr_simulation_gz` | 控制器配置包        |
| `controllers_file`      | 字符串 | `hdr_controllers.yaml` | 控制器配置文件     |
| `description_package`   | 字符串 | `hdr_description` | URDF包名称          |
| `description_file`      | 字符串 | `hdr.urdf.xacro` | 机器人描述文件      |
| `initial_positions_file` | 字符串 | `initial_positions.yaml` | 初始关节位置     |
| `kinematics_file`      | 字符串 | `kinematics.yaml` | 运动学求解器配置     |

### 未来改进
- 传感器和工具模拟支持
- 世界和示例场景支持
[__SOURCE](9-hdr_msgs/README.md)
# 9. HD 현대 로보틱스 ROS2 메시지

### 개요

`hdr_msgs` 패키지는 HD 현대 로보틱스 소프트웨어 스택에서 사용하는 맞춤형 ROS2 메시지 유형을 정의합니다.


### ROS2 메시지

| 메시지 유형           | 설명                                                |
|-----------------------|-----------------------------------------------------|
| `srv/DateTime.srv`    | 로봇 컨트롤러의 시스템 시간을 가져오거나 설정합니다. 입력에는 전체 날짜/시간 필드(연도, 월, 일, 시, 분, 초)가 포함됩니다. |
| `srv/Emergency.srv`   | 단계 매개변수(단계_no, 정지_at, 정지_모드)를 사용하여 비상 정지 논리를 테스트합니다. 시뮬레이션/테스트 시나리오에 사용됩니다. |
| `srv/ExecuteCmd.srv`  | 구성 가능한 실행 간격으로 문자열 목록으로 콘솔 명령을 실행합니다. rl.stop과 같은 원시 저수준 명령에 유용합니다. |
| `srv/ExecuteMove.srv` | 문자열 기반 설명을 사용하여 로봇 이동 명령을 실행합니다. 예: "move L,spd=1sec,tool=1 [0, 0, 0, 0, 90, 0]". task_no는 작업 인덱스(일반적으로 0)를 식별합니다. |
| `srv/FileList.srv`    | 로봇의 디렉토리 내용을 조회합니다. 부울 값을 통해 파일 또는 디렉토리를 포함하도록 필터링할 수 있습니다. |
| `srv/FilePath.srv`    | 읽기, 삭제 또는 존재 여부 확인과 같은 작업을 위한 파일 경로를 전송하거나 조회합니다. |
| `srv/FileRename.srv`  | 로봇 컨트롤러의 파일 시스템에서 파일을 이름 변경하거나 이동합니다. |
| `srv/FileSend.srv`    | 로컬 PC에서 로봇 컨트롤러로 파일을 업로드합니다. 소스 및 대상 경로가 필요합니다. |
| `srv/IoplcGet.srv`    | PLC 메모리(예: 중계기, M, S, R)를 읽습니다. 직접 주소 지정 및 이름 기반 신호 주소 지정을 모두 지원합니다. |
| `srv/IoplcPost.srv`   | M, S, R 또는 FBx.y와 같은 기호 이름을 사용하여 PLC 메모리(중계기)에 씁니다. |
| `srv/IoRequest.srv`   | 디지털, 직렬 또는 사용자 I/O에 접근하는 데 사용됩니다. 유형 필드는 'di', 'do', 'si' 또는 'so'와 같은 I/O 종류를 지정합니다. blk_no와 sig_no는 블록 및 신호 인덱스를 지정합니다. 'val' 필드는 I/O 값을 설정할 때 사용되며 읽기 작업 중에는 무시됩니다. |
| `srv/JointTrajecotryPoints.srv` | 모션 실행을 위한 궤적 포인트를 제공합니다. |
| `srv/LogManager.srv`  | 카테고리(E, W 등), ID 범위 및 타임스탬프 필터를 사용하여 로그 항목을 조회합니다. |
| `srv/Number.srv`      | 정수를 전송/수신하기 위한 범용 서비스입니다. 도구 번호, 좌표계, 인덱스 설정 등에 사용됩니다. |
| `srv/OpCnd.srv`       | 재생 모드 또는 사용자 좌표계와 같은 운영 조건을 읽거나 씁니다. |
| `srv/PoseCur.srv`     | 내부 구성에 따라 관절 공간 또는 작업 영역에서 현재 로봇 포즈(위치 + 방향)를 가져옵니다. |
| `srv/ProgramCnt.srv`  | 특정 작업 논리에서 특정 위치로 이동하기 위해 프로그램 실행 포인터(pno, sno, fno 등)를 설정합니다. |
| `srv/ProgramVar.srv`  | 변수를 읽거나 할당합니다. 범위(로컬/전역), 표현식 및 지속성을 지정할 수 있습니다. |
[__SOURCE](10-running/README.md)
# 10. ROS2 驱动程序执行和机器人控制

### 概述

本节提供了使用 ROS2 驱动程序操作 HD Hyundai Robotics 机器人的全面指南。

HD Hyundai Robotics ROS2 系统提供以下控制方法：

- **MoveIt2 集成**：运动规划和执行
- **ros2_control**：硬件接口控制
- **ROS2 服务**：控制器 API 访问

### 下一步

- [MoveIt2 启动程序](1-launch-moveit2/README.md)
- [直接 ros2_control 控制](2-launch-ros2_control/README.md)
[__SOURCE](10-running/1-launch-moveit2/README.md)
# 10.1 使用 MoveIt2 运行

### 概述

通过 MoveIt2 运行 HD 韩国现代机器人机器人的基本程序。

### 启动前准备

#### 硬件准备
- 打开机器人控制器并设置为 REMOTE 模式
- 确保紧急停止按钮可以访问
- 验证网络连接（ping 192.168.1.150）
- 确认工作区域没有障碍物

#### 软件准备
- 设置 ROS2 环境： `source ~/ros2_ws/install/setup.bash`
- 验证机器人模型

### 基本启动程序

#### 1. 启动 MoveIt2
```bash
# 基本 MoveIt2 启动
ros2 launch hdr_moveit_config hdr_moveit.launch.py robot_model:=ha006b

# 使用指定的 IP 地址启动
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

### 安全预防措施

#### 紧急停止
- 始终保持硬件紧急停止按钮易于接触

#### 安全关闭
1. 停止所有运动
2. 将机器人移动到安全位置
3. 终止 MoveIt2 节点
4. 关闭机器人控制器电源

### 常见故障排除

**连接问题**
- 验证网络连接: `ping 192.168.1.150`
- 确认机器人控制器处于遥控模式

**当控制器无法启动时:**
- 验证机器人控制器处于遥控制模式
- 检查网络连接
- 确认机器人不处于紧急停止状态

**当关节状态未发布时:**
- 检查硬件接口连接状态
- 验证机器人控制器状态

**轨迹执行失败:**
- 检查关节限制
- 验证目标位置有效
- 检查控制器错误消息

#### 当机器人在电机开启和启动模式下不工作时
**正常操作**
当 **电机开启** 和 **启动模式** 同时启用时，机器人正常工作。

**当机器人不工作时**
如果在启用 **电机开启** 的情况下未激活启动模式，则系统会生成错误 "外部命令操作已禁用 (E01554)。"  
如果给出不可行的命令值（例如，超出物理限制），可能会发生轴超速错误，导致机器人停止。  
在这种情况下，可以通过重新激活 **电机开启 + 启动模式** 来恢复系统。
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
- **joint_trajectory_controller**: 轨迹跟随控制

### 简单测试
#### 关节轨迹测试
```bash
# 简单关节运动测试
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
- 确认机器人控制器处于远程模式

**当控制器无法启动时：**
- 验证机器人控制器处于远程模式
- 检查网络连接
- 确认机器人不处于紧急停止状态

**当关节状态未发布时：**
- 检查硬件接口连接状态
- 验证机器人控制器状态

**轨迹执行失败：**
- 检查关节限制
- 验证目标位置是否有效
- 检查控制器错误消息

#### 当机器人不在电机开启和启动模式下操作时
**正常操作**
当两个**电机开启**和**启动模式**都启用时，机器人正常操作。

**当机器人不操作时**
如果在启用**电机开启**的情况下没有激活启动模式，系统将生成错误 "外部命令操作被禁用 (E01554)"。
如果给出不合理的命令值（例如，超出物理限制），可能会发生轴过速错误，导致机器人停止。
在这种情况下，可以通过重新激活**电机开启 + 启动模式**来恢复系统。
### 安全注意事项

- 在实际操作机器人时，始终保持紧急停止按钮可及
- 如果机器人出现意外行为，立即进行紧急停止
- 第一次使用时应以低速进行测试