# 7.1.5 I/O API

### Overview

The I/O API category provides PLC communication functions for the HD Hyundai Robotics controller. These APIs enable querying and setting relay values in the Hi6, Hi7 PLC.

### Available I/O APIs

| Function | Description |
|----------|-------------|
| `GetRelayValue` | Query relay values from Hi6, Hi7 PLC using "FB{index}.{relay_type}" format or simple formats like "M", "S" |
| `SetRelayValue` | Set specific relay values in the robot controller's internal PLC. Supports various data type suffixes |
