# 5. Robot URDF (`hdr_description`)

`hdr_description`  包含 HD 现代机器人在 ROS2 中的机器人 URDF、网格和可视化配置。该包提供了模拟、可视化和运动规划所需的基本 URDF/XACRO 定义。

[Source Code] [GitHub Repository ↗](https://github.com/hyundai-robotics/hdr_description)

### Key Features

- **机器人模型特定 URDF**：所有支持的机器人模型的 URDF/XACRO 文件
- **3D 网格**：用于准确模拟的碰撞和视觉网格
- **RViz 集成**：预配置的可视化设置
- **ros2_control 集成**：关节接口定义

### Package Structure

| Directory | Contents | Purpose |
|-----------|----------|----------|
| `urdf/` | 机器人 URDF 文件 | URDF/XACRO 定义 |
| `meshes/` | 3D 模型网格文件 | 碰撞和视觉表示 |
| `launch/` | 可视化启动文件 | RViz 显示配置 |
| `rviz/` | RViz 配置文件 | 显示设置和插件 |

### URDF Configuration

#### Main Files
- **`hdr.urdf.xacro`**：包含所有组件的顶层宏
- **`hdr.ros2_control.xacro`**：ros2_control 硬件接口宏

#### Robot-Specific Files
每个机器人模型在 `urdf/robots/` 下都有自己的目录：
- `ha006b.urdf.xacro`
- `hdf7_9.urdf.xacro`
- `hdf8_8.urdf.xacro`
- `hdr10l_19.urdf.xacro`
- `hdr20_17.urdf.xacro`
- `hdr50_22.urdf.xacro`
- `hdr220_26.urdf.xacro`
- `hh020.urdf.xacro`
- `hdr35_20.urdf.xacro`

### Usage Examples

#### Visualization in RViz
```bash
ros2 launch hdr_description display_robot.launch.py robot_model:=ha006b
```

#### Launch Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `robot_model` | string | `ha006b` | 要显示的机器人模型 |
| `description_package` | string | `hdr_description` | 包含 URDF 文件的包 |
| `description_file` | string | `hdr.urdf.xacro` | 主 URDF/XACRO 文件 |

### Mesh Quality

该包为每个机器人提供两种类型的网格：

#### Visual Meshes
- 高分辨率网格以实现真实的可视化
- 详细的表面纹理和材料
- 用于 RViz 和 Gazebo 中的视觉表示

#### Collision Meshes
- 简化的网格用于碰撞检测
- 针对计算效率进行了优化
- 由物理引擎和运动规划器使用

有关模型特定的详细信息，请参见 [Supported Robot Models](../1-intro/2-robot-models/README.md).