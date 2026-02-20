# 7.1.5 I/O API

### 概述

I/O API 类别为 HD 现代机器人控制器提供 PLC 通信功能。这些 API 使能够查询和设置 Hi6、Hi7 PLC 中的继电器值。

### 可用的 I/O APIs

| 功能 | 描述 |
|----------|-------------|
| `GetRelayValue` | 使用 "FB{index}.{relay_type}" 格式或简单格式如 "M"、"S" 从 Hi6、Hi7 PLC 查询继电器值 |
| `SetRelayValue` | 在机器人控制器的内部 PLC 中设置特定继电器值。支持各种数据类型后缀 |