
[__SOURCE](README.md)
# Hi6 & Hi7 제어기 기능설명서 - ROS2 드라이버

현재 ROS2 호환 제어기는 Hi6 시리즈이며, 제어기 소프트웨어 버전 **v60.34-00** 이상에서 지원됩니다. </br>
**v60.34-00** 버전은 2026년 2Q 중 공식 릴리스가 예정되어 있으므로, 정식 릴리스 이전에는 HD현대로보틱스 ROS2 드라이버 사용을 지양하시기 바랍니다. </br>
⚠️ **Hi7 모델의 경우 출시 예정이며, 상세 지원 일정은 아직 확정되지 않았습니다. 정식 릴리즈 일정이 수립되는 대로 공지를 통해 안내해 드릴 예정이오니 참고하시기 바랍니다.**

[__SOURCE](0-precautions.md)
# 사전 주의사항

{% include url="https://hrcontentsrelay-bmgae5hdbzapc4bc.koreacentral-01.azurewebsites.net/api/proxy?path=doc-common-pages/ko/precautions.md" %}

[__SOURCE](1-intro/README.md)
# 1. 개요

본 매뉴얼에서는 HD현대로보틱스 (HDR) ROS2 드라이버에 대한 설명을 제공합니다.

HDR ROS2 드라이버는 HD현대로보틱스 산업용 로봇 제어기(Hi6, Hi7 시리즈)와 ROS2 시스템을 연동하여 시뮬레이션 환경 및 실제 로봇 제어 기능을 모두 지원합니다.

![hdr_main](../_assets/0_hdr_main.png)


### 사전 확인 사항
HDR ROS2 드라이버 사용에 앞서 아래 항목을 반드시 확인하시기 바랍니다.
- [지원 제어기](1-controller-models/README.md) - 호환 가능한 Hi6, Hi7 시리즈 제어기
- [지원 로봇 모델](2-robot-models/README.md) - 호환 가능한 HD현대로보틱스 로봇 모델
- [시스템 요구사항](3-requirements/README.md) - 하드웨어 및 소프트웨어 요구사항
- [ROS2 버전](4-ros2-version/README.md) - 지원 ROS2 버전
- [로봇 joint, link 명](5-hdr-robot/README.md) - ROS2 내 로봇 joint 및 link 명칭

### 설치 및 초기 설정
위 항목을 모두 확인한 후 문제가 없다면 아래 절차에 따라 ROS2 드라이버 설치 및 초기 설정을 진행하시기 바랍니다.
- [레포지토리 개요](1-repo-overview/README.md) - HDR ROS2 드라이버 레포지토리 구조 및 아키텍처 확인
- [패키지 설치](2-installation/README.md) - HDR ROS2 드라이버 빌드 및 설치 방법
- [제어기 및 PC 설정](3-initial-setup/README.md) - HDR ROS2 드라이버 사용을 위한 초기 설정 방법
- [설치 검증](4-verifying/README.md) - 설치 및 설정이 올바르게 완료되었는지 확인

### ROS2 드라이버 바로 실행하기
위의 설치 및 초기 설정 과정을 모두 마쳤다면, 아래 절차를 통해 HDR ROS2 드라이버를 실행하고 로봇 제어를 시작할 수 있습니다.

- [ROS2 드라이버 실행](8-running/README.md) - ROS2 드라이버 실행 및 로봇 제어 방법

⚠️ **반드시 사전 확인 사항을 확인하고 설치 및 초기 설정을 모두 완료한 뒤 진행하시기 바랍니다.** 

⚠️ **현재 HD현대로보틱스 ROS2 드라이버는 제어기 소프트웨어 버전 *v60.34-00* 이상에서 지원됩니다. </br> *v60.34-00* 버전은 2026년 2Q 중 공식 릴리스가 예정되어 있으므로, 정식 릴리스 이전에는 ROS2 드라이버 사용을 지양하시기 바랍니다.**


[__SOURCE](1-intro/1-controller-models/README.md)
# 1.1 지원 제어기 모델
ROS2 기능을 공식적으로 지원하는 HD현대로보틱스 Hi6 제어기 모델은 아래와 같습니다.

- Hi6-N10
- Hi6-N20
- Hi6-N00(HK)
- Hi6-N00-60(HK)
- Hi6-N30(HK)
- Hi6-N80(HK)
- Hi6-T15

**제어기 요구사항**:
- SW 버전 버전: **60.32-00** 이상
- 동작 모드: **REMOTE 모드**

Hi7 제어기 시리즈의 경우, 향후 모델 라인업 및 지원 일정이 확정되는 대로 본 목록에 업데이트할 예정입니다.

> ⚠️ **참고:** HD현대로보틱스 ROS2 드라이버는 **Hi5** 제어기 시리즈를 **지원하지 않습니다**.

### 다음 단계

제어기 호환성을 확인한 후, [지원 로봇 모델](../2-robot-models/README.md)을 확인하여 귀하의 로봇이 지원되는지 확인하십시오.

[__SOURCE](1-intro/2-robot-models/README.md)
# 1.2 지원 로봇 모델

현재 HD현대로보틱스 드라이버에서 공식적으로 지원하는 로봇 모델은 다음와 같습니다.

- ha006b
- hdf7_9
- hdf8_8
- hdr10l_19
- hdr20_17
- hdr50_22
- hdr220_26
- hh020  
- hdr35_20

### 모델명 변경사항

> ❗ **참고:** 로봇 모델 `hdf7_9`, `hdf8_8`, `hdr20_17`, `hdr50_22`, `hdr220_26`, `hdr35_20`은 각각 모델 `HH7`, `HH8`, `UH020`, `HH050`, `HS220`, `UH035`의 변경된 이름입니다.

### 각 모델에 포함된 내용

지원되는 각 로봇 모델에는 다음이 포함됩니다:

- **URDF**: 충돌 메쉬가 포함된 로봇 URDF
- **Mesh**: 시각화를 위한 3D 모델
- **MoveIt2 구성**: 모델 별 soft limit가 포함된 모션 플래닝 설정
- **Gazebo 지원**: 시뮬레이션 통합 지원

### 다음 단계

로봇 모델을 확인한 후, [시스템 요구사항](../3-requirements/README.md)으로 진행하여 시스템이 올바르게 구성되었는지 확인하십시오.

[__SOURCE](1-intro/3-requirements/README.md)
# 1.3 시스템 요구사항

본 페이지에서는 HD현대로보틱스 ROS2 드라이버를 실행하기 위한 하드웨어 및 소프트웨어 요구사항을 설명합니다.

### 하드웨어 요구사항

#### 로봇 제어기
- **호환 제어기**: Hi6-N10, Hi6-N20, Hi6-N00(HK), Hi6-N00-60(HK), Hi6-N30(HK), Hi6-N80(HK), Hi6-T15
- **제어기 SW 버전 버전**: **60.32-00** 이상
- **동작 모드**: 로봇이 **REMOTE** 모드로 설정되어야 함
- **네트워크 인터페이스**: 이더넷 연결 (LAN1, LAN2 또는 LAN3)

#### 개발 PC
- **운영체제**: Ubuntu 22.04 LTS 또는 Ubuntu 24.04 LTS
- **메모리**: 최소 8GB RAM (시뮬레이션용으로는 16GB 권장)
- **네트워크**: 로봇 통신을 위한 이더넷 인터페이스
- **CPU**: 멀티코어 프로세서 (4코어 이상 권장)


### 다음 단계

시스템이 모든 요구사항을 충족하면 [지원 ROS2 버전](../4-ros2-version/README.md)을 확인하세요.

[__SOURCE](1-intro/4-ros2-version/README.md)
# 1.4 지원 ROS2 버전

HD현대로보틱스 ROS2 드라이버는 로봇 제어기 및 시뮬레이션 환경에서 테스트되고 검증된 특정 ROS2 배포판을 지원합니다.

### 지원되는 ROS2 배포판

- **ROS2 Humble Hawksbill** (Ubuntu 22.04 LTS)
- **ROS2 Jazzy Jalisco** (Ubuntu 24.04 LTS)

### 버전 확인

설치 후 ROS2 설정을 확인하십시오:

```bash
# ROS2 환경 소스
source /opt/ros/$ROS_DISTRO/setup.bash

# ROS2 버전 확인
ros2 doctor
```

### 다음 단계

ROS2 호환성을 확인한 후 설치를 위해 [시작하기](../../1-start/README.md)로 진행하세요.

[__SOURCE](1-intro/5-hdr-robot/README.md)
# 1.5 로봇 joint 및 link 명칭

HD현대로보틱스 로봇은 URDF 내에서 아래와 같은 joint 및 link 명칭을 따릅니다.


### Joint 명

|joint no|joint name </br>(URDF)|joint name </br>(TP)|
|:------:|:---:|:---:|
|1|j1|S|
|2|j2|H|
|3|j3|V|
|4|j4|R2|
|5|j5|B|
|6|j6|R1|


### Link 명

|link No|link Name|
|:------:|:---:|
|0|base_link|
|1|lower_frame_link|
|2|upper_frame_link|
|3|arm_link|
|4|wrist_body_link|
|5|wrist_holder_link|
|6|flange_link|


### Link 간 관계

|link No|link Name|joint|parent link|joint type|note|
|:------:|:---:|:---:|:------:|:---:|:---:|
||world||||||
|0|base_link|world_joint|world|fixed|||
|1|lower_frame_link|j1|base_link|revolute||
|2|upper_frame_link|j2|lower_frame_link|revolute||
|3|arm_link|j3|upper_frame_link|revolute||
|4|wrist_body_link|j4|arm_link|revolute||
|5|wrist_holder_link|j5|wrist_body_link|revolute||
|6|flange_link|j6|wrist_holder_link|revolute||
||flange|flange_link-flange|flange_link|fixed|ROS-Industrial 표준 좌표계|
||tool0|flange-tool0|flange|fixed|ROS-Industrial 표준 좌표계|

[__SOURCE](2-start/README.md)
# 2. 시작하기

본 섹션에서는 HD현대로보틱스 ROS2 드라이버의 설치, 구성 및 실행을 위한 단계별 지침을 제공합니다. 이 가이드를 따라 개발 환경을 설정하고 로봇과의 통신을 구축하세요.

### 설치 및 설정 과정

1. [레포지토리 개요](1-repo-overview/README.md) - 패키지 구조와 관계 이해
2. [설치](2-installation/README.md) - 레포지토리 클론 및 빌드
3. [초기 설정](3-initial-setup/README.md) - 네트워킹 설정 구성
4. [설정 검증](4-verifying/README.md) - 설치 테스트

[__SOURCE](2-start/1-repo-overview/README.md)
# 2.1 레포지토리 개요

HD현대로보틱스 ROS2 드라이버는 로봇 제어, 시뮬레이션 및 모션 플래닝 기능을 제공하기 위해 함께 작동하는 여러 상호 연결된 패키지로 구성됩니다.

### 레포지토리 아키텍처

```
HD Hyundai Robotics ROS2 Driver

hdr_ros2_driver            # 상위 레포지토리
   hdr_bringup             # 로봇 연동 및 제어 launch 파일
   hdr_ros2_driver         # 핵심 통신 드라이버
   hdr_hardware_interface  # ros2_control 통합
   hdr_moveit_config       # MoveIt configuration
   hdr_msgs                # HD로보틱스 커스텀 메시지 정의

hdr_client_driver          # C++ 클라이언트 라이브러리

hdr_description            # 로봇 URDF 모델 및 mesh

hdr_simulation_gz          # Gazebo 시뮬레이션 연동
```

### 레포지토리 내 패키지 세부사항

- **[ROS2 드라이버 (`hdr_ros2_driver`)](../../2-hdr_ros2_driver/README.md)** </br>
로봇 제어, 파일 관리, I/O 작업 및 시스템 모니터링을 위한 서비스를 제공하는 기본 ROS2 노드

- **[HDR 클라이언트 드라이버 (`hdr_client_driver`)](../../6-hdr_client_driver/README.md)** </br>
HD현대로보틱스 제어기와 TCP/UDP 통신 프로토콜을 구현하는 C++ 라이브러리

- **[ROS2 제어 통합 (`hdr_hardware_interface`)](../../3-hdr_hardware_interface/README.md)** </br>
표준 ROS2 제어 프레임워크와의 통합을 위한 ros2_control SystemInterface

- **[로봇 설명 (`hdr_description`)](../../4-hdr_description/README.md)** </br>
지원되는 로봇 모델에 대한 URDF/XACRO, 충돌/시각적 mesh 및 RViz 구성

- **[MoveIt2 구성 (`hdr_moveit_config`)](../../5-hdr_moveit_config/README.md)** </br>
SRDF, Soft limits, 기구학 및 모션 플래닝 설정을 포함한 로봇 모델 별 MoveIt2 구성

- **[Gazebo 시뮬레이션 (`hdr_simulation_gz`)](../../6-hdr_simulation_gz/README.md)** </br>
Gazebo Ignition 시뮬레이션 연동

- **[커스텀 메시지 (`hdr_msgs`)](../../7-hdr_msgs/README.md)** </br>
HD현대로보틱스 제어기와의 통신을 위한 커스텀 ROS2 서비스 및 메시지 정의


### 다음 단계

1. 위 링크된 개별 패키지 문서를 검토하십시오.
2. [설치](../2-installation/README.md)로 진행하여 패키지를 빌드하십시오.
3. [초기 설정](../3-initial-setup/README.md)에서 로봇 연결을 구성하십시오.

[__SOURCE](2-start/2-installation/README.md)
# 2.2 패키지 빌드 및 설치
이 섹션에서는 레포지토리 복제, 종속성 설치 및 패키지 빌드를 포함한 HD현대로보틱스 ROS2 드라이버의 설치 과정을 다룹니다.

### 작업공간 설정

#### ROS2 작업공간 생성

```bash
# 작업공간 디렉토리 생성
mkdir -p ~/hdr_ws/src
cd ~/hdr_ws
```

#### 소스 레포지토리 복제

```bash
cd ~/hdr_ws/src

# HDR 핵심 드라이버 및 client 라이브러리
git clone https://github.com/hyundai-robotics/hdr_ros2_driver.git
git clone https://github.com/hyundai-robotics/hdr_client_driver.git

# HDR description 패키지
git clone https://github.com/hyundai-robotics/hdr_description.git

# Gazebo 시뮬레이션
git clone https://github.com/hyundai-robotics/hdr_simulation_gz.git
```

### 종속성 설치

#### ROS2 종속성 설치

```bash
cd ~/hdr_ws

# 패키지 데이터베이스 업데이트
rosdep update

# HDR 패키지의 모든 종속성 설치
rosdep install --from-paths src --ignore-src --rosdistro $ROS_DISTRO -y
```

### 빌드 프로세스

#### 표준 빌드

```bash
cd ~/hdr_ws

# 최적화를 통해 모든 패키지 빌드
colcon build --symlink-install --cmake-args=-DCMAKE_BUILD_TYPE=Release
```

#### 빌드 구성 옵션
```bash
# 디버그 기호와 함께 빌드
colcon build --symlink-install --cmake-args=-DCMAKE_BUILD_TYPE=Debug
```

#### 환경 설정

```bash
cd ~/hdr_ws
source install/setup.bash

echo "source ~/hdr_ws/install/setup.bash" >> ~/.bashrc
```

### 다음 단계

패키지 설치 및 빌드 성공 후:
1. 제어기 및 PC 설정을 위해 [초기 설정](../3-initial-setup/README.md)을 진행하십시오
2. [설치 검증](../4-verifying/README.md) 테스트를 실행하십시오

[__SOURCE](2-start/3-initial-setup/README.md)
# 2.3 제어기 및 PC 통신 설정

본 가이드는 HD현대로보틱스 로봇 제어기와 통신하기 위한 개발 PC의 네트워크 인터페이스 구성을 다룹니다.

### 전제조건
⚠️ 설정을 시작하기 전에 아래 내용을 확인하세요:
- **로봇 제어기 SW 버전**: SW 버전 **60.32-00** 이상의 Hi6, Hi7 시리즈 제어기

### 네트워크 구성 개요

PC는 이더넷을 통해 로봇 제어기와 통신하도록 구성되어야 합니다. 기본 구성은 제어기가 192.168.1.150에 있는 192.168.1.x 서브넷을 사용합니다.

### 기본 네트워크 구성 (LAN1 사용 시)

| 구성 요소 | 매개변수 | 기본값 |
|-----------|-----------|---------------|
| **PC IP 주소** | 고정 IP | 192.168.1.x (사용자 설정)|
| **로봇 제어기 IP** | 고정 IP | 192.168.1.150 |
| **서브넷 마스크** | 네트워크 마스크 | 255.255.255.0 |
| **게이트웨이** | 기본 게이트웨이 | 192.168.1.1  |

### 케이블 연결

![controller](../../_assets/controller.png)

1. **로봇 제어기 이더넷 포트 위치 확인**
   - **Hi6-N 제어기**: 메인 모듈 상단 이더넷 포트
   - **Hi6-T 제어기**: 제어기 전면 이더넷 포트

2. **이더넷 케이블 연결**
   - Cat5e 또는 Cat6 이더넷 케이블 사용
   - **권장사항**: LAN1 사용 (일반적으로 192.168.1.x로 미리 구성됨)
   - LAN2, LAN3 포트도 사용 가능하며, 기본 설정된 제어기 IP는 각각 다음과 같습니다. </br>
      LAN2: 192.168.4.150 → PC는 192.168.4.x 대역으로 설정 필요 </br>
      LAN3: 192.168.3.150 → PC는 192.168.3.x 대역으로 설정 필요

3. **물리적 연결 확인**
   - 케이블 연결이 안전한지 확인
   - 네트워크 포트의 LED 표시등 확인 (있는 경우)


### PC 네트워크 인터페이스 구성

![LAN_com](../../_assets/LAN_com.png)

#### Network Manager GUI 사용

##### Ubuntu Desktop (GNOME)

1. **네트워크 설정 열기**
   - 우측 상단의 네트워크 아이콘을 클릭
   - "유선 설정"을 선택하거나 설정 → 네트워크로 이동

2. **유선 연결 구성**
   - 유선 연결 옆의 톱니바퀴 아이콘을 클릭
   - "IPv4" 탭으로 이동

3. **고정 IP 구성 설정 (LAN1 사용 시)**
   - **방법**: 수동
   - **주소**: 192.168.1.100
   - **넷마스크**: 255.255.255.0
   - **게이트웨이**: 192.168.1.1

4. **설정 적용**
   - "적용"을 클릭하고 네트워크 인터페이스 연결을 해제한 후 재연결

![ip_setup](../../_assets/ip_setup.png)

### 검증

#### 네트워크 구성 확인

```bash
# 네트워크 연결 확인
ping -c 4 192.168.1.150
```

![ping_test](../../_assets/ping_test.png)

[__SOURCE](2-start/4-verifying/README.md)
# 2.4 설치 검증

본 가이드는 HD현대로보틱스 ROS2 드라이버가 올바르게 설치, 구성되고 작동할 준비가 되었는지 확인하는 검증 절차를 제공합니다.


#### 로봇 모드 설정

HDR ROS2 드라이버는 로봇이 **REMOTE** 모드일 때만 동작합니다.

티치 펜던트(TP)에서 모드 스위치를 REMOTE 위치로 전환하여 제어기를 원격 제어 모드로 설정한 후 ROS2 드라이버를 실행하시기 바랍니다.

![ip_setup](../../_assets/tp_operate.png)


#### HDR ROS2 드라이버 실행 테스트

```bash
# HDR ROS2 드라이버 실행 (로봇이 REMOTE 모드에 있는지 확인)
ros2 launch hdr_bringup hdr_control.py \
  robot_model:=hdf7_7      # 로봇 모델 입력 (default: ha006b)


# 다른 터미널에서 controller 매니저 확인
ros2 control list_controllers

# 예상 출력:
# joint_state_broadcaster[joint_state_broadcaster/JointStateBroadcaster] active
# joint_trajectory_controller[joint_trajectory_controller/JointTrajectoryController] active
```

#### joint state 발행 테스트

```bash
# joint state가 발행되고 있는지 확인
ros2 topic list | grep joint_states

# joint state 모니터링
ros2 topic echo /joint_states --once

# 발행 hz 확인
ros2 topic hz /joint_states
```

[__SOURCE](3-hdr_ros2_driver/README.md)
# 3. ROS2 드라이버 (`hdr_ros2_driver`)

`hdr_ros2_driver` 패키지는 HD현대로보틱스의 Open API와 인터페이스하기 위한 핵심 ROS2 드라이버를 제공합니다. 이 드라이버는 REST API를 통해 로봇 제어기와의 포괄적인 통신을 가능하게 하며, 로봇 제어, 모니터링, 파일 작업 및 시스템 관리를 위한 서비스를 지원합니다.

### 주요 기능

- **로봇 상태 퍼블리싱**: `/joint_states` 토픽을 통한 실시간 joint state 정보
- **모션 제어**: ROS2 action을 통한 joint trajectory 제어
- **포괄적인 서비스**: 기능별로 구성된 30개 이상의 서비스 엔드포인트


### 상세 문서

- [실행 지침](1-launch/README.md) - 드라이버 실행을 위한 launch 파일
- [구성 매개변수](2-parameters/README.md) - 사용 가능한 launch 내 매개변수
- [제공되는 토픽](3-topics/README.md) - 퍼블리시되는 로봇 상태 정보
- [사용 가능한 action](4-actions/README.md) - joint trajectory 실행 및 모션 제어
- [지원 ROS2 서비스](5-services/README.md) - API 서비스 참조

[__SOURCE](3-hdr_ros2_driver/1-launch/README.md)
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

### 사용자 정의 구성

#### 사용자 정의 IP 및 포트
```bash
# 사용자 정의 네트워크 설정으로 실행
ros2 launch hdr_ros2_driver hdr_ros2_driver_launch.py \
  openapi_ip:=192.168.0.10 \
  openapi_port:=8080
```

### 실행 매개변수

| 매개변수 | 타입 | 기본값 | 설명 |
|-----------|------|---------|-------------|
| `openapi_ip` | string | `192.168.1.150` | 로봇 제어기 서버 IP 주소 |
| `openapi_port` | int | `8888` | 제어기 서버의 포트 번호 |
| `robot_model` | string | `ha006b` | 로봇 모델명 |

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
   - 제어기 SW 버전이 **60.32-00** 이상인지 확인
   
[__SOURCE](3-hdr_ros2_driver/2-topics/README.md)
# 3.2 제공되는 토픽

### 개요

ROS2 드라이버는 표준화된 ROS2 토픽을 통해 실시간 로봇 데이터를 퍼블리시합니다. 이러한 토픽은 모니터링 및 제어 애플리케이션을 위한 조인트 상태, 로봇 상태 정보 및 진단 데이터를 제공합니다.

### publish되는 토픽

#### 조인트 상태 정보

##### `/joint_states` (sensor_msgs/msg/JointState)
**설명**: 실시간 조인트 position 데이터

**메시지 필드**:
```yaml
std_msgs/Header header
  uint32 seq
  time stamp
  string frame_id
string[] name          # URDF와 일치하는 조인트 이름
float64[] position     # 라디안 단위의 조인트 position
float64[] velocity     # 라디안/초 단위의 조인트 velocity
float64[] effort       # 조인트 torque
```

**퍼블리싱 주기**: 50 Hz (`publish_rate` 매개변수를 통해 구성 가능)

[__SOURCE](3-hdr_ros2_driver/3-actions/README.md)
# 3.3 사용 가능한 action

### 개요

ROS2 드라이버는 로봇 joint trajectory 제어에 대한 action 인터페이스를 제공합니다. action은 진행 상황 피드백 및 취소 기능과 함께 비동기 작업을 가능하게 합니다.

### joint trajectory control action

#### `/joint_trajectory_controller/follow_joint_trajectory` (control_msgs/action/FollowJointTrajectory)

**설명**: joint trajectory 제어를 실행합니다.

**action_goal**:
```yaml
trajectory_msgs/JointTrajectory trajectory
  std_msgs/Header header
  actionlib_msgs/GoalID goal_id
    time stamp
    string id
  control_msgs/FollowJointTrajectoryGoal goal
    trajectory_msgs/JointTrajectory trajectory
      std_msgs/Header header
      string[] joint_names
      trajectory_msgs/JointTrajectoryPoint[] points
    control_msgs/JointTolerance[] path_tolerance
      string name
      float64 position
      float64 velocity
      float64 acceleration
    control_msgs/JointTolerance[] goal_tolerance
      string name
      float64 position
      float64 velocity
      float64 acceleration
    duration goal_time_tolerance
```

**action_feedback**:
```yaml
std_msgs/Header header
string[] joint_names
trajectory_msgs/JointTrajectoryPoint desired
trajectory_msgs/JointTrajectoryPoint actual  
trajectory_msgs/JointTrajectoryPoint error
```

**action_result**:
```yaml
std_msgs/Header header
actionlib_msgs/GoalStatus status
control_msgs/FollowJointTrajectoryResult result
```

[__SOURCE](3-hdr_ros2_driver/4-services/README.md)
# 3.4 ROS2 드라이버 서비스

### 개요

`hdr_ros2_driver`는 HD현대로보틱스 Hi6, Hi7 제어기와 통신하기 위한 다양한 ROS2 서비스를 제공합니다. 

### 서비스 범주

| 범주 | 설명 |
|------|------|
| **[제어 서비스](1-control/README.md)** | 로봇 제어, 모터 전원, 비상정지, 좌표계, I/O 관리 |
| **[작업 관리](2-task/README.md)** | 변수 할당, 동작 실행, 프로그램 제어 |
| **[파일 관리](3-file/README.md)** | 파일 업로드/다운로드, 디렉토리 조작 |
| **[PLC 통신](4-plc/README.md)** | PLC 릴레이 값 제어 |
| **[콘솔 명령](5-console/README.md)** | 콘솔 명령 실행, 시스템 시간, 로그 관리 |
| **[프로젝트 관리](6-project/README.md)** | 작업 정보, 작업 삭제/재로드 |
| **[버전 정보](7-version/README.md)** | API 버전, 시스템 버전 조회 |

### 기본 사용법

#### 서비스 목록 확인
```bash
# 모든 HDR 드라이버 서비스 목록
ros2 service list | grep hdr_ros2_driver
```

#### 일반적인 서비스 호출
```bash
# API 버전 확인
ros2 service call /hdr_ros2_driver/get/api_ver std_srvs/srv/Trigger

# 모터 상태 확인
ros2 service call /hdr_ros2_driver/robot/get/motor_state std_srvs/srv/Trigger

# 모터 전원 켜기
ros2 service call /hdr_ros2_driver/robot/post/motor_power std_srvs/srv/Trigger
```

[__SOURCE](4-hdr_hardware_interface/README.md)
# 4. ROS2 제어 통합 (`hdr_hardware_interface`)

### 개요

`hdr_hardware_interface` 패키지는 HD 현대로보틱스의 Open API 기반 제어기를 ROS2 제어 프레임워크와 연결하기 위한 `ros2_control` SystemInterface를 제공합니다. 조인트 position 상태 및 명령 인터페이스를 HTTP 기반 로봇 서비스에 매핑하며 제어기 라이프사이클, 실시간 pose 추적을 처리합니다.

### 패키지 구조

| 디렉토리                           | 설명                                                                 |
| ----------------------------------- | ----------------------------------------------------------------------------|
| `include/`                          | `HDRRobotHardware` 및 유틸리티 헬퍼를 포함한 C++ 헤더                |
| `src/`                              | SystemInterface 로직 구현                                     |
| `launch/`                           | `ros2_control` 인터페이스를 실행하기 위한 런치 파일 제공             |
| `config/`                           | 제어기 및 기구학 설정을 위한 YAML 구성 파일 포함   |
| `hdr_hardware_interface_plugin.xml` | pluginlib용 메타데이터                                               |

---

### 사용법

###### ros2_control로 HDR 하드웨어 인터페이스 실행

```bash
ros2 launch hdr_hardware_interface ros2_control.launch.py \
  robot_model:=hdf7_9 \
  openapi_ip:=192.168.1.150 \
  openapi_port:=8888
```

###### 플러그인 구성
하드웨어 인터페이스를 활성화하려면 URDF 또는 xacro의 `<ros2_control>` 내에 포함시킵니다

```xml
<ros2_control name="HDRRobotHardware" type="system">
  <hardware>
    <plugin>hdr_hardware_interface/HDRRobotHardware</plugin>
    <param name="robot_model">ha006b</param>
    <param name="openapi_ip">192.168.1.150</param>
    <param name="openapi_port">8888</param>
  </hardware>
</ros2_control>
```

##### 구성 옵션

| 매개변수                      | 타입   | 기본값                         | 설명                                                                 |
|---------------------------|--------|----------------------------------|-----------------------------------------------------------------------------|
| `robot_model`             | string | `"ha006b"`                      | 로봇 모델 이름                               |
| `openapi_ip`              | string | `"192.168.1.150"`               | 로봇 제어기의 HTTP API IP 주소                                  |                              |
| `command_start_time`   | float  | `-1.0`                          | 명령 실행 시간 (즉시 실행의 경우 -1.0)             |
| `command_buffer_size`  | int    | `5`                             | 명령 데이터 버퍼 크기                                 |
| `use_sim`                 | bool   | `false`                         | `gz_ros2_control/GazeboSimSystem` 플러그인을 사용하여 시뮬레이션 모드를 활성화하며, 일반적으로 Ignition Gazebo와의 통합에 사용됩니다<br>`use_sim_time` 매개변수도 true로 설정되어 시뮬레이션 시간과 동기화됩니다     |
| `use_mock_hardware`       | bool   | `false`                         | 로봇 없이 테스트하기 위해 `mock_components/GenericSystem`을 사용하는 mock 하드웨어 인터페이스를 활성화합니다   |
| `initial_positions_file`  | string | `""`                            | 초기 조인트 위치를 지정하는 선택적 YAML 파일                       |
| `controllers_config_package` | string | `"hdr_hardware_interface"`     | config YAML이 포함된 패키지 이름                                       |
| `controllers_file`        | string | `"default_controllers.yaml"`   | 제어기 구성 YAML 파일명                                     |
| `kinematics_file`         | string | `"default_kinematics.yaml"`    | 기구학 플러그인 구성 YAML 파일명                              |


##### 토픽

| 토픽 이름                   | 메시지 타입                   | 설명                               |
| ---------------------------- | ------------------------------ | ----------------------------------------- |
| `/joint_states`              | sensor_msgs::msg::JointState | position 정보를 포함한 현재 조인트 상태를 퍼블리시합니다 |
| `/controller_manager/status` | lifecycle_msgs::msg::State   | ros2_control 매니저의 라이프사이클 상태 |

##### 액션

| 액션 이름                                            | 액션 타입                                   | 설명                                |
| ------------------------------------------------------ | --------------------------------------------- | ------------------------------------------ |
| `/joint_trajectory_controller/follow_joint_trajectory` | control_msgs::action::FollowJointTrajectory | ROS2 action을 통해 조인트 궤적 명령을 실행합니다 |

##### 서비스

| 서비스 이름                                   | 서비스 타입                                         | 설명                         |
| ---------------------------------------------- | ---------------------------------------------------- | ----------------------------------- |
| `/controller_manager/list_controllers`         | controller_manager_msgs/srv/ListControllers        | 활성화된 controller 목록을 반환합니다     |
| `/controller_manager/list_hardware_interfaces` | controller_manager_msgs/srv/ListHardwareInterfaces | 사용 가능한 조인트 명령 및 상태 인터페이스를 반환합니다 |
| `/controller_manager/switch_controller`        | controller_manager_msgs/srv/SwitchController       | controller를 활성화하거나 비활성화합니다  |
| `/controller_manager/load_controller`          | controller_manager_msgs/srv/LoadController         | controller를 로드합니다             |
| `/controller_manager/unload_controller`        | controller_manager_msgs/srv/UnloadController       | 지정된 controller를 언로드합니다.    |

---

[__SOURCE](5-hdr_description/README.md)
# 5. 로봇 URDF (`hdr_description`)

`hdr_description` 패키지는 ROS2에서 HD현대로보틱스 로봇을 위한 로봇 URDF, mesh, 시각화 구성을 포함합니다. 이 패키지는 시뮬레이션, 시각화, 모션 플래닝에 필요한 기본적인 URDF/XACRO 정의를 제공합니다.

### 주요 기능

- **로봇 모델 별 URDF**: 지원하는 모든 로봇 모델용 URDF/XACRO 파일
- **3D Mesh**: 정확한 시뮬레이션을 위한 충돌 및 시각적 메시
- **RViz 통합**: 미리 구성된 시각화 설정
- **ros2_control 통합**: 조인트 인터페이스 정의

### 패키지 구조

| 디렉토리 | 내용 | 목적 |
|-----------|----------|----------|
| `urdf/` | 로봇 URDF 파일 | URDF/XACRO 정의 |
| `meshes/` | 3D 모델 mesh 파일 | 충돌 및 시각적 표현 |
| `launch/` | 시각화 실행 파일 | RViz 디스플레이 구성 |
| `rviz/` | RViz 구성 파일 | 디스플레이 설정 및 플러그인 |

### URDF 구성

#### 주요 파일
- **`hdr.urdf.xacro`**: 모든 구성 요소를 포함하는 최상위 매크로
- **`hdr.ros2_control.xacro`**: ros2_control 하드웨어 인터페이스 매크로

#### 로봇별 파일
각 로봇 모델은 `urdf/robots/` 하위에 고유한 디렉토리를 가집니다:
- `ha006b.urdf.xacro`
- `hdf7_9.urdf.xacro` 
- `hdf8_8.urdf.xacro`
- `hdr10l_19.urdf.xacro`
- `hdr20_17.urdf.xacro`
- `hdr50_22.urdf.xacro`
- `hdr220_26.urdf.xacro`
- `hh020.urdf.xacro`
- `hdr35_20.urdf.xacro`

### 사용 예제

#### RViz에서 시각화
```bash
ros2 launch hdr_description display_robot.launch.py robot_model:=ha006b
```

#### 실행 매개변수

| 매개변수 | 타입 | 기본값 | 설명 |
|-----------|------|---------|-------------|
| `robot_model` | string | `ha006b` | 표시할 로봇 모델 |
| `description_package` | string | `hdr_description` | URDF 파일이 포함된 패키지 |
| `description_file` | string | `hdr.urdf.xacro` | 메인 URDF/XACRO 파일 |

### 메시 품질

패키지는 각 로봇에 대해 두 가지 유형의 메시를 제공합니다:

#### 시각적 메시
- 현실적인 시각화를 위한 고해상도 mesh
- 상세한 표면 텍스처 및 재질
- RViz 및 Gazebo에서 시각적 표현에 사용

#### 충돌 메시  
- 충돌 감지를 위한 단순화된 mesh
- 계산 효율성에 최적화됨
- 물리 엔진 및 모션 플래너에서 사용

모델별 세부사항은 [지원되는 로봇 모델](../0-intro/2-robot-models/README.md)을 참조하세요.

[__SOURCE](6-hdr_moveit_config/README.md)
# 6. MoveIt2 구성 (`hdr_moveit_config`)

`hdr_moveit_config` 패키지는 실제 환경과 시뮬레이션 환경에서 HD현대로보틱스 로봇을 제어하기 위한 MoveIt2 구성 패키지를 제공합니다. 이 패키지는 SRDF 정의, 조인트 제한 및 제어기 설정을 포함한 로봇별 모션 플래닝 구성을 포함합니다.

### 주요 기능

- **로봇별 구성**: 지원되는 각 로봇 모델에 대한 개별 MoveIt2 설정
- **SRDF 정의**: 플래닝 그룹 및 자세가 포함된 의미적 로봇 기술서
- **조인트 제한 관리**: 안전한 작동을 위한 속도 및 가속도 스케일링
- **기구학 통합**: 순기구학/역기구학 솔버 구성
- **제어기 통합**: ros2_control 및 궤적 실행 설정

### 패키지 조직

각 로봇 모델은 고유한 MoveIt2 구성 패키지를 가집니다:

- `ha006b_moveit_config/`
- `hdf7_9_moveit_config/` 
- `hdf8_8_moveit_config/`
- `hdr10l_19_moveit_config/`
- `hdr20_17_moveit_config/`
- `hdr50_22_moveit_config/`
- `hdr220_26_moveit_config/`
- `hh020_moveit_config/`
- `hdr35_20_moveit_config/`

### 구성 파일

각 로봇 구성에는 다음이 포함됩니다:

#### 핵심 구성
- **SRDF 파일**: 플래닝 그룹이 포함된 의미적 로봇 기술서
- **joint_limits.yaml**: 스케일링 팩터가 있는 속도 및 가속도 제한
- **kinematics.yaml**: 기구학 솔버 플러그인 구성
- **controllers.yaml**: ros2_control 궤적 제어기 설정

#### 고급 설정
- **ompl_planning.yaml**: OMPL 모션 플래너 구성
- **pilz_cartesian_limits.yaml**: Pilz 플래너용 직교 모션 제한
- **sensors_3d.yaml**: 3D 센서 통합 (해당하는 경우)
- **initial_positions.yaml**: 기본 시작 자세

### 안전 고려사항

#### 속도 스케일링
안정적인 작동을 위해 **≤ 0.5**의 스케일링 팩터 사용을 권장합니다:

```yaml
default_velocity_scaling_factor: 0.5
default_acceleration_scaling_factor: 0.5
```

#### 조인트 제한
`joint_limits.yaml` 파일은 다음을 정의합니다:
- 최대 조인트 속도
- 최대 조인트 가속도  
- 소프트웨어 위치 제한
- 모션 플래닝용 스케일링 팩터

### 실행

```bash
ros2 launch hdr_bringup hdr_moveit.launch.py robot_model:=ha006b
```

![hdr_moveit](../_assets/hdr_moveit.png)

### 플래닝 그룹

일반적인 SRDF 플래닝 그룹 구성:

```xml
<group name="manipulator">
    <chain base_link="base_link" tip_link="link6"/>
</group>

<group_state name="home" group="manipulator">
    <joint name="j1" value="0"/>
    <joint name="j2" value="0"/>
    <joint name="j3" value="0"/>
    <joint name="j4" value="0"/>
    <joint name="j5" value="0"/>
    <joint name="j6" value="0"/>
</group_state>
```


### 사용자 정의

모션 플래닝 동작을 수정하려면:
1. 속도/가속도 제한을 위해 `joint_limits.yaml` 편집 (URDF 상에 정의된 조인트 별 최대 속도 초과하여 적용 불가능)
2. 플래너별 설정을 위해 `ompl_planning.yaml` 수정
3. 새로운 플래닝 그룹 또는 자세를 위해 SRDF 업데이트
4. `controllers.yaml`에서 제어기 매개변수 조정

[__SOURCE](7-hdr_client_driver/README.md)
# 7. HD현대로보틱스 클라이언트 드라이버

HDR 클라이언트 드라이버는 HD현대로보틱스의 로봇 제어기와 HTTP (Open API) 및 소켓 (TCP/UDP) 인터페이스를 통해 통신하기 위한 포괄적인 C++ 라이브러리를 제공합니다. 이 라이브러리는 양쪽 통신 계층을 추상화하고 로봇 제어 및 모니터링, 파일 관리, 실시간 명령 실행, ROS2와의 통합을 위한 객체지향 인터페이스를 제공합니다.

> ❗ 중요: 모든 REST API 기반 통신은 로봇이 REMOTE 모드에 있어야 동작 합니다.

### 패키지 구조

| 디렉터리 | 설명 |
|----------|------|
| `include/` | HDR 클라이언트 드라이버 라이브러리를 위한 헤더 파일 |
| `src/` | 클라이언트 드라이버 함수의 소스 구현 |
| `src/functions/` | 다양한 로봇 제어기 기능을 위한 API 카테고리 구현 |
| `examples/` | 드라이버 API 사용 방법을 보여주는 예제 프로그램 |

[__SOURCE](7-hdr_client_driver/1-api-categories/README.md)
# 7.1 API 카테고리

HDR 클라이언트 드라이버는 다음과 같은 API 카테고리를 지원합니다:

### 지원되는 API 카테고리

HDR 클라이언트 드라이버는 로봇 제어기의 다양한 기능에 대응하는 다음과 같은 API 카테고리를 제공합니다:

- **[제어](1-control/README.md)** - 기본 로봇 제어 작업
- **[로봇](2-robot/README.md)** - 로봇 모션 및 상태 관리
- **[프로젝트](3-project/README.md)** - 프로젝트 및 작업 관리
- **[파일](4-file/README.md)** - 파일 시스템 작업
- **[I/O](5-io/README.md)** - 입력/출력 제어
- **[작업](6-task/README.md)** - 작업 실행 및 변수 관리
- **[기타](7-etc/README.md)** - 시스템 유틸리티

[__SOURCE](8-hdr_simulation_gz/README.md)
# 8. Gazebo 시뮬레이션 (`hdr_simulation_gz`)

`hdr_simulation_gz` 패키지는 HD현대로보틱스 산업용 로봇을 위한 ROS2 + Gazebo (Ignition) 시뮬레이션 환경을 제공합니다. 이 패키지는 물리적 하드웨어 없이도 로봇 응용 프로그램의 개발, 테스트 및 검증을 가능하게 합니다.

### 주요 기능

- **Gazebo 통합**: Ignition Gazebo 시뮬레이션 지원
- **물리 시뮬레이션**: 현실적인 로봇 동역학 및 충돌 감지
- **MoveIt2 호환**: 시뮬레이션 환경에서의 모션 플래닝
- **ros2_control 통합**: `gz_ros2_control/GazeboSimSystem` 플러그인 사용

### 패키지 구조

| 디렉토리 | 내용 | 목적 |
|-----------|----------|----------|
| `launch/` | 시뮬레이션 실행 파일 | 로봇 생성 및 제어기 설정 |
| `config/` | 제어기 구성 파일 | ros2_control YAML 파일 |

### 실행 파일

#### 로봇 생성
```bash
# ros2_control이 포함된 로봇을 Gazebo에서 spawn
ros2 launch hdr_simulation_gz hdr_gz_spawn.launch.py robot_model:=ha006b
```

#### MoveIt2 통합
```bash
# MoveIt2 모션 플래닝과 함께 시뮬레이션 실행
ros2 launch hdr_simulation_gz hdr_gz_moveit.launch.py robot_model:=hdr50_22
```

### 구성 옵션

| 매개변수 | 타입 | 기본값 | 설명 |
|-----------|------|---------|-------------|
| `robot_model` | string | `ha006b` | 시뮬레이션할 로봇 모델 |
| `use_sim` | bool | `true` | Gazebo 시뮬레이션 모드 활성화 |
| `runtime_config_package` | string | `hdr_simulation_gz` | 제어기 구성 패키지 |
| `controllers_file` | string | `hdr_controllers.yaml` | 제어기 구성 파일 |
| `description_package` | string | `hdr_description` | URDF 패키지 이름 |
| `description_file` | string | `hdr.urdf.xacro` | 로봇 설명 파일 |
| `initial_positions_file` | string | `initial_positions.yaml` | 시작 조인트 위치 |
| `kinematics_file` | string | `kinematics.yaml` | 기구학 솔버 구성 |


### 향후 개선사항
- 센서 및 툴 시뮬레이션 지원
- world 및 예제 지원

[__SOURCE](9-hdr_msgs/README.md)
# 9. HD현대로보틱스 ROS2 메시지

### 개요

`hdr_msgs` 패키지는 HD현대로보틱스 소프트웨어 스택에서 사용되는 사용자 정의 ROS2 message 타입을 정의합니다. 


### ROS2 messages

| Message Type          | 설명                                           |
|-----------------------|-------------------------------------------------------|
| `srv/DateTime.srv`    | 로봇 제어기의 시스템 시간를 가져오거나 설정합니다. 입력에는 전체 날짜/시간 필드(year, mon, day, hour, min, sec)가 포함됩니다. |
| `srv/Emergency.srv`   | 단계적 매개변수(step_no, stop_at, stop_mode)를 사용하여 비상 정지 로직을 테스트합니다. 시뮬레이션/테스트 시나리오에 사용됩니다. |
| `srv/ExecuteCmd.srv`  | 콘솔 명령어를 문자열 라인 목록으로 실행하며, 실행 간격을 설정할 수 있습니다. rl.stop과 같은 원시 저수준 명령어에 유용합니다. |
| `srv/ExecuteMove.srv` | 문자열 기반 명령문을 사용하여 로봇 이동 명령을 실행합니다. 예: "move L,spd=1sec,tool=1 [0, 0, 0, 0, 90, 0]". task_no는 작업 인덱스를 식별합니다(일반적으로 0). |
| `srv/FileList.srv`    | 로봇에서 디렉토리 내용을 조회합니다. 불리언 값을 통해 파일이나 디렉토리를 포함하도록 필터링할 수 있습니다. |
| `srv/FilePath.srv`    | 읽기, 삭제, 존재 확인과 같은 작업을 위해 파일 경로를 전송하거나 조회할 수 있습니다. |
| `srv/FileRename.srv`  | 로봇 제어기의 파일 시스템에서 파일 이름을 변경하거나 이동합니다. |
| `srv/FileSend.srv`    | 로컬 PC에서 로봇 제어기로 파일을 업로드합니다. 소스 및 대상 경로가 필요합니다. |
| `srv/IoplcGet.srv`    | PLC 메모리(예: 릴레이, M, S, R)를 읽습니다. 직접 주소 지정과 이름 기반 신호 주소 지정을 모두 지원합니다. |
| `srv/IoplcPost.srv`   | M, S, R 또는 FBx.y와 같은 심볼릭 이름을 사용하여 PLC 메모리(릴레이)에 씁니다. |
| `srv/IoRequest.srv`   | 디지털, 시리얼 또는 사용자 I/O에 접근하는 데 사용됩니다. type 필드는 'di', 'do', 'si' 또는 'so'와 같은 I/O 종류를 지정합니다. blk_no와 sig_no는 블록 및 신호 인덱스를 지정합니다. 'val' 필드는 I/O 값을 설정할 때 사용되며 읽기 작업을 수행할 때는 무시됩니다. |
| `srv/JointTrajecotryPoints.srv` | 모션 실행을 위한 궤적 정보를 제공합니다. |
| `srv/LogManager.srv`  | 카테고리(E, W 등), ID 범위 및 타임스탬프 필터를 사용하여 로그 항목을 조회합니다. |
| `srv/Number.srv`      | 정수를 전송/수신하는 범용 서비스입니다. 도구 번호, 좌표계, 인덱스 설정 등에 사용됩니다. |
| `srv/OpCnd.srv`       | 재생 모드나 사용자 좌표계와 같은 작동 조건을 읽거나 씁니다. |
| `srv/PoseCur.srv`     | 내부 구성에 따라 관절 공간 또는 작업 공간에서 현재 로봇 포즈(위치 + 방향)를 가져옵니다. |
| `srv/ProgramCnt.srv`  | 작업 로직의 특정 위치로 이동하기 위해 프로그램 실행 포인터(pno, sno, fno 등)를 설정합니다. |
| `srv/ProgramVar.srv`  | 변수를 읽거나 할당합니다. 범위(로컬/글로벌), 표현식 및 지속성을 지정할 수 있습니다. |

[__SOURCE](10-running/README.md)
# 10. ROS2 드라이버 실행 및 로봇 제어

### 개요

이 섹션에서는 ROS2 드라이버를 사용하여 HD현대로보틱스 로봇을 조작하는 포괄적인 가이드를 제공합니다.

HD현대로보틱스 ROS2 시스템은 다음과 같은 제어 방법을 제공합니다:

- **MoveIt2 통합**: 모션 플래닝 및 실행
- **ros2_control**: 하드웨어 인터페이스 제어  
- **ROS2 서비스**: 제어기 API 접근

### 다음 단계

- [MoveIt2 실행 절차](1-launch-moveit2/README.md)
- [ros2_control 직접 제어](2-launch-ros2_control/README.md)

[__SOURCE](10-running/1-launch-moveit2/README.md)
# 10.1 MoveIt2로 실행하기

### 개요

HD현대로보틱스 로봇을 MoveIt2로 실행하는 기본 절차입니다.

### 실행 전 준비사항

#### 하드웨어 준비
- 로봇 제어기 전원 켜고 REMOTE 모드 설정
- 비상 정지 버튼이 접근 가능한 위치에 있는지 확인
- 네트워크 연결 확인 (ping 192.168.1.150)
- 작업 공간에 장애물이 없는지 확인

#### 소프트웨어 준비
- ROS2 환경 설정: `source ~/ros2_ws/install/setup.bash`
- 로봇 모델 확인

### 기본 실행 절차

#### 1. MoveIt2 실행
```bash
# 기본 MoveIt2 실행
ros2 launch hdr_bringup hdr_moveit.launch.py robot_model:=ha006b

# IP 주소 지정해서 실행  
ros2 launch hdr_bringup hdr_moveit.launch.py \
    robot_model:=ha006b \
    robot_ip:=192.168.1.150
```

#### 2. 연결 상태 확인
```bash
# 조인트 상태 확인
ros2 topic echo /joint_states --once

# MoveIt2 서비스 확인
ros2 service list | grep move_group
```

### 지원되는 로봇 모델

- ha006b
- hdf7_9
- hdf8_8
- hdr10l_19
- hdr20_17
- hdr50_22
- hdr220_26
- hh020
- hdr35_20

#### 일반적인 문제

**연결 문제**
- 네트워크 연결 확인: `ping 192.168.1.150`
- 로봇 제어기가 REMOTE 모드인지 확인

**제어기가 시작되지 않는 경우:**
- 로봇 제어기가 REMOTE 모드인지 확인
- 네트워크 연결 확인
- 로봇이 비상 정지 상태가 아닌지 확인

**조인트 상태가 발행되지 않는 경우:**
- 하드웨어 인터페이스 연결 상태 확인
- 로봇 제어기 상태 확인

**궤적 실행 실패:**
- 조인트 한계값 확인
- 목표 위치가 유효한지 확인
- 제어기 오류 메시지 확인

#### 모터 ON & START 모드 상태에서 로봇이 동작하지 않을 떄

**정상 동작**
- 모터 ON과 START 모드가 모두 활성화되어 있을 때 로봇은 정상적으로 동작

**로봇이 동작하지 않는 경우**
- 모터 ON은 켜져 있지만 START 모드가 활성화되어 있지 않으면 E01554 오류 발생
- 조인트 한계값을 넘어가는 등 실행할 수 없는 명령어를 입력한 경우 회전 축의 속도 초과 오류가 발생하여 로봇이 정지
- 해당 상황에서는 모터 ON + START 모드를 다시 활성화하여 시스템을 복구

### 안전 주의사항

- 실제 로봇과 작업할 때는 항상 비상 정지 버튼을 접근 가능한 곳에 두세요
- 로봇이 예상치 못한 동작을 할 경우 즉시 비상 정지하세요
- 처음 사용할 때는 낮은 속도로 테스트하세요

[__SOURCE](10-running/2-launch-ros2_control/README.md)
# 10.2 ros2_control 시스템 실행

### 개요

HD현대로보틱스 로봇을 위한 ros2_control 시스템의 기본 실행 방법을 설명합니다.

### 기본 실행

#### ros2_control 실행
```bash
# 기본 실행
ros2 launch hdr_bringup hdr_control.launch.py robot_model:=ha006b

# IP 주소 지정
ros2 launch hdr_bringup hdr_control.launch.py \
    robot_model:=ha006b \
    robot_ip:=192.168.1.150
```

### 제어기

#### 제어기 상태 확인
```bash
# 제어기 목록 보기
ros2 control list_controllers

# 하드웨어 인터페이스 확인
ros2 control list_hardware_interfaces

# 조인트 상태 확인
ros2 topic echo /joint_states
```

#### 제어기 활성화/비활성화
```bash
# 제어기 활성화
ros2 control switch_controllers --activate joint_trajectory_controller

# 제어기 비활성화
ros2 control switch_controllers --deactivate joint_trajectory_controller
```

### 기본 제어기 설정

ros2_control은 다음 제어기들을 제공합니다:

- **joint_state_broadcaster**: 조인트 상태 발행
- **joint_trajectory_controller**: 궤적 추종 제어

### 간단한 테스트

#### 조인트 궤적 테스트
```bash
# 간단한 조인트 이동 테스트
ros2 action send_goal /joint_trajectory_controller/follow_joint_trajectory \
    control_msgs/action/FollowJointTrajectory \
    "{
      trajectory: {
        joint_names: ['j1', 'j2', 'j3', 'j4', 'j5', 'j6'],
        points: [
          {
            positions: [0.0, 0.0, 0.0, 0.0, 0.0, 0.0],
            time_from_start: {sec: 2}
          }
        ]
      }
    }"
```

### 문제 해결

#### 일반적인 문제

**연결 문제**
- 네트워크 연결 확인: `ping 192.168.1.150`
- 로봇 제어기가 REMOTE 모드인지 확인

**제어기가 시작되지 않는 경우:**
- 로봇 제어기가 REMOTE 모드인지 확인
- 네트워크 연결 확인
- 로봇이 비상 정지 상태가 아닌지 확인

**조인트 상태가 발행되지 않는 경우:**
- 하드웨어 인터페이스 연결 상태 확인
- 로봇 제어기 상태 확인

**궤적 실행 실패:**
- 조인트 한계값 확인
- 목표 위치가 유효한지 확인
- 제어기 오류 메시지 확인

#### 모터 ON & START 모드 상태에서 로봇이 동작하지 않을 떄

**정상 동작**
- 모터 ON과 START 모드가 모두 활성화되어 있을 때 로봇은 정상적으로 동작

**로봇이 동작하지 않는 경우**
- 모터 ON은 켜져 있지만 START 모드가 활성화되어 있지 않으면 E01554 오류 발생
- 조인트 한계값을 넘어가는 등 실행할 수 없는 명령어를 입력한 경우 회전 축의 속도 초과 오류가 발생하여 로봇이 정지
- 해당 상황에서는 모터 ON + START 모드를 다시 활성화하여 시스템을 복구

### 안전 주의사항

- 실제 로봇과 작업할 때는 항상 비상 정지 버튼을 접근 가능한 곳에 두세요
- 로봇이 예상치 못한 동작을 할 경우 즉시 비상 정지하세요
- 처음 사용할 때는 낮은 속도로 테스트하세요
