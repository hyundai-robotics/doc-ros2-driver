# 1.5 机器人关节和连接件名称

HD现代机器人遵循以下URDF中的关节和连接件命名约定。

### 关节名称

|关节编号|关节名称 </br>(URDF)|关节名称 </br>(TP)|
|:------:|:---:|:---:|
|1|j1|S|
|2|j2|H|
|3|j3|V|
|4|j4|R2|
|5|j5|B|
|6|j6|R1|


### 连接件名称

|连接件编号|连接件名称|
|:------:|:---:|
|0|base_link|
|1|lower_frame_link|
|2|upper_frame_link|
|3|arm_link|
|4|wrist_body_link|
|5|wrist_holder_link|
|6|flange_link|


### 连接件关系

|连接件编号|连接件名称|关节|父连接件|关节类型|备注|
|:------:|:---:|:---:|:------:|:---:|:---:|
||世界||||||
|0|base_link|world_joint|世界|固定|||
|1|lower_frame_link|j1|base_link|旋转||
|2|upper_frame_link|j2|lower_frame_link|旋转||
|3|arm_link|j3|upper_frame_link|旋转||
|4|wrist_body_link|j4|arm_link|旋转||
|5|wrist_holder_link|j5|wrist_body_link|旋转||
|6|flange_link|j6|wrist_holder_link|旋转||
||flange|flange_link-flange|flange_link|固定|ROS工业标准坐标系|
||tool0|flange-tool0|flange|固定|ROS工业标准坐标系|