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