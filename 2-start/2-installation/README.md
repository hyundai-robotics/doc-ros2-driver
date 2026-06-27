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