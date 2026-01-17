# File API

## Overview

The File API category provides file system operations for the HD Hyundai Robotics controller. These APIs enable remote file management, file upload/download, and directory management.

## Available File APIs

| Function | Description |
|----------|-------------|
| `GetFiles` | Retrieve list of files and folders at specified path |
| `GetFileInfo` | Query metadata of file or directory (size, timestamp, type) |
| `GetFileList` | Retrieve filtered list including files only, directories only, or all |
| `GetFileExist` | Check existence of specified file or directory |
| `PostRenameFile` | Rename or move file or directory from one path to another |
| `PostMkdir` | Create new directory at specified path |
| `PostFiles` | Upload local file to specified location on controller |
| `PostDeleteFile` | Delete file or directory on controller |