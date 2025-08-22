# 네트워크 테스트

본 가이드는 ROS2 작업을 위한 안정적인 통신을 보장하기 위해 개발 PC와 HD현대로보틱스 로봇 제어기 간의 네트워크 연결 테스트를 다룹니다.

## 테스트 개요
네트워크 테스트는 다음 순서로 수행해야 합니다:

1. **네트워크 계층 테스트** - IP 연결성 및 라우팅
2. **애플리케이션 계층 테스트** - OpenAPI 통신
3. **ROS2 통신 테스트** - ROS2 드라이버 통신

## 네트워크 계층 테스트

### 기본 연결성 테스트

```bash
# 로봇 제어기에 대한 기본 IP 연결성 테스트
ping -c 5 192.168.1.150

# 예상 출력:
# 5 packets transmitted, 5 received, 0% packet loss
# rtt min/avg/max/mdev = X.X/X.X/X.X/X.X ms
```

## 애플리케이션 계층 테스트

### API 응답 테스트

```bash
# 버전 엔드포인트 테스트
curl -X GET \
  -H "Content-Type: application/json" \
  http://192.168.1.150:8888/api/version

# 예상 응답 (예시):
# {
#   "api_version": "1.0",
#   "system_version": "60.34-00",
#   "status": "ok"
# }
```

## ROS2 통신 테스트

### HDR 드라이버 실행

```bash
# 통신 테스트를 위한 ROS2 드라이버 실행
ros2 launch hdr_ros2_driver hdr_ros2_driver_launch.py \
  openapi_ip:=192.168.1.150 \
  openapi_port:=8888
```

### ROS2 서비스 테스트

```bash
ros2 service list | grep hdr_ros2_driver

# 버전 서비스 테스트
ros2 service call /hdr_ros2_driver/version/get/api_ver std_srvs/srv/Trigger

# 모터 상태 서비스 테스트  
ros2 service call /hdr_ros2_driver/robot/get/motor_state std_srvs/srv/Trigger
```

### 토픽 모니터링

```bash
# 조인트 상태 모니터링
ros2 topic echo /joint_states --once
```

## 문제 해결

### 일반적인 문제 및 해결책

#### Ping 실패

**증상**: `ping: sendmsg: Operation not permitted` 또는 응답 없음

**해결책**:
```bash
# 네트워크 구성 확인
ip addr show
ip route show

# 인터페이스가 활성 상태인지 확인
sudo ip link set eth0 up

# 방화벽 규칙 확인
sudo ufw status
sudo iptables -L
```

#### 포트 닫힘

**증상**: 연결 거부됨, 포트가 닫힌 것으로 표시

**해결책**:
- 로봇 제어기의 전원이 켜져 있는지 확인
- 제어기가 REMOTE 모드에 있는지 확인
- 올바른 포트 번호 확인 (기본값: 8888)

#### ROS2 서비스 실패

**증상**: 서비스 사용 불가, 호출 타임아웃

**해결책**:
```bash
# ROS2 환경 확인
echo $ROS_DISTRO
ros2 --help

# HDR 패키지 확인
ros2 pkg list | grep hdr

# 디버그 출력과 함께 드라이버 재시작
ros2 launch hdr_ros2_driver hdr_ros2_driver_launch.py --ros-args --log-level DEBUG
```

## 다음 단계

네트워크 테스트 후 [설치 검증](../4-verifying/README.md)을 수행하십시오.