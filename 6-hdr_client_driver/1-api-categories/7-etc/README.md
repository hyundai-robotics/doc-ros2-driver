# Miscellaneous API

## Overview

The Miscellaneous API category provides additional utility and system management functions for the HD Hyundai Robotics controller. These APIs include system time management and log query capabilities.

## Available Miscellaneous APIs

| Function | Description |
|----------|-------------|
| `GetDateTime` | Query current system date and time from robot controller (year, month, day, hour, minute, second) |
| `PutDateTime` | Set system date and time on robot controller (includes input validation) |
| `GetLogManager` | Query controller logs with filtering options (entry count, categories E,W,N,S,O,I,P,H,C,M, ID range, timestamp range) |