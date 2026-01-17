# 파일 관리 서비스

## 개요

`hdr_ros2_driver`에서 제공하는 파일 관리 관련 ROS2 서비스입니다.

## 파일 관리 서비스

### 파일 조회 및 정보

```bash
# 파일 내용 조회
ros2 service call /hdr_ros2_driver/file/get/files hdr_msgs/srv/FilePath "{path: 'project/jobs/0001.job'}"

# 디렉토리 내 파일 목록 조회
ros2 service call /hdr_ros2_driver/file/get/file_list hdr_msgs/srv/FileList "{path: 'project/jobs', incl_file: true, incl_dir: false}"

# 파일 정보 조회
ros2 service call /hdr_ros2_driver/file/get/file_info hdr_msgs/srv/FilePath "{path: 'project/jobs/0001.job'}"

# 파일 존재 여부 확인
ros2 service call /hdr_ros2_driver/file/get/file_exist hdr_msgs/srv/FilePath "{path: 'project/jobs/0001.job'}"
```

### 파일 조작

```bash
# 파일 업로드
ros2 service call /hdr_ros2_driver/file/post/files hdr_msgs/srv/FileSend "{target_file: 'project/jobs/test.job', source_file: '/home/test/test.job'}"

# 디렉토리 생성
ros2 service call /hdr_ros2_driver/file/post/mkdir hdr_msgs/srv/FilePath "{path: 'project/jobs/special'}"

# 파일 이름 변경
ros2 service call /hdr_ros2_driver/file/post/rename_file hdr_msgs/srv/FileRename "{pathname_from: 'project/jobs/0001.job', pathname_to: 'project/jobs/4321.job'}"

# 파일 삭제
ros2 service call /hdr_ros2_driver/file/delete/files hdr_msgs/srv/FilePath "{path: 'project/jobs/0001.job'}"
```