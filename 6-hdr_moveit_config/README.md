# 6. MoveIt2 配置 (`hdr_moveit_config`)

`hdr_moveit_config` 包提供用于控制 HD Hyundai Robotics 机器人在实际和仿真环境中的 MoveIt2 配置包。该包包含特定于机器人的运动规划配置，具有 SRDF 定义、关节限制和控制器设置。

### 主要特性

- **特定于机器人的配置**：每个支持的机器人模型的单独 MoveIt2 设置
- **SRDF 定义**：带有规划组和姿态的语义机器人描述
- **关节限制管理**：安全操作的速度和加速度缩放
- **运动学集成**：正/反运动学求解器配置
- **控制器集成**：ros2_control 和轨迹执行设置

### 包组织

每个机器人模型都有自己独立的 MoveIt2 配置包：

- `ha006b_moveit_config/`
- `hdf7_9_moveit_config/`
- `hdf8_8_moveit_config/`
- `hdr10l_19_moveit_config/`
- `hdr20_17_moveit_config/`
- `hdr50_22_moveit_config/`
- `hdr220_26_moveit_config/`
- `hh020_moveit_config/`
- `hdr35_20_moveit_config/`

### 配置文件

每个机器人配置包括：

#### 核心配置
- **SRDF 文件**：带有规划组的语义机器人描述
- **joint_limits.yaml**：带有缩放因子的速度和加速度限制
- **kinematics.yaml**：运动学求解器插件配置
- **controllers.yaml**：ros2_control 轨迹控制器设置

#### 高级设置
- **ompl_planning.yaml**：OMPL 运动规划器配置
- **pilz_cartesian_limits.yaml**：Pilz 规划器的笛卡尔运动限制
- **sensors_3d.yaml**：3D 传感器集成（如适用）
- **initial_positions.yaml**：默认起始姿态

### 安全注意事项

#### 速度缩放
**≤ 0.5** 的缩放因子推荐用于稳定操作：

```yaml
default_velocity_scaling_factor: 0.5
default_acceleration_scaling_factor: 0.5
```

#### 关节限制
`joint_limits.yaml` 文件定义：
- 最大关节速度
- 最大关节加速度
- 软件位置限制
- 运动规划的缩放因子

### 启动

```bash
ros2 launch hdr_bringup hdr_moveit.launch.py robot_model:=ha006b
```

![](../_assets/hdr_moveit.png)

### 规划组

典型的 SRDF 规划组配置：

```xml
<group name="manipulator">
    <chain base_link="base_link" tip_link="link6"/>
</group>

<group_state name="home" group="manipulator">
    <joint name="j1" value="0"/>
    <joint name="j2" value="0"/>
    <joint name="j3" value="0"/>
    <joint name="j4" value="0"/>
    <joint name="j5" value="0"/>
    <joint name="j6" value="0"/>
</group_state>
```


### 定制

要修改运动规划行为：
1. 编辑 `joint_limits.yaml` 以设置速度/加速度限制（不能超过 URDF 中每个关节定义的最大速度）
2. 修改 `ompl_planning.yaml` 以设置特定于规划器的参数
3. 更新 SRDF 以添加新的规划组或姿态
4. 在 `controllers.yaml` 中调整控制器参数