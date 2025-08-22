# Table of contents

* [HD현대로보틱스 ROS2 드라이버 매뉴얼](README.md)

* [0. 개요](0-intro/README.md)
  * [0.1 제어기 모델](0-intro/1-controller-models/README.md)
  * [0.2 로봇 모델](0-intro/2-robot-models/README.md)
  * [0.3 요구사항](0-intro/3-requirements/README.md)
  * [0.4 ROS2 버전](0-intro/4-ros2-version/README.md)

* [1. 시작하기](1-start/README.md)
  * [1.1 레포지토리 개요](1-start/1-repo-overview/README.md)
  * [1.2 설치](1-start/2-installation/README.md)
    * [1.2.1 빌드 및 설치](1-start/2-installation/1-build-install/README.md)
  * [1.3 초기 설정](1-start/3-initial-setup/README.md)
    * [1.3.1 제어기 PC 연결](1-start/3-initial-setup/1-controller-PC/README.md)
    * [1.3.2 제어기 설정](1-start/3-initial-setup/2-controller-set/README.md)
    * [1.3.3 네트워크 테스트](1-start/3-initial-setup/3-network-test/README.md)
  * [1.4 검증](1-start/4-verifying/README.md)

* [2. ROS2 드라이버 (hdr_ros2_driver)](2-hdr_ros2_driver/README.md)
  * [2.1 런치](2-hdr_ros2_driver/1-launch/README.md)
  * [2.2 토픽](2-hdr_ros2_driver/2-topics/README.md)
  * [2.3 액션](2-hdr_ros2_driver/3-actions/README.md)
  * [2.4 서비스](2-hdr_ros2_driver/4-services/README.md)
    * [2.4.1 제어](2-hdr_ros2_driver/4-services/1-control/README.md)
    * [2.4.2 태스크](2-hdr_ros2_driver/4-services/2-task/README.md)
    * [2.4.3 파일](2-hdr_ros2_driver/4-services/3-file/README.md)
    * [2.4.4 PLC](2-hdr_ros2_driver/4-services/4-plc/README.md)
    * [2.4.5 콘솔](2-hdr_ros2_driver/4-services/5-console/README.md)
    * [2.4.6 프로젝트](2-hdr_ros2_driver/4-services/6-project/README.md)
    * [2.4.7 버전](2-hdr_ros2_driver/4-services/7-version/README.md)

* [3. ROS2 제어 통합 (hdr_hardware_interface)](3-hdr_hardware_interface/README.md)

* [4. 로봇 URDF (hdr_description)](4-hdr_description/README.md)

* [5. MoveIt2 구성 (hdr_moveit_config)](5-hdr_moveit_config/README.md)

* [6. C++ 클라이언트 라이브러리 (hdr_client_driver)](6-hdr_client_driver/README.md)
  * [6.1 API 카테고리](6-hdr_client_driver/1-api-categories/README.md)
    * [6.1.1 제어](6-hdr_client_driver/1-api-categories/1-control/README.md)
    * [6.1.2 로봇](6-hdr_client_driver/1-api-categories/2-robot/README.md)
    * [6.1.3 프로젝트](6-hdr_client_driver/1-api-categories/3-project/README.md)
    * [6.1.4 파일](6-hdr_client_driver/1-api-categories/4-file/README.md)
    * [6.1.5 IO](6-hdr_client_driver/1-api-categories/5-io/README.md)
    * [6.1.6 태스크](6-hdr_client_driver/1-api-categories/6-task/README.md)
    * [6.1.7 기타](6-hdr_client_driver/1-api-categories/7-etc/README.md)

* [6. Gazebo 시뮬레이션 (hdr_simulation_gz)](6-hdr_simulation_gz/README.md)

* [7. ROS 메시지 정의 (hdr_msgs)](7-hdr_msgs/README.md)
  * [7.1 서비스 정의](7-hdr_msgs/1-service-definitions/README.md)

* [8. 실행](8-running/README.md)
  * [8.1 MoveIt2 실행](8-running/1-launch-moveit2/README.md)
  * [8.2 ROS2 Control 실행](8-running/2-launch-ros2_control/README.md)
  * [8.3 비상정지](8-running/3-emg-stop/README.md)