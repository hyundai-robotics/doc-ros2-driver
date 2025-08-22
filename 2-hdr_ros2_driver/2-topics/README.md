# 제공되는 토픽

## 개요

ROS2 드라이버는 표준화된 ROS2 토픽을 통해 실시간 로봇 데이터를 퍼블리시합니다. 이러한 토픽은 모니터링 및 제어 애플리케이션을 위한 조인트 상태, 로봇 상태 정보 및 진단 데이터를 제공합니다.

## publish되는 토픽

### 조인트 상태 정보

#### `/joint_states` (sensor_msgs/msg/JointState)
**설명**: 실시간 조인트 position 데이터

**메시지 필드**:
```yaml
std_msgs/Header header
  uint32 seq
  time stamp
  string frame_id
string[] name          # URDF와 일치하는 조인트 이름
float64[] position     # 라디안 단위의 조인트 position
float64[] velocity     # NULL
float64[] effort       # NULL
```

**퍼블리싱 주기**: 50 Hz (`publish_rate` 매개변수를 통해 구성 가능)


### 변환 정보

#### `/tf` 및 `/tf_static` (tf2_msgs/msg/TFMessage)
**설명**: 로봇 기구학 체인 변환

**퍼블리시되는 변환**:
- `base_link` → `link1` → `link2` → ... → `tool0`
- 로봇 장착 및 교정을 위한 정적 변환