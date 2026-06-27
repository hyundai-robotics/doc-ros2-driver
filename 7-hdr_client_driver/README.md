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