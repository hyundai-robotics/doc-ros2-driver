# MoveIt2 구성 (`hdr_moveit_config`)

`hdr_moveit_config` 패키지는 실제 환경과 시뮬레이션 환경에서 HD현대로보틱스 로봇을 제어하기 위한 MoveIt2 구성 패키지를 제공합니다. 이 패키지는 SRDF 정의, 조인트 제한 및 제어기 설정을 포함한 로봇별 모션 플래닝 구성을 포함합니다.

## 주요 기능

- **로봇별 구성**: 지원되는 각 로봇 모델에 대한 개별 MoveIt2 설정
- **SRDF 정의**: 플래닝 그룹 및 자세가 포함된 의미적 로봇 기술서
- **조인트 제한 관리**: 안전한 작동을 위한 속도 및 가속도 스케일링
- **기구학 통합**: 순기구학/역기구학 솔버 구성
- **제어기 통합**: ros2_control 및 궤적 실행 설정

## 패키지 조직

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

## 구성 파일

각 로봇 구성에는 다음이 포함됩니다:

### 핵심 구성
- **SRDF 파일**: 플래닝 그룹이 포함된 의미적 로봇 기술서
- **joint_limits.yaml**: 스케일링 팩터가 있는 속도 및 가속도 제한
- **kinematics.yaml**: 기구학 솔버 플러그인 구성
- **controllers.yaml**: ros2_control 궤적 제어기 설정

### 고급 설정
- **ompl_planning.yaml**: OMPL 모션 플래너 구성
- **pilz_cartesian_limits.yaml**: Pilz 플래너용 직교 모션 제한
- **sensors_3d.yaml**: 3D 센서 통합 (해당하는 경우)
- **initial_positions.yaml**: 기본 시작 자세

## 안전 고려사항

### 속도 스케일링
안정적인 작동을 위해 **≤ 0.5**의 스케일링 팩터 사용을 권장합니다:

```yaml
default_velocity_scaling_factor: 0.5
default_acceleration_scaling_factor: 0.5
```

### 조인트 제한
`joint_limits.yaml` 파일은 다음을 정의합니다:
- 최대 조인트 속도
- 최대 조인트 가속도  
- 소프트웨어 위치 제한
- 모션 플래닝용 스케일링 팩터

## 실행

```bash
ros2 launch hdr_bringup hdr_moveit.launch.py robot_model:=ha006b
```

![hdr_moveit](../_assets/hdr_moveit.png)

## 플래닝 그룹

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


## 사용자 정의

모션 플래닝 동작을 수정하려면:
1. 속도/가속도 제한을 위해 `joint_limits.yaml` 편집 (URDF 상에 정의된 조인트 별 최대 속도 초과하여 적용 불가능)
2. 플래너별 설정을 위해 `ompl_planning.yaml` 수정
3. 새로운 플래닝 그룹 또는 자세를 위해 SRDF 업데이트
4. `controllers.yaml`에서 제어기 매개변수 조정