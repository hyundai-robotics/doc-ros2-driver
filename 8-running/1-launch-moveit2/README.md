# MoveIt2로 실행하기

## 개요

HD현대로보틱스 로봇을 MoveIt2로 실행하는 기본 절차입니다.

## 실행 전 준비사항

### 하드웨어 준비
- 로봇 제어기 전원 켜고 REMOTE 모드 설정
- 비상 정지 버튼이 접근 가능한 위치에 있는지 확인
- 네트워크 연결 확인 (ping 192.168.1.150)
- 작업 공간에 장애물이 없는지 확인

### 소프트웨어 준비
- ROS2 환경 설정: `source ~/ros2_ws/install/setup.bash`
- 로봇 모델 확인

## 기본 실행 절차

### 1. MoveIt2 실행
```bash
# 기본 MoveIt2 실행
ros2 launch hdr_moveit_config hdr_moveit.launch.py robot_model:=ha006b

# IP 주소 지정해서 실행  
ros2 launch hdr_moveit_config hdr_moveit.launch.py \
    robot_model:=ha006b \
    robot_ip:=192.168.1.150
```

### 2. 연결 상태 확인
```bash
# 조인트 상태 확인
ros2 topic echo /joint_states --once

# MoveIt2 서비스 확인
ros2 service list | grep move_group
```

## 지원되는 로봇 모델

- ha006b
- hdf7_9
- hdf8_8
- hdr50_22
- hdr220_26
- hh020

## 안전 주의사항

### 비상 정지
- 하드웨어 비상 정지 버튼을 항상 접근 가능한 곳에 두세요

### 안전한 종료
1. 모든 동작 정지
2. 로봇을 안전 위치로 이동
3. MoveIt2 노드 종료
4. 로봇 제어기 전원 끄기

## 일반적인 문제 해결

### 연결 문제
- 네트워크 연결 확인: `ping 192.168.1.150`
- 로봇 제어기가 REMOTE 모드인지 확인

### 계획 실패
- 목표 위치가 작업 영역 내에 있는지 확인
- 충돌 검사 설정 확인
- 조인트 한계값 확인

### 실행 문제
- 로봇이 비상 정지 상태가 아닌지 확인
- 제어기 오류 상태 확인
- ROS2 토픽 연결 상태 확인