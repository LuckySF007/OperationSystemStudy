# 

# CPU Scheduling 03

### Round robin

- 대기 시간이 해당 job이 사용하려는 시간에 비례하는 경향이 있음

### Multilevel Queue

- Ready queue를 여러 개로 분할(Queue에 우선순위를 둔다. // 각 queue는 독립적인 스케줄링 알고리즘을 가짐.
- foreground - interactive한 job - RR
- background(batch (no human interaction) - FCFS
- Queue 에 대한 Scheduling 필요
    - Fixed priority scheduling : 모든 foreground job이 처리된 후에 background job 처리
    - background queue에 대해 Starvation 가능성이 있음
- 각 큐에 CPU time을 적절한 비율로 할당. ex) 80% foreground // 20% background

### Multilevel Feedback Queue

- process가 queue간 이동이 가능함.
- aging을 이와 같은 방식으로 구현할 수 있다.
- Multilevel Feedback Queue를 정의하는 파라미터.
    - Queue의 수
    - 각 큐의 scheduling algorithm
    - process를 상위 큐로 보내는 기준, 하위 큐로 보내는 기준
    - 프로세스가 cpu 서비스를 받으려 할 때 들어갈 큐를 결정하는 기준
    

### Multiple-Processor Scheduling(CPU가 여러 개인 경우)

- Homogeneous processor인 경우
    - Queue에 한 줄로 세워 각 프로세서(CPU)가 알아서 꺼내가게 함.
    - 반드시 특정 프로세서에서 수행되어야 하는 프로세스가 있는 경우 문제가 복잡해짐.
- Load sharing
    - 일부 프로세서에 job이 몰리지 않도록 부하를 적절히 공유하는 메커니즘 필요
    - 프로세서(CPU)마다 별개의 큐를 두는 방법 vs 공동 큐를 사용하는 방법
- Symmetric Multiprocessing(SMP)
    - 각 프로세서가 각자 알아서 스케줄링 결정
    - 모든 프로세서의 지위가 동등.
- Asymmetric multiprocessing
    - 하나의 프로세서가 시스템 데이터의 접근과 공유를 책임지고 나머지 프로세서는 거기에 따름

### Real-Time Scheduling(주어진 Deadline 안에 꼭 처리가 되어 야함)

- Hard real-time systems  :  Hard real-time task 주어진 시간 안에 반드시 처리 되어 야함.
- Soft real-time systems : 일반 process에 비해 높은 우선순위를 가짐.

### Thread Scheduling

- Local Scheduling
    - User level thread의 경우 사용자 수준의 thread libaray에 의해 어떤 thread를 스케줄 할지 결정.(process 내부에서)
    - 운영체제는 user thread의 존재를 모름.
- Global Scheduling
    - Kernel level thread의 경우 일반 프로세스와 마찬 가지로 커널의 단기 스케줄러가 어떤 thread를 스케줄 할지 결정

### Algorithm Evaluation

- Queueing models
    - 확률 분포로 주어지는 arrival rate(도착률)와 service rate(처리율)등을 통해 각종 performance index값을 계산
- Implementation(구현) & Measurement(성능 측정)
    - 실제 시스템에 알고리즘을 구현하여 실제 작업에 대해서 성능을 측정 비교
- Simulation(모의 실험)
    - 알고리즘을 모의 프로그램으로 작성 후 trace를 입력으로 하여 결과 비교