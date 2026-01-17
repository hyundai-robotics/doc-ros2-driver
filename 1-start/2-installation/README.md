# Package Build and Installation
This section covers the installation process of the HD Hyundai Robotics ROS2 driver, including repository cloning, dependencies installation, and package build.

## Workspace Setup

### Create ROS2 Workspace

```bash
# Create workspace directory
mkdir -p ~/hdr_ws/src
cd ~/hdr_ws
```

### Clone Source Repositories

```bash
cd ~/hdr_ws/src

# HDR core driver and client library
git clone https://github.com/hyundai-robotics/hdr_ros2_driver.git
git clone https://github.com/hyundai-robotics/hdr_client_driver.git

# HDR description package
git clone https://github.com/hyundai-robotics/hdr_description.git

# Gazebo simulation
git clone https://github.com/hyundai-robotics/hdr_simulation_gz.git
```

## Dependencies Installation

### Install ROS2 Dependencies

```bash
cd ~/hdr_ws

# Update package database
rosdep update

# Install all dependencies for HDR packages
rosdep install --from-paths src --ignore-src --rosdistro $ROS_DISTRO -y
```

## Build Process

### Standard Build

```bash
cd ~/hdr_ws

# Build all packages with optimization
colcon build --symlink-install --cmake-args=-DCMAKE_BUILD_TYPE=Release
```

### Build Configuration Options
```bash
# Build with debug symbols
colcon build --symlink-install --cmake-args=-DCMAKE_BUILD_TYPE=Debug
```

### Environment Setup

```bash
cd ~/hdr_ws
source install/setup.bash

echo "source ~/hdr_ws/install/setup.bash" >> ~/.bashrc
```

## Next Steps

After successful package installation and build:
1. Proceed to [Initial Setup](../3-initial-setup/README.md) for controller and PC configuration
2. Run [Installation Verification](../4-verifying/README.md) tests