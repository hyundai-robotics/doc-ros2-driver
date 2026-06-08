# 3. ROS2 드라이버 (`hdr_ros2_driver`)

`hdr_ros2_driver` 패키지는 HD현대로보틱스의 Open API와 인터페이스하기 위한 핵심 ROS2 드라이버를 제공합니다. 이 드라이버는 REST API를 통해 로봇 제어기와의 포괄적인 통신을 가능하게 하며, 로봇 제어, 모니터링, 파일 작업 및 시스템 관리를 위한 서비스를 지원합니다.

- [소스 코드] [hdr_ros2_driver] [GitHub Repository ↗](https://github.com/hyundai-robotics/hdr_ros2_driver)

### 주요 기능

- **로봇 상태 퍼블리싱**: `/joint_states` 토픽을 통한 실시간 joint state 정보
- **모션 제어**: ROS2 action을 통한 joint trajectory 제어
- **포괄적인 서비스**: 기능별로 구성된 30개 이상의 서비스 엔드포인트


### 상세 문서

- [런치](1-launch/README.md) - 드라이버 실행을 위한 launch 파일
- [토픽](2-topics/README.md) - 퍼블리시되는 로봇 상태 정보
- [액션](3-actions/README.md) - joint trajectory 실행 및 모션 제어
- [서비스](4-services/README.md) - API 서비스 참조
