# 5. Robot URDF (`hdr_description`)

The `hdr_description` package contains robot URDF, meshes, and visualization configurations for HD Hyundai Robotics robots in ROS2. This package provides essential URDF/XACRO definitions needed for simulation, visualization, and motion planning.

### Key Features

- **Robot Model-Specific URDF**: URDF/XACRO files for all supported robot models
- **3D Meshes**: Collision and visual meshes for accurate simulation
- **RViz Integration**: Pre-configured visualization settings
- **ros2_control Integration**: Joint interface definitions

### Package Structure

| Directory | Contents | Purpose |
|-----------|----------|----------|
| `urdf/` | Robot URDF files | URDF/XACRO definitions |
| `meshes/` | 3D model mesh files | Collision and visual representation |
| `launch/` | Visualization launch files | RViz display configuration |
| `rviz/` | RViz configuration files | Display settings and plugins |

### URDF Configuration

#### Main Files
- **`hdr.urdf.xacro`**: Top-level macro including all components
- **`hdr.ros2_control.xacro`**: ros2_control hardware interface macro

#### Robot-Specific Files
Each robot model has its own directory under `urdf/robots/`:
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
| `robot_model` | string | `ha006b` | Robot model to display |
| `description_package` | string | `hdr_description` | Package containing URDF files |
| `description_file` | string | `hdr.urdf.xacro` | Main URDF/XACRO file |

### Mesh Quality

The package provides two types of meshes for each robot:

#### Visual Meshes
- High-resolution meshes for realistic visualization
- Detailed surface textures and materials
- Used for visual representation in RViz and Gazebo

#### Collision Meshes
- Simplified meshes for collision detection
- Optimized for computational efficiency
- Used by physics engines and motion planners

For model-specific details, see [Supported Robot Models](../1-intro/2-robot-models/README.md).
