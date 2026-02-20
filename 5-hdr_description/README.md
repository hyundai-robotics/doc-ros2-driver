# 5. 机器人 URDF (`hdr_description`)

`hdr_description` 包含了 ROS2 中 HD 现代机器人机器人的机器人 URDF、网格和可视化配置。该软件包提供了模拟、可视化和运动规划所需的基本 URDF/XACRO 定义。

### 主要特性

- **特定机器人模型的 URDF**：所有支持的机器人模型的 URDF/XACRO 文件
- **3D 网格**：用于准确模拟的碰撞和视觉网格
- **RViz 集成**：预配置的可视化设置
- **ros2_control 集成**：关节接口定义

### 包结构

| 目录      | 内容                     | 目的                   |
|-----------|-------------------------|------------------------|
| `urdf/`   | 机器人 URDF 文件        | URDF/XACRO 定义       |
| `meshes/` | 3D 模型网格文件         | 碰撞和视觉表示       |
| `launch/` | 可视化启动文件          | RViz 显示配置          |
| `rviz/`   | RViz 配置文件           | 显示设置和插件        |

### URDF 配置

#### 主要文件
- **`hdr.urdf.xacro`**：包含所有组件的顶级宏
- **`hdr.ros2_control.xacro`**：ros2_control 硬件接口宏

#### 机器人特定文件
每个机器人模型在 `urdf/robots/` 下有自己的目录：
- `ha006b.urdf.xacro`
- `hdf7_9.urdf.xacro`
- `hdf8_8.urdf.xacro`
- `hdr10l_19.urdf.xacro`
- `hdr20_17.urdf.xacro`
- `hdr50_22.urdf.xacro`
- `hdr220_26.urdf.xacro`
- `hh020.urdf.xacro`
- `hdr35_20.urdf.xacro`

### 使用示例

#### 在 RViz 中可视化
```bash
ros2 launch hdr_description display_robot.launch.py robot_model:=ha006b
```

#### 启动参数

| 参数         | 类型    | 默认      | 描述                |
|--------------|---------|-----------|---------------------|
| `robot_model`| string  | `ha006b`  | 要显示的机器人模型 |
| `description_package` | string | `hdr_description` | 包含URDF文件的包 |
| `description_file` | string | `hdr.urdf.xacro` | 主URDF/XACRO文件 |

### 网格质量

该包为每个机器人提供两种类型的网格：

#### 视觉网格
- 高分辨率网格以实现真实的可视化
- 细致的表面纹理和材料
- 用于RViz和Gazebo中的视觉表示

#### 碰撞网格
- 简化的网格用于碰撞检测
- 针对计算效率进行了优化
- 被物理引擎和运动规划器使用

有关特定模型的详细信息，请参见 [支持的机器人模型](../0-intro/2-robot-models/README.md)。