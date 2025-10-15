# Controller and PC Communication Setup

This guide covers the configuration of network interfaces on your development PC for communication with HD Hyundai Robotics robot controllers.

## Prerequisites
⚠️ Please verify the following before starting setup:
- **Robot Controller SW Version**: Hi6 series controller with SW version **60.34-00** or higher

## Network Configuration Overview

The PC must be configured to communicate with the robot controller via Ethernet. The default configuration uses a 192.168.1.x subnet with the controller at 192.168.1.150.

## Default Network Configuration (Using LAN1)

| Component | Parameter | Default Value |
|-----------|-----------|---------------|
| **PC IP Address** | Static IP | 192.168.1.x (user configured)|
| **Robot Controller IP** | Static IP | 192.168.1.150 |
| **Subnet Mask** | Network Mask | 255.255.255.0 |
| **Gateway** | Default Gateway | 192.168.1.1  |

## Cable Connection

![controller](../../_assets/controller.png)

1. **Locate Robot Controller Ethernet Port**
   - **Hi6-N Controller**: Ethernet port on top of main module
   - **Hi6-T Controller**: Ethernet port on controller front panel

2. **Connect Ethernet Cable**
   - Use Cat5e or Cat6 Ethernet cable
   - **Recommendation**: Use LAN1 (typically pre-configured to 192.168.1.x)
   - LAN2, LAN3 ports are also available with different default controller IPs: </br>
      LAN2: 192.168.4.150 → PC needs to be configured to 192.168.4.x range </br>
      LAN3: 192.168.3.150 → PC needs to be configured to 192.168.3.x range

3. **Verify Physical Connection**
   - Ensure cable connection is secure
   - Check network port LED indicators (if available)


## PC Network Interface Configuration

![LAN_com](../../_assets/LAN_com.png)

### Using Network Manager GUI

#### Ubuntu Desktop (GNOME)

1. **Open Network Settings**
   - Click on the network icon in the top-right corner
   - Select "Wired Settings" or go to Settings → Network

2. **Configure Wired Connection**
   - Click the gear icon next to the wired connection
   - Navigate to the "IPv4" tab

3. **Set Static IP Configuration (Using LAN1)**
   - **Method**: Manual
   - **Address**: 192.168.1.100
   - **Netmask**: 255.255.255.0
   - **Gateway**: 192.168.1.1

4. **Apply Settings**
   - Click "Apply" and disconnect then reconnect the network interface

![ip_setup](../../_assets/ip_setup.png)

## Verification

### Verify Network Configuration

```bash
# Test network connectivity
ping -c 4 192.168.1.150
```

![ping_test](../../_assets/ping_test.png)