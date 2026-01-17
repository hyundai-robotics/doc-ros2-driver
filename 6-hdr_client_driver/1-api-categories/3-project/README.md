# Project API

## Overview

The Project API category provides project and job management functions for the HD Hyundai Robotics controller. These APIs enable monitoring project execution status, querying job information, and managing jobs.

## Available Project APIs

| Function | Description |
|----------|-------------|
| `GetProjectRgen` | Query current project execution status (0: not running, 1: running, 2: paused) |
| `GetProjectJobsInfo` | Retrieve metadata of all jobs registered in the project (name, path, modification status) |
| `PostProjectReloadUpdateJobs` | Reload and synchronize externally modified jobs to update in-memory job status |
| `PostProjectDeleteJob` | Delete specified job file from project path |