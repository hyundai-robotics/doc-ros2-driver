# 9. HD Hyundai Robotics ROS2 Messages

### Overview

The `hdr_msgs` package defines custom ROS2 message types used in the HD Hyundai Robotics software stack.


### ROS2 Messages

| Message Type          | Description                                           |
|-----------------------|-------------------------------------------------------|
| `srv/DateTime.srv`    | Gets or sets the system time of the robot controller. Input includes full date/time fields (year, mon, day, hour, min, sec). |
| `srv/Emergency.srv`   | Tests emergency stop logic using step parameters (step_no, stop_at, stop_mode). Used for simulation/testing scenarios. |
| `srv/ExecuteCmd.srv`  | Executes console commands as a list of string lines with configurable execution intervals. Useful for raw low-level commands like rl.stop. |
| `srv/ExecuteMove.srv` | Executes robot movement commands using string-based statements. Example: "move L,spd=1sec,tool=1 [0, 0, 0, 0, 90, 0]". task_no identifies the task index (typically 0). |
| `srv/FileList.srv`    | Queries directory contents on the robot. Can filter to include files or directories through boolean values. |
| `srv/FilePath.srv`    | Sends or queries file paths for operations like reading, deletion, or existence checking. |
| `srv/FileRename.srv`  | Renames or moves files in the robot controller's file system. |
| `srv/FileSend.srv`    | Uploads files from local PC to robot controller. Requires source and destination paths. |
| `srv/IoplcGet.srv`    | Reads PLC memory (e.g., relays, M, S, R). Supports both direct addressing and name-based signal addressing. |
| `srv/IoplcPost.srv`   | Writes to PLC memory (relays) using symbolic names such as M, S, R, or FBx.y. |
| `srv/IoRequest.srv`   | Used to access digital, serial, or user I/O. The type field specifies I/O kind like 'di', 'do', 'si', or 'so'. blk_no and sig_no specify block and signal indices. The 'val' field is used when setting I/O values and ignored during read operations. |
| `srv/JointTrajecotryPoints.srv` | Provides trajectory points for executing motion |
| `srv/LogManager.srv`  | Queries log entries using category (E, W, etc.), ID ranges, and timestamp filters. |
| `srv/Number.srv`      | General-purpose service for sending/receiving integers. Used for tool numbers, coordinate systems, index settings, etc. |
| `srv/OpCnd.srv`       | Reads or writes operating conditions such as playback mode or user coordinate systems. |
| `srv/PoseCur.srv`     | Gets current robot pose (position + orientation) in joint space or workspace according to internal configuration. |
| `srv/ProgramCnt.srv`  | Sets program execution pointer (pno, sno, fno, etc.) to move to specific positions in task logic. |
| `srv/ProgramVar.srv`  | Reads or assigns variables. Can specify scope (local/global), expressions, and persistence. |
