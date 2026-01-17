# 버전 정보 서비스

## 개요

`hdr_ros2_driver`에서 제공하는 버전 정보 관련 ROS2 서비스입니다.

## 버전 정보 서비스

### 시스템 버전 조회

```bash
# API 버전 조회
ros2 service call /hdr_ros2_driver/get/api_ver std_srvs/srv/Trigger

# 시스템 버전 조회
ros2 service call /hdr_ros2_driver/get/system_ver std_srvs/srv/Trigger
```