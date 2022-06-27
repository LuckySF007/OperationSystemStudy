# 16강. cpu 스케줄링- 04

## Multiple-Processor Scheduling

CPU가 여러 개인 경우 스케줄링은 더욱 복잡해짐

- Homogeneous processor인 경우
    - Queue에 한줄로 세워서 각 프로세서가 알아서 꺼내가게 할 수 있다.
    - 반드시 특정 프로세서에서 수행되어야 하는 프로세스가 있는 경우에는 문제가 더 복잡해짐
- Load sharing
    - 일부 프로세서에 job이 몰리지 않도록 부하를 적절히 공유하는 메커니즘 필요
    - 별개의 큐를 두는 방법 vs 공동 큐를 두는 방법
- 대칭형 다중처리(Symmetric Multiprocessing)
    - 각CPU가 각자 알아서 스케줄링 결정
- 비대칭형 다중처리(Asymmetric Multiprocessing)
    - 하나의 CPU가 시스템 데이터의 접근과 공유를 책임지고 나머지 CPU는 거기에 따름
    

## Real-Time Scheduling

- Hard Real-Time Scheduling
    - 정해진 시간안에 무조건 끝내도록 스케줄링 해야함
- Soft Real-Time Scheduling
    - 일반 프로세스에 비해 높은 Priority를 가지도록 해야함
    

## Thread Scheduling

- local scheduling
    - User level thread의 경우 사용자 수준의 thread library에 의해 어떤 thread에 줄지 결정
- global scheduling
    - kernel level thread의 경우 일반 프로세스와 마찬가지로 커널의 단기 스케줄러가 어떤 thread를 스케줄링 할지 결정
    

## 스케줄링 알고리즘의 평가

- 큐잉 모델
    - 도착한 수식을 계산해서 어떤 알고리즘이 좋은지 판단
    - 이론적인 방법
- 구현 & 성능 측정
    - 실제 시스템에 알고리즘을 구현하여 실제 작업에 대해서 성능을 측정 비교
- 모의 실험(Simulation)
    - 알고리즘을 모의 프로그램으로 작성 후 **Trace**를 입력으로 하여 결과 비교