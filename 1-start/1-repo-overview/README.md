# 레포지토리 개요

HD현대로보틱스 ROS2 드라이버는 로봇 제어, 시뮬레이션 및 모션 플래닝 기능을 제공하기 위해 함께 작동하는 여러 상호 연결된 패키지로 구성됩니다.

## 레포지토리 아키텍처

```
HD Hyundai Robotics ROS2 Driver

hdr_ros2_driver 
   hdr_ros2_driver          # 핵심 통신 드라이버
   hdr_hardware_interface   # ros2_control 통합
   hdr_moveit_config       # MoveIt 모션 플래닝 구성
   hdr_msgs                # 커스텀 메시지 정의

hdr_client_driver        # C++ 클라이언트 라이브러리  
hdr_description         # 로봇 URDF 모델 및 메쉬
hdr_simulation_gz       # Gazebo 시뮬레이션
```

## 레포지토리 내 패키지 세부사항

### 핵심 패키지

- **[ROS2 드라이버 (`hdr_ros2_driver`)](../../2-hdr_ros2_driver/README.md)**: 로봇 제어, 파일 관리, I/O 작업 및 시스템 모니터링을 위한 서비스를 제공하는 기본 ROS2 노드

- **[HDR 클라이언트 드라이버 (`hdr_client_driver`)](../../6-hdr_client_driver/README.md)**: Hi6 제어기와 TCP/UDP 통신 프로토콜을 구현하는 C++ 라이브러리

- **[ROS2 제어 통합 (`hdr_hardware_interface`)](../../3-hdr_hardware_interface/README.md)**: 표준 ROS2 제어 프레임워크와의 통합을 가능하게 하는 ros2_control SystemInterface

### 모델 및 구성 패키지

- **[로봇 설명 (`hdr_description`)](../../4-hdr_description/README.md)**: 모든 지원되는 로봇 모델에 대한 URDF/XACRO 로봇 설명, 충돌/시각적 메쉬 및 RViz 구성

- **[MoveIt2 구성 (`hdr_moveit_config`)](../../5-hdr_moveit_config/README.md)**: SRDF, soft limits, 기구학 및 모션 플래닝 설정을 포함한 모델별 MoveIt2 구성

### 시뮬레이션 및 HD현대로보틱스 커스텀 메시지

- **[Gazebo 시뮬레이션 (`hdr_simulation_gz`)](../../6-hdr_simulation_gz/README.md)**: 시뮬레이션 환경 연동을 제공하는 Gazebo Ignition 통합

- **[커스텀 메시지 (`hdr_msgs`)](../../7-hdr_msgs/README.md)**: 제어기와의 통신을 위한 커스텀 ROS2 서비스 및 메시지 정의


## 다음 단계

1. 위에 링크된 개별 패키지 문서를 검토하십시오.
2. [설치](../2-installation/README.md)로 진행하여 패키지를 빌드하십시오.
3. [초기 설정](../3-initial-setup/README.md)에서 로봇 연결을 구성하십시오.