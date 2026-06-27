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