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