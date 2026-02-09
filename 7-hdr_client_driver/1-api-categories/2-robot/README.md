# 7.1.2 Robot API

### Overview

The Robot API category handles core robot operations including motion control, position management, tool configuration, and safety systems. These APIs provide direct control over robot movement and status monitoring.

### Available Robot APIs

| Function | Description |
|----------|-------------|
| `GetRobotMotorState` | Check robot servo motor power status (ON/OFF), useful for checking motion command readiness |
| `GetRobotPoCur` | Current robot pose (position and orientation) with various options (job index, coordinate system, etc.) |
| `GetRobotCurTool` | Retrieve currently selected tool information (TCP configuration, weight, etc.) |
| `GetRobotTools` | Retrieve list of all tools registered in the system (TCP offsets, weights, etc.) |
| `GetRobotToolsT` | Query specific tool's detailed information by tool number (0-31) |
| `GetJointTrajBuffAvail` | Get the available size of the trajectory buffer |
| `PostRobotMotorPower` | Turn robot motor power ON or OFF |
| `PostRobotOperation` | Start or stop robot program execution |
| `PostRobotToolNo` | Set active tool number to use (0-31) |
| `PostRobotCrdSys` | Specify coordinate system to use for motion and I/O (-1: default, 0: base, 1: tool, 2: user1, 3: user2) |
| `PostRobotEmergencyStop` | Immediate emergency stop of all robot motion for safety response |
| `PostInitJointTrajectory` | Initialize the joint trajectory buffer |
| `PostInsertJointTrajectoryPoints` | Insert joint trajectory points into the controller buffer for motion execution |
