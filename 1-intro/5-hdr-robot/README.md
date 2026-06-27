# 1.5 机器人关节和连杆名称

HD Hyundai Robotics 机器人遵循如下所示的 URDF 中的关节和连杆命名约定。


### 关节名称

|joint no|joint name </br>(URDF)|joint name </br>(TP)|
|:------:|:---:|:---:|
|1|j1|S|
|2|j2|H|
|3|j3|V|
|4|j4|R2|
|5|j5|B|
|6|j6|R1|


### 连杆名称

|link No|link Name|
|:------:|:---:|
|0|base_link|
|1|lower_frame_link|
|2|upper_frame_link|
|3|arm_link|
|4|wrist_body_link|
|5|wrist_holder_link|
|6|flange_link|


### 连杆关系

|link No|link Name|joint|parent link|joint type|note|
|:------:|:---:|:---:|:------:|:---:|:---:|
||world||||||
|0|base_link|world_joint|world|fixed|||
|1|lower_frame_link|j1|base_link|revolute||
|2|upper_frame_link|j2|lower_frame_link|revolute||
|3|arm_link|j3|upper_frame_link|revolute||
|4|wrist_body_link|j4|arm_link|revolute||
|5|wrist_holder_link|j5|wrist_body_link|revolute||
|6|flange_link|j6|wrist_holder_link|revolute||
||flange|flange_link-flange|flange_link|fixed|ROS-Industrial 标准坐标系|
||tool0|flange-tool0|flange|fixed|ROS-Industrial 标准坐标系|