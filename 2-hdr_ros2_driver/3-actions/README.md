# 사용 가능한 action

## 개요

ROS2 드라이버는 로봇 궤적 실행에 대한 action 인터페이스를 제공합니다. action은 진행 상황 피드백 및 취소 기능과 함께 비동기 작업을 가능하게 합니다.

## 궤적 실행 action

### `/follow_joint_trajectory` (control_msgs/action/FollowJointTrajectory)

**설명**: 조인트 공간 궤적을 실행합니다

**목표 필드**:
```yaml
trajectory_msgs/JointTrajectory trajectory
  std_msgs/Header header
  string[] joint_names
  JointTrajectoryPoint[] points
    float64[] positions
    float64[] velocities  
    float64[] accelerations
    float64[] effort
    builtin_interfaces/Duration time_from_start
path_tolerance[] goal_tolerance
  string name
  float64 position
  float64 velocity  
  float64 acceleration
builtin_interfaces/Duration goal_time_tolerance
```

**피드백 필드**:
```yaml
std_msgs/Header header
string[] joint_names
trajectory_msgs/JointTrajectoryPoint desired
trajectory_msgs/JointTrajectoryPoint actual  
trajectory_msgs/JointTrajectoryPoint error
```

**결과 필드**:
```yaml
int32 error_code
string error_string
```