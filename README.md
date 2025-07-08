# 두산로보틱스 협동로봇 M0609 및 OnRobot RG2 운영

## 동작 종류
1. Pick and Place
    - 주요 함수
        | 함수 | 설명 |
        | --- | --- |
        | trans | ref 좌표계 기준으로 정의된 pos(포즈)를 동일 좌표계를 기준으로 delta만큼 이동/회전하여 ref_out 좌표계 기준으로 변환 후 반환 |
2. Gear 조립
    - 주요 함수
        | 함수 | 설명 |
        | --- | --- |
        | set_desired_force | 전역으로 설정된 좌표계(set_ref_coord() 참조) 기준으로 힘 제어 목표값, 힘 제어 방향, 힘 목표값, 외력참조모드 설정 |
        | amove_periodic | 비동기(async)방식의 move_periodic 모션 |
        | check_position_condition | 툴이 원하는 위치까지 내려왔는지 확인
3. Sports Cup Stacking
    - gripper 설정
        ![img1](https://github.com/idingg/cobot-operation/blob/main/images/gripper_rg2_config.png?raw=true)
    - 바닥 좌표 계산
        ![img2](https://github.com/idingg/cobot-operation/blob/main/images/pos_calc.png?raw=true)
    - 주요 함수
        | 함수 | 설명 |
        | --- | --- |
        | sorted() | 컵을 위쪽이 아닌 가로방향으로 잡기 때문에 그리퍼와의 충돌로 놓을 수 없는 자리가 발생하므로 sorted를 사용해 Y축 좌표가 큰 곳부터 컵을 배치 |
        | make_positions_ﬂoor(ﬂoor=1, ref=[0, 0, 0, 0, 0, 0]) → list(posx) | 층 수와 기준좌표를 인자로 받아 층 별 필요한 삼각형 좌표에 기준좌표 ref 를 trans한 좌표 리스트를 반환 |
        | split_cups(pos_start, pos_goal, total_num, pick_num) | 시작좌표에 있는 컵 뭉치 중 원하는 개수를 집어 목표좌표로 이동 |

### 개발 환경

- 로봇 프레임워크: <img src="https://img.shields.io/badge/ROS2-22314E?style=for-the-badge&logo=ros&logoColor=white">
- 프로그래밍 언어: <img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white">
- 하드웨어: <img src="https://img.shields.io/badge/Doosan robotics-005eb8?style=for-the-badge&logo=&logoColor=white"> <img src="https://img.shields.io/badge/onrobot-ffffff?style=for-the-badge&logo=&logoColor=white">

### 시연 영상
https://github.com/user-attachments/assets/9f9bc13b-12de-43a2-afb8-aeb6a982e137

https://github.com/user-attachments/assets/d3ec029d-2219-4b6c-ae60-f502c310ba01

https://github.com/user-attachments/assets/39be0614-fa09-4e8a-82c0-840b91c667c0
