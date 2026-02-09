# 7.1.6 Task API

### Overview

The Task API category provides task execution and variable management functions for the HD Hyundai Robotics controller. These APIs enable variable assignment, wait state release, program counter control, expression evaluation, and direct motion command execution.

### Available Task APIs

| Function | Description |
|----------|-------------|
| `PostAssignVar` | Assign variables to task using expressions or JSON values (supports local/global scope and persistence) |
| `PostReleaseWait` | Release task[0] from WAIT state to resume paused task |
| `PostSetCurPcIdx` | Manually set program counter (PC) index for task[0] (useful for debugging or jumping to specific logic) |
| `PostSolveExpr` | Evaluate expressions within task scope (supports math, logic, and variable access) |
| `PostExecuteMove` | Execute direct movement commands in robot task (L, P, SP, etc.) |
