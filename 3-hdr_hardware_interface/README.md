# ROS2 제어 통합 (`hdr_hardware_interface`)

## 개요

`hdr_hardware_interface` 패키지는 HD 현대로보틱스의 Open API 기반 제어기를 ROS2 제어 프레임워크와 연결하기 위한 `ros2_control` SystemInterface를 제공합니다. 조인트 position 상태 및 명령 인터페이스를 HTTP 기반 로봇 서비스에 매핑하며 제어기 라이프사이클, 실시간 pose 추적을 처리합니다.

## 패키지 구조

| 디렉토리                           | 설명                                                                 |
| ----------------------------------- | ----------------------------------------------------------------------------|
| `include/`                          | `HDRRobotHardware` 및 유틸리티 헬퍼를 포함한 C++ 헤더                |
| `src/`                              | SystemInterface 로직 구현                                     |
| `launch/`                           | `ros2_control` 인터페이스를 실행하기 위한 런치 파일 제공             |
| `config/`                           | 제어기 및 기구학 설정을 위한 YAML 구성 파일 포함   |
| `hdr_hardware_interface_plugin.xml` | pluginlib용 메타데이터                                               |

---

## 사용법

##### ros2_control로 HDR 하드웨어 인터페이스 실행

```bash
ros2 launch hdr_hardware_interface ros2_control.launch.py \
  robot_model:=hdf7_9 \
  openapi_ip:=192.168.1.150 \
  openapi_port:=8888
```

##### 플러그인 구성
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

#### 구성 옵션

| 매개변수                      | 타입   | 기본값                         | 설명                                                                 |
|---------------------------|--------|----------------------------------|-----------------------------------------------------------------------------|
| `robot_model`             | string | `"ha006b"`                      | 로봇 모델 이름                               |
| `openapi_ip`              | string | `"192.168.1.150"`               | 로봇 제어기의 HTTP API IP 주소                                  |
| `openapi_port`            | int    | `8888`                          | 로봇 OpenAPI 서버가 사용하는 HTTP 포트                                     |
| `command_port`         | int    | `8000`                          | 궤적 명령 전송을 위한 포트 번호                              |
| `command_start_time`   | float  | `-1.0`                          | 명령 실행 시간 (즉시 실행의 경우 -1.0)             |
| `command_buffer_size`  | int    | `5`                             | 명령 데이터 버퍼 크기                                 |
| `use_sim`                 | bool   | `false`                         | `gz_ros2_control/GazeboSimSystem` 플러그인을 사용하여 시뮬레이션 모드를 활성화하며, 일반적으로 Ignition Gazebo와의 통합에 사용됩니다<br>`use_sim_time` 매개변수도 true로 설정되어 시뮬레이션 시간과 동기화됩니다     |
| `use_mock_hardware`       | bool   | `false`                         | 로봇 없이 테스트하기 위해 `mock_components/GenericSystem`을 사용하는 mock 하드웨어 인터페이스를 활성화합니다   |
| `initial_positions_file`  | string | `""`                            | 초기 조인트 위치를 지정하는 선택적 YAML 파일                       |
| `controllers_config_package` | string | `"hdr_hardware_interface"`     | config YAML이 포함된 패키지 이름                                       |
| `controllers_file`        | string | `"default_controllers.yaml"`   | 제어기 구성 YAML 파일명                                     |
| `kinematics_file`         | string | `"default_kinematics.yaml"`    | 기구학 플러그인 구성 YAML 파일명                              |


#### 토픽

| 토픽 이름                   | 메시지 타입                   | 설명                               |
| ---------------------------- | ------------------------------ | ----------------------------------------- |
| `/joint_states`              | sensor_msgs::msg::JointState | position 정보를 포함한 현재 조인트 상태를 퍼블리시합니다 |
| `/controller_manager/status` | lifecycle_msgs::msg::State   | ros2_control 매니저의 라이프사이클 상태 |

#### 액션

| 액션 이름                                            | 액션 타입                                   | 설명                                |
| ------------------------------------------------------ | --------------------------------------------- | ------------------------------------------ |
| `/joint_trajectory_controller/follow_joint_trajectory` | control_msgs::action::FollowJointTrajectory | ROS2 action을 통해 조인트 궤적 명령을 실행합니다 |

#### 서비스

| 서비스 이름                                   | 서비스 타입                                         | 설명                         |
| ---------------------------------------------- | ---------------------------------------------------- | ----------------------------------- |
| `/controller_manager/list_controllers`         | controller_manager_msgs/srv/ListControllers        | 활성화된 controller 목록을 반환합니다     |
| `/controller_manager/list_hardware_interfaces` | controller_manager_msgs/srv/ListHardwareInterfaces | 사용 가능한 조인트 명령 및 상태 인터페이스를 반환합니다 |
| `/controller_manager/switch_controller`        | controller_manager_msgs/srv/SwitchController       | controller를 활성화하거나 비활성화합니다  |
| `/controller_manager/load_controller`          | controller_manager_msgs/srv/LoadController         | controller를 로드합니다             |
| `/controller_manager/unload_controller`        | controller_manager_msgs/srv/UnloadController       | 지정된 controller를 언로드하고 제거합니다    |

---

## 4. 문제 해결
- **제어기를 찾을 수 없음**: URDF의 플러그인 이름을 확인하고 다시 빌드하세요.
- **실행 시 타임아웃**: OpenAPI IP 주소가 host PC에서 접근 가능한지 확인하세요.
- **조인트 상태 없음**: 드라이버가 실행 중이고 `robot_pose` 기능이 활성화되어 있는지 확인하세요.
- **인터페이스 시작 실패**: 지원되는 펌웨어 버전 ≥ **60.34-00**인지 확인하세요. (이 버전은 **10월**에 릴리스 예정입니다.)