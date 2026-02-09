# 7.1.1 Control API

### Overview

The Control API category provides basic robot control operations including motor management, coordinate system handling, and motion mode control. These APIs form the foundation for all robot operations.

### Available Control APIs

| Function | Description |
|----------|-------------|
| `GetControlOpCnd` | Retrieve robot controller's execution condition configuration (playback mode, step back maximum speed, user coordinate number) |
| `GetControlIosDio` | Read specific digital I/O signal values (supported types: "di", "dib", "diw", "dil", "dif", "do", "dob", "dow", "dol", "dof") |
| `GetControlIosSio` | Query special I/O (SIO) signal values (input types: "si", "sib" etc., output types: "so", "sob" etc.) |
| `GetControlUcsNos` | Retrieve list of available user coordinate system (UCS) numbers for motion programming |
| `PostControlIosDio` | Set digital output (DO) signal values (type, block number, signal number, value) |
| `PutControlOpCnd` | Update operation condition parameters (playback mode, reverse motion maximum speed, user coordinate system) |
