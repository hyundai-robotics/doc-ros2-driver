# 7.1.1 控制 API

### 概述

控制 API 类别提供基本的机器人控制操作，包括电机管理、坐标系统处理和运动模式控制。这些 API 形成所有机器人操作的基础。

### 可用的控制 API

| 功能 | 描述 |
|----------|-------------|
| `GetControlOpCnd` | 获取机器人控制器的执行条件配置（播放模式，退步最大速度，用户坐标号） |
| `GetControlIosDio` | 读取特定数字 I/O 信号值（支持类型：“di”，“dib”，“diw”，“dil”，“dif”，“do”，“dob”，“dow”，“dol”，“dof”） |
| `GetControlIosSio` | 查询特殊 I/O (SIO) 信号值（输入类型：“si”，“sib”等，输出类型：“so”，“sob”等） |
| `GetControlUcsNos` | 获取可用于运动编程的用户坐标系统 (UCS) 编号列表 |
| `PostControlIosDio` | 设置数字输出 (DO) 信号值（类型，块编号，信号编号，值） |
| `PutControlOpCnd` | 更新操作条件参数（播放模式，反向运动最大速度，用户坐标系统） |