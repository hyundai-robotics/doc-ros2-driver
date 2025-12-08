# MoveIt2 Configuration (`hdr_moveit_config`)

The `hdr_moveit_config` package provides MoveIt2 configuration packages for controlling HD Hyundai Robotics robots in both real and simulation environments. This package includes robot-specific motion planning configurations with SRDF definitions, joint limits, and controller settings.

## Key Features

- **Robot-Specific Configuration**: Individual MoveIt2 settings for each supported robot model
- **SRDF Definitions**: Semantic robot description with planning groups and poses
- **Joint Limits Management**: Velocity and acceleration scaling for safe operation
- **Kinematics Integration**: Forward/inverse kinematics solver configuration
- **Controller Integration**: ros2_control and trajectory execution setup

## Package Organization

Each robot model has its own MoveIt2 configuration package:

- `ha006b_moveit_config/`
- `hdf7_9_moveit_config/`
- `hdf8_8_moveit_config/`
- `hdr10l_19_moveit_config/`
- `hdr20_17_moveit_config/`
- `hdr50_22_moveit_config/`
- `hdr220_26_moveit_config/`
- `hh020_moveit_config/`
- `hdr35_20_moveit_config/`

## Configuration Files

Each robot configuration includes:

### Core Configuration
- **SRDF Files**: Semantic robot description with planning groups
- **joint_limits.yaml**: Velocity and acceleration limits with scaling factors
- **kinematics.yaml**: Kinematics solver plugin configuration
- **controllers.yaml**: ros2_control trajectory controller settings

### Advanced Settings
- **ompl_planning.yaml**: OMPL motion planner configuration
- **pilz_cartesian_limits.yaml**: Cartesian motion limits for Pilz planner
- **sensors_3d.yaml**: 3D sensor integration (if applicable)
- **initial_positions.yaml**: Default starting poses

## Safety Considerations

### Velocity Scaling
**≤ 0.5** scaling factors are recommended for stable operation:

```yaml
default_velocity_scaling_factor: 0.5
default_acceleration_scaling_factor: 0.5
```

### Joint Limits
The `joint_limits.yaml` file defines:
- Maximum joint velocities
- Maximum joint accelerations
- Software position limits
- Scaling factors for motion planning

## Launch

```bash
ros2 launch hdr_bringup hdr_moveit.launch.py robot_model:=ha006b
```

![hdr_moveit](../_assets/hdr_moveit.png)

## Planning Groups

Typical SRDF planning group configuration:

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


## Customization

To modify motion planning behavior:
1. Edit `joint_limits.yaml` for velocity/acceleration limits (cannot exceed maximum velocities defined per joint in URDF)
2. Modify `ompl_planning.yaml` for planner-specific settings
3. Update SRDF for new planning groups or poses
4. Adjust controller parameters in `controllers.yaml`