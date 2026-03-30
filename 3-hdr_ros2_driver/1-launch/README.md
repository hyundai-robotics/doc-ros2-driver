# 3.1 HDR ROS2 Driver launch

This section covers how to launch the HDR ROS2 driver.

### Basic Launch

#### HDR ROS2 Driver Launch
```bash
# Launch with default parameters
ros2 launch hdr_ros2_driver hdr_ros2_driver_launch.py
```

This will start the driver with:
- Default IP: 192.168.1.150
- Default Port: 8888

### Custom Configuration

#### Custom IP and Port
```bash
# Launch with custom network settings
ros2 launch hdr_ros2_driver hdr_ros2_driver_launch.py \
  openapi_ip:=192.168.0.10 \
  openapi_port:=8080
```

### Launch Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `openapi_ip` | string | `192.168.1.150` | Robot controller server IP address |
| `openapi_port` | int | `8888` | Controller server port number |
| `robot_model` | string | `ha006b` | Robot model name |

### Verification

After launch, verify the driver is running:

```bash
# Check if driver node is active
ros2 node list | grep hdr_ros2_driver

# List available services
ros2 service list | grep hdr_ros2_driver

# Test basic connection
ros2 service call /hdr_ros2_driver/get/api_ver std_srvs/srv/Trigger
```

### Network Setup Prerequisites

Before launching, ensure proper network configuration:

1. **Ethernet Connection**: Connect PC to robot controller via LAN1, LAN2, or LAN3
2. **Controller IP**: Default 192.168.1.150 (configurable through teaching pendant)
3. **PC IP**: Set to 192.168.1.x range (x ≠ 150)
4. **REMOTE Mode**: Ensure robot controller is in REMOTE mode

### Troubleshooting

#### Common Issues

1. **Connection Timeout**
   - Verify robot IP and port: `ping 192.168.1.150`
   - Check ethernet cable connection

2. **Service Unavailable**
   - Verify driver launched successfully
   - Check ROS2 environment is sourced
   - Check launch output for error messages
   - Ensure robot is in REMOTE mode
   - Verify controller SW version is **70.00-00** or higher
   