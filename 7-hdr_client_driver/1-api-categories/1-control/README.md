# 7.1.1 제어 API

### 개요

제어 API 카테고리는 모터 관리, 좌표계 처리 및 동작 모드 제어를 포함한 기본적인 로봇 제어 작업을 제공합니다. 이러한 API들은 모든 로봇 작업의 기초를 형성합니다.

### 사용 가능한 제어 API

| 함수 | 설명 |
|------|------|
| `GetControlOpCnd` | 로봇 제어기의 실행 조건 구성 조회 (재생 모드, 스텝 백 최대 속도, 사용자 좌표 번호) |
| `GetControlIosDio` | 특정 디지털 I/O 신호 값 읽기 (지원 유형: "di", "dib", "diw", "dil", "dif", "do", "dob", "dow", "dol", "dof") |
| `GetControlIosSio` | 특수 I/O (SIO) 신호 값 조회 (입력 유형: "si", "sib" 등, 출력 유형: "so", "sob" 등) |
| `GetControlUcsNos` | 모션 프로그래밍을 위한 사용 가능한 사용자 좌표계 (UCS) 번호 목록 조회 |
| `PostControlIosDio` | 디지털 출력(DO) 신호 값 설정 (유형, 블록 번호, 신호 번호, 값) |
| `PutControlOpCnd` | 동작 조건 매개변수 업데이트 (재생 모드, 역방향 모션 최대 속도, 사용자 좌표계) |
