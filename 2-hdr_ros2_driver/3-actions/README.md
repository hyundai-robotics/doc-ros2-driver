# Available Actions

## Overview

The ROS2 driver provides action interfaces for robot joint trajectory control. Actions enable asynchronous operations with progress feedback and cancellation capabilities.

## Joint Trajectory Control Action

### `/joint_trajectory_controller/follow_joint_trajectory` (control_msgs/action/FollowJointTrajectory)

**Description**: Executes joint trajectory control.

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