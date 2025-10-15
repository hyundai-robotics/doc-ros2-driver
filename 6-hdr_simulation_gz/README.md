# Gazebo Simulation (`hdr_simulation_gz`)

The `hdr_simulation_gz` package provides a ROS2 + Gazebo (Ignition) simulation environment for HD Hyundai Robotics industrial robots. This package enables development, testing, and validation of robotic applications without physical hardware.

## Key Features

- **Gazebo Integration**: Ignition Gazebo simulation support
- **Physics Simulation**: Realistic robot dynamics and collision detection
- **MoveIt2 Compatibility**: Motion planning in simulation environment
- **ros2_control Integration**: Uses `gz_ros2_control/GazeboSimSystem` plugin

## Package Structure

| Directory | Contents | Purpose |
|-----------|----------|----------|
| `launch/` | Simulation launch files | Robot spawning and controller setup |
| `config/` | Controller configuration files | ros2_control YAML files |

## Launch Files

### Robot Spawning
```bash
# Spawn robot with ros2_control in Gazebo
ros2 launch hdr_simulation_gz hdr_gz_spawn.launch.py robot_model:=ha006b
```

### MoveIt2 Integration
```bash
# Run simulation with MoveIt2 motion planning
ros2 launch hdr_simulation_gz hdr_gz_moveit.launch.py robot_model:=hdr50_22
```

## Configuration Options

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `robot_model` | string | `ha006b` | Robot model to simulate |
| `use_sim` | bool | `true` | Enable Gazebo simulation mode |
| `runtime_config_package` | string | `hdr_simulation_gz` | Controller configuration package |
| `controllers_file` | string | `hdr_controllers.yaml` | Controller configuration file |
| `description_package` | string | `hdr_description` | URDF package name |
| `description_file` | string | `hdr.urdf.xacro` | Robot description file |
| `initial_positions_file` | string | `initial_positions.yaml` | Initial joint positions |
| `kinematics_file` | string | `kinematics.yaml` | Kinematics solver configuration |


## Future Improvements
- Sensor and tool simulation support
- World and example scenario support