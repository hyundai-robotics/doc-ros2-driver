# 3.3 可用的操作

### 概述

ROS2 驱动程序提供了机器人关节轨迹控制的动作接口。动作允许异步操作，具有进度反馈和取消功能。

### 关节轨迹控制操作

#### `/joint_trajectory_controller/follow_joint_trajectory` (control_msgs/action/FollowJointTrajectory)

**描述**: 执行关节轨迹控制。

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
