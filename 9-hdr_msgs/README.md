# 9. HD Hyundai Robotics ROS2 消息

### 概述

`hdr_msgs` 包定义了用于 HD Hyundai Robotics 软件栈的自定义 ROS2 消息类型。

### ROS2 消息

| 消息类型                | 描述                                                 |
|-----------------------|-------------------------------------------------------|
| `srv/DateTime.srv`    | 获取或设置机器人控制器的系统时间。输入包括完整的日期/时间字段（年、月、日、小时、分钟、秒）。 |
| `srv/Emergency.srv`   | 使用步骤参数（step_no, stop_at, stop_mode）测试紧急停止逻辑。用于仿真/测试场景。 |
| `srv/ExecuteCmd.srv`  | 作为字符串行列表执行控制台命令，具有可配置的执行间隔。对于原始低级命令如 rl.stop 很有用。 |
| `srv/ExecuteMove.srv` | 使用基于字符串的语句执行机器人移动命令。示例：“move L,spd=1sec,tool=1 [0, 0, 0, 0, 90, 0]”。 task_no标识任务索引（通常是 0）。 |
| `srv/FileList.srv`    | 查询机器人上的目录内容。可以通过布尔值过滤以包含文件或目录。 |
| `srv/FilePath.srv`    | 发送或查询文件路径以进行读取、删除或存在性检查等操作。 |
| `srv/FileRename.srv`  | 重命名或移动机器人控制器文件系统中的文件。 |
| `srv/FileSend.srv`    | 将文件从本地计算机上传到机器人控制器。需要源路径和目标路径。 |
| `srv/IoplcGet.srv`    | 读取 PLC 内存（例如，继电器、M、S、R）。支持直接寻址和基于名称的信号寻址。 |
| `srv/IoplcPost.srv`   | 使用符号名称如 M、S、R 或 FBx.y 写入 PLC 内存（继电器）。 |
| `srv/IoRequest.srv`   | 用于访问数字、串行或用户 I/O。类型字段指定 I/O 类型，如 'di'、'do'、'si' 或 'so'。 blk_no 和 sig_no 指定块和信号索引。“val” 字段在设置 I/O 值时使用，并在读取操作中忽略。 |
| `srv/JointTrajecotryPoints.srv` | 提供执行运动的轨迹点 |
| `srv/LogManager.srv`  | 使用类别（E、W 等）、ID 范围和时间戳过滤器查询日志条目。 |
| `srv/Number.srv`      | 通用服务，用于发送/接收整数。用于工具编号、坐标系统、索引设置等。 |
| `srv/OpCnd.srv`       | 读取或写入操作条件，如播放模式或用户坐标系统。 |
| `srv/PoseCur.srv`     | 根据内部配置获取当前机器人姿态（位置 + 定向），可在关节空间或工作空间中获取。 |
| `srv/ProgramCnt.srv`  | 设置程序执行指针（pno、sno、fno 等），以在任务逻辑中移动到特定位置。 |
| `srv/ProgramVar.srv`  | 读取或分配变量。可以指定范围（局部/全局）、表达式和持久性。 |