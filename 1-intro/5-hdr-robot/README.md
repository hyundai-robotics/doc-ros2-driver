# 1.5 로봇 joint 및 link 명칭

HD현대로보틱스 로봇은 URDF 내에서 아래와 같은 joint 및 link 명칭을 따릅니다.


### Joint 명

|joint no|joint name </br>(URDF)|joint name </br>(TP)|
|:------:|:---:|:---:|
|1|j1|S|
|2|j2|H|
|3|j3|V|
|4|j4|R2|
|5|j5|B|
|6|j6|R1|


### Link 명

|link No|link Name|
|:------:|:---:|
|0|base_link|
|1|lower_frame_link|
|2|upper_frame_link|
|3|arm_link|
|4|wrist_body_link|
|5|wrist_holder_link|
|6|flange_link|


### Link 간 관계

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
||flange|flange_link-flange|flange_link|fixed|ROS-Industrial 표준 좌표계|
||tool0|flange-tool0|flange|fixed|ROS-Industrial 표준 좌표계|
