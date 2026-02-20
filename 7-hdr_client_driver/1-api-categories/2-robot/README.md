# 7.1.2 机器人 API

### 概述

机器人 API 类别处理核心机器人操作，包括运动控制、位置管理、工具配置和安全系统。这些 API 提供对机器人运动和状态监控的直接控制。

### 可用的机器人 API

| 函数 | 描述 |
|----------|-------------|
| `GetRobotMotorState` | 检查机器人伺服电机电源状态（开启/关闭），用于检查运动命令准备就绪情况 |
| `GetRobotPoCur` | 当前机器人姿态（位置和方向），配有各种选项（任务索引、坐标系统等） |
| `GetRobotCurTool` | 检索当前选择的工具信息（TCP 配置、重量等） |
| `GetRobotTools` | 检索系统中注册的所有工具列表（TCP 偏移、重量等） |
| `GetRobotToolsT` | 通过工具编号（0-31）查询特定工具的详细信息 |
| `GetJointTrajBuffAvail` | 获取可用轨迹缓冲区的大小 |
| `PostRobotMotorPower` | 打开或关闭机器人电机电源 |
| `PostRobotOperation` | 启动或停止机器人程序执行 |
| `PostRobotToolNo` | 设置使用的活动工具编号（0-31） |
| `PostRobotCrdSys` | 指定用于运动和 I/O 的坐标系统（-1：默认，0：基座，1：工具，2：用户1，3：用户2） |
| `PostRobotEmergencyStop` | 立即停止所有机器人的运动以响应安全措施 |
| `PostInitJointTrajectory` | 初始化关节轨迹缓冲区 |
| `PostInsertJointTrajectoryPoints` | 将关节轨迹点插入控制器缓冲区以进行运动执行 |