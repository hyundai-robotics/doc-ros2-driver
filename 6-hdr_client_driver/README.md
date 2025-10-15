# HD Hyundai Robotics Client Driver

The HDR client driver provides a comprehensive C++ library for communicating with HD Hyundai Robotics robot controllers via HTTP (Open API) and socket (TCP/UDP) interfaces. This library abstracts both communication layers and provides object-oriented interfaces for robot control and monitoring, file management, real-time command execution, and integration with ROS2.

> ❗ **Note**: Real-time interface (2ms cycle) for motion control, status feedback, and I/O operations is scheduled for release in **November 2025**.

> ❗ Important: All REST API-based communication requires the robot to be in REMOTE mode.

## Package Structure

| Directory | Description |
|-----------|-------------|
| `include/` | Header files for the HDR client driver library |
| `src/` | Source implementation of client driver functions |
| `src/functions/` | API category implementations for various robot controller functions |
| `examples/` | Example programs demonstrating how to use the driver APIs |