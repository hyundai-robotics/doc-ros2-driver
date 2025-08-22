# 패키지 빌드 및 설치

이 가이드는 ROS2 작업공간 설정, 종속성 설치를 포함하여 HD현대로보틱스 ROS2 드라이버 패키지를 소스에서 빌드하는 방법을 다룹니다.

## 작업공간 설정

### ROS2 작업공간 생성

```bash
# 작업공간 디렉토리 생성
mkdir -p ~/hdr_ws/src
cd ~/hdr_ws

# 작업공간 초기화
echo "작업공간 생성 위치: $(pwd)"
```

### 소스 저장소 복제

```bash
cd ~/hdr_ws/src

# HDR 핵심 드라이버 및 client 라이브러리
git clone https://github.com/hyundai-robotics/hdr_ros2_driver.git
git clone https://github.com/hyundai-robotics/hdr_client_driver.git

# HDR description 패키지
git clone https://github.com/hyundai-robotics/hdr_description.git

# Gazebo 시뮬레이션
git clone https://github.com/hyundai-robotics/hdr_simulation_gz.git
```

## 종속성 설치

### ROS2 종속성 설치

```bash
cd ~/hdr_ws

# 패키지 데이터베이스 업데이트
rosdep update

# HDR 패키지의 모든 종속성 설치
rosdep install --from-paths src --ignore-src --rosdistro $ROS_DISTRO -y
```

## 빌드 프로세스

### 표준 빌드

```bash
cd ~/hdr_ws

# 최적화를 통해 모든 패키지 빌드
colcon build --symlink-install --cmake-args=-DCMAKE_BUILD_TYPE=Release
```

### 빌드 구성 옵션
```bash
# 디버그 기호와 함께 빌드
colcon build --symlink-install --cmake-args=-DCMAKE_BUILD_TYPE=Debug
```

### 환경 설정

```bash
cd ~/hdr_ws
source install/setup.bash

echo "source ~/hdr_ws/install/setup.bash" >> ~/.bashrc
```

## 다음 단계

패키지 빌드가 성공한 후:
1. 로봇 구성을 위한 [초기 설정](../3-initial-setup/README.md) 진행
2. [검증 테스트](../4-verifying/README.md)로 ROS2 드라이버 설치 및 세팅 상태 확인