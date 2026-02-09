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

