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