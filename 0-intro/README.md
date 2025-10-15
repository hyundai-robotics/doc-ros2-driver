# Overview

This manual provides a description of the HD Hyundai Robotics (HDR) ROS2 driver.

The HDR ROS2 driver integrates HD Hyundai Robotics industrial robot controllers (Hi6 series) with ROS2 systems to support both simulation environments and real robot control functions.

![hdr_main](../_assets/0_hdr_main.png)


## Prerequisites
Before using the HDR ROS2 driver, please make sure to check the following items:
- [Supported Controllers](1-controller-models/README.md) - Compatible Hi6 series controllers
- [Supported Robot Models](2-robot-models/README.md) - Compatible HD Hyundai Robotics robot models
- [System Requirements](3-requirements/README.md) - Hardware and software requirements
- [ROS2 Version](4-ros2-version/README.md) - Supported ROS2 versions
- [Robot Joint and Link Names](5-hdr-robot/README.md) - Robot joint and link naming conventions in ROS2

## Installation and Initial Setup
After verifying all the above items, please proceed with the ROS2 driver installation and initial setup according to the following procedures:
- [Repository Overview](1-repo-overview/README.md) - HDR ROS2 driver repository structure and architecture overview
- [Package Installation](2-installation/README.md) - HDR ROS2 driver build and installation method
- [Controller and PC Setup](3-initial-setup/README.md) - Initial setup method for using HDR ROS2 driver
- [Installation Verification](4-verifying/README.md) - Verify that installation and setup are completed correctly

## Quick Start with ROS2 Driver
After completing all the installation and initial setup processes above, you can start the HDR ROS2 driver and begin robot control through the following procedures:

- [Running ROS2 Driver](8-running/README.md) - ROS2 driver execution and robot control methods

⚠️ **Please make sure to check the prerequisites and complete all installation and initial setup before proceeding.**

⚠️ **Currently, the HD Hyundai Robotics ROS2 driver is supported on controller software version *v60.34-00* or higher. </br> The *v60.34-00* version is scheduled for official release in October 2025, so please refrain from using the ROS2 driver before the official release.**