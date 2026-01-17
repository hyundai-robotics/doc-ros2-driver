# 사용 가능한 action

## 개요

ROS2 드라이버는 로봇 joint trajectory 제어에 대한 action 인터페이스를 제공합니다. action은 진행 상황 피드백 및 취소 기능과 함께 비동기 작업을 가능하게 합니다.

## joint trajectory control action

### `/joint_trajectory_controller/follow_joint_trajectory` (control_msgs/action/FollowJointTrajectory)

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