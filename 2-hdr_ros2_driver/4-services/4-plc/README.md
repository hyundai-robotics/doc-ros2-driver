# PLC 통신 서비스

## 개요

`hdr_ros2_driver`에서 제공하는 PLC 통신 관련 ROS2 서비스입니다.

## PLC 통신 서비스

### 릴레이 값 제어

```bash
# 릴레이 값 가져오기
ros2 service call /hdr_ros2_driver/plc/get/relay_value hdr_msgs/srv/IoplcGet "{name: 'M', st: 100, len: 10}"

# 릴레이 값 설정
ros2 service call /hdr_ros2_driver/plc/post/relay_value hdr_msgs/srv/IoplcPost "{name: 'fb1.do0', value: 1}"
```