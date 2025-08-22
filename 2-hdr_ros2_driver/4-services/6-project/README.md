# 프로젝트 관리 서비스

## 개요

`hdr_ros2_driver`에서 제공하는 프로젝트 및 작업 관리 관련 ROS2 서비스입니다.

## 프로젝트 관리 서비스

### 작업 정보

```bash
# 작업 정보 가져오기
ros2 service call /hdr_ros2_driver/project/get/jobs_info std_srvs/srv/Trigger

# 로봇 세대 정보 가져오기
ros2 service call /hdr_ros2_driver/project/get/rgen std_srvs/srv/Trigger
```

### 작업 조작

```bash
# 작업 삭제
ros2 service call /hdr_ros2_driver/project/post/delete_job hdr_msgs/srv/FilePath "{path: '0001.job'}"

# 업데이트된 작업 다시 로드
ros2 service call /hdr_ros2_driver/project/post/reload_updated_jobs std_srvs/srv/Trigger
```