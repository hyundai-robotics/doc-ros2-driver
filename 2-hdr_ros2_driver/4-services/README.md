# ROS2 드라이버 서비스

## 개요

`hdr_ros2_driver`는 HD현대로보틱스 Hi6 제어기와 통신하기 위한 다양한 ROS2 서비스를 제공합니다. 

## 서비스 범주

| 범주 | 설명 |
|------|------|
| **[제어 서비스](1-control/README.md)** | 로봇 제어, 모터 전원, 비상정지, 좌표계, I/O 관리 |
| **[작업 관리](2-task/README.md)** | 변수 할당, 동작 실행, 프로그램 제어 |
| **[파일 관리](3-file/README.md)** | 파일 업로드/다운로드, 디렉토리 조작 |
| **[PLC 통신](4-plc/README.md)** | PLC 릴레이 값 제어 |
| **[콘솔 명령](5-console/README.md)** | 콘솔 명령 실행, 시스템 시간, 로그 관리 |
| **[프로젝트 관리](6-project/README.md)** | 작업 정보, 작업 삭제/재로드 |
| **[버전 정보](7-version/README.md)** | API 버전, 시스템 버전 조회 |

## 기본 사용법

### 서비스 목록 확인
```bash
# 모든 HDR 드라이버 서비스 목록
ros2 service list | grep hdr_ros2_driver
```

### 일반적인 서비스 호출
```bash
# API 버전 확인
ros2 service call /hdr_ros2_driver/get/api_ver std_srvs/srv/Trigger

# 모터 상태 확인
ros2 service call /hdr_ros2_driver/robot/get/motor_state std_srvs/srv/Trigger

# 모터 전원 켜기
ros2 service call /hdr_ros2_driver/robot/post/motor_power std_srvs/srv/Trigger
```