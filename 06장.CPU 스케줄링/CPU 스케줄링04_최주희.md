# 06장.CPU 스케줄링 - 04

## Multiple-Processor Scheduling

- cpu가 여러개인 경우 스케줄링은 더욱 복잡해짐
- 특정 cpu에서 수행되어야하는 프로세스가 있는 경우
    - 큐에서 한줄로 세워서 각 프로세서가 알아서 꺼내가게 할 수 있음
    - 문제가 더욱 복잡
- Load sharing
    - 일부 프로세서에 job이 몰리지 않도록 부하를 적절히 공유하는 메커니즘 필요
    - 별개의 큐를 두는 방법 vs 공동 큐를 사용하는 방법
- Symmetric Multiprocessing (대칭형 다중처리) : 각 프로세서가 각자 알아서 스케줄링 결정
- Asymmetric Multiprocessing (비대칭형 다중처리) : 하나의 cpu가 다른 모든 cpu의 스케줄링 및 데이터 접근을 책임지고 나머지 cpu는 거기에 따라 움직이는 방식

<br>

## Real-Time Scheduling

- 실시간 시스템에서는 각 작업마다 주어진 데드라인 안에 반드시 작업을 처리해야함
- Hard Real-Time 시스템 : 데드라인을 정확히 지켜야 하는 시스템 (ex.미사일 발사, 원자로 제어)
- Soft Real-Time 시스템 : 데드라인을 정확히 지키지 못했다고 해서 위험한 상황이 발생하지는 않음 (ex.멀티미디어 스트리밍)
- 먼저 온 요청보다는 데드라인이 얼마 남지 않은 요청을 먼저 처리하는 스케줄링을 널리 사용

<br>

## 스케줄링 알고리즘 성능 평가 방법

- Queueing models : 확률 분포로 주어지는 도착률과 처리율을 통해 각종 성능 지표 계산
- Implementation & Measurement : 실제 시스템에 알고리즘을 구현하여 실제 작업(workload)에 대해서 성능을 측정 비교
- Simulation : 알고리즘을 모의 프로그램으로 작성 후 cpu 요청을 입력으로 하여 결과 비교 (입력값은 가상으로 생성 or 실제 시스템에서 cpu 요청 내역(trace)을 추출해 사용)