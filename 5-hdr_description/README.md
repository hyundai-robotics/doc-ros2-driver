# 5. 로봇 URDF (`hdr_description`)

`hdr_description` 패키지는 ROS2에서 HD현대로보틱스 로봇을 위한 로봇 URDF, mesh, 시각화 구성을 포함합니다. 이 패키지는 시뮬레이션, 시각화, 모션 플래닝에 필요한 기본적인 URDF/XACRO 정의를 제공합니다.

[소스 코드] [hdr_description] [GitHub Repository ↗](https://github.com/hyundai-robotics/hdr_description)

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

모델별 세부사항은 [지원 로봇 모델](../1-intro/2-robot-models/README.md)을 참조하세요.
