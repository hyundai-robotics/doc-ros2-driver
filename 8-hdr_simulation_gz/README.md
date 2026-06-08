# 8. Gazebo 시뮬레이션 (`hdr_simulation_gz`)

`hdr_simulation_gz` 패키지는 HD현대로보틱스 산업용 로봇을 위한 ROS2 + Gazebo (Ignition) 시뮬레이션 환경을 제공합니다. 이 패키지는 물리적 하드웨어 없이도 로봇 응용 프로그램의 개발, 테스트 및 검증을 가능하게 합니다.

[소스 코드] [hdr_simulation_gz] [GitHub Repository ↗](https://github.com/hyundai-robotics/hdr_simulation_gz)

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
