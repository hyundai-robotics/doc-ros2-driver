# 로봇 API

## 개요

로봇 API 카테고리는 모션 제어, 위치 관리, 도구 구성 및 안전 시스템을 포함한 핵심 로봇 작업을 다룹니다. 이러한 API는 로봇 움직임에 대한 직접적인 제어와 상태 모니터링을 제공합니다.

## 사용 가능한 로봇 API

| 함수 | 설명 |
|------|------|
| `GetRobotMotorState` | 로봇 서보 모터 전원 상태 확인 (ON/OFF), 모션 명령 준비 상태 확인에 유용 |
| `GetRobotPoCur` | 현재 로봇 자세(위치 및 방향) 다양한 옵션 (작업 인덱스, 좌표계 등) |
| `GetRobotCurTool` | 현재 선택된 도구 정보 조회 (TCP 구성, 무게 등) |
| `GetRobotTools` | 시스템에 등록된 모든 도구 목록 조회 (TCP 오프셋, 무게 등) |
| `GetRobotToolsT` | 도구 번호(0-31)별 특정 도구의 상세 정보 조회 |
| `PostRobotMotorPower` | 로봇 모터 전원 ON 또는 OFF |
| `PostRobotOperation` | 로봇 프로그램 실행 시작 또는 중지 |
| `PostRobotToolNo` | 사용할 활성 도구 번호 설정 (0-31) |
| `PostRobotCrdSys` | 모션 및 I/O에 사용할 좌표계 지정 (-1: 기본값, 0: 베이스, 1: 도구, 2: 사용자1, 3: 사용자2) |
| `PostRobotEmergencyStop` | 안전 대응을 위해 모든 로봇 모션의 즉시 비상 정지 |