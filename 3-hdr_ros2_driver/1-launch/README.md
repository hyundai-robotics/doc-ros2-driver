# 3.1 HDR ROS2 드라이버 launch

이 섹션에서는 HDR ROS2 드라이버를 실행하는 방법을 다룹니다.

### 기본 실행

#### HDR ROS2 드라이버 실행
```bash
# 기본 매개변수 실행
ros2 launch hdr_ros2_driver hdr_ros2_driver_launch.py
```

다음과 같이 드라이버를 시작합니다:
- 기본 IP: 192.168.1.150
- 기본 포트: 8888

### 확인

실행 후, 드라이버가 실행 중인지 확인하십시오:

```bash
# 드라이버 노드가 활성화되었는지 확인
ros2 node list | grep hdr_ros2_driver

# 사용 가능한 서비스 나열
ros2 service list | grep hdr_ros2_driver

# 기본 연결 테스트
ros2 service call /hdr_ros2_driver/get/api_ver std_srvs/srv/Trigger
```

### 네트워크 설정 전제조건

실행하기 전에 적절한 네트워크 구성을 확인하십시오:

1. **이더넷 연결**: LAN1, LAN2 또는 LAN3을 통해 PC를 로봇 제어기에 연결
2. **제어기 IP**: 기본값 192.168.1.150 (티칭 펜던트를 통해 구성 가능)  
3. **PC IP**: 192.168.1.x 범위로 설정 (x ≠ 150)
4. **REMOTE 모드**: 로봇 제어기가 REMOTE 모드에 있는지 확인

### 문제 해결

#### 일반적인 문제

1. **연결 시간 초과**
   - 로봇 IP 및 포트 확인: `ping 192.168.1.150`
   - 이더넷 케이블 연결 확인

2. **서비스 사용 불가**
   - 드라이버가 성공적으로 실행되었는지 확인
   - ROS2 환경이 소스되었는지 확인
   - 실행 출력에서 오류 메시지 확인
   - 로봇이 REMOTE 모드에 있는지 확인
   - 제어기 SW 버전이 **70.00-00** 이상인지 확인
   