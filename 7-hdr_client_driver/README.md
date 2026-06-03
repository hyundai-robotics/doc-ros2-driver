# 7. HD Hyundai Robotics Client Driver

The HDR client driver provides a comprehensive C++ library for communicating with HD Hyundai Robotics robot controllers via HTTP (Open API) and socket (TCP/UDP) interfaces. This library abstracts both communication layers and provides object-oriented interfaces for robot control and monitoring, file management, real-time command execution, and integration with ROS2.

{% hint style="warning" %}
All REST API-based communication requires the robot to be in REMOTE mode.
{% endhint %}

### Package Structure

| Directory | Description |
|-----------|-------------|
| `include/` | Header files for the HDR client driver library |
| `src/` | Source implementation of client driver functions |
| `src/functions/` | API category implementations for various robot controller functions |
| `examples/` | Example programs demonstrating how to use the driver APIs |
