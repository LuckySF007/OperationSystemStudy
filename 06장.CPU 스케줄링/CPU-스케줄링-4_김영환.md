# 운영체제 - CPU 스케줄링 4

## Multiple-Processor Scheduling

- CPU가 여러 개인 경우
  - 스케줄링은 더욱 복잡해진다.

### Homogeneous processor인 경우

- 큐에 한 줄로 세워서 각 프로세서가 알아서 꺼내가게 할 수 있다.
- 반드시 특정 프로세서에서 수행되어야 하는 경우, 문제가 복잡해진다.

### Load sharing

- 일부 프로세서에 job이 몰리지 않도록 부하를 적절히 공유하는 메커니즘이 필요
  - 별개의 큐를 두는 방법
  - 공동 큐를 두는 방법

### Symmetric Multiprocessing (SMP)

- 각 프로세서가 각자 알아서 스케줄링 결정
- 모든 프로세서가 대등하게 일한다. (대장 CPU가 없음)

### Asymmetric multiprocessing

- 하나의 프로세서가 시스템 데이터의 접근, 공유를 책임진다. 나머지 프로세서는 거기에 따른다.



## Real-Time Scheduling

### Hard real-time systems

- 정해진 시간 안에 반드시 끝내야 한다.

### Soft real-time computing

- 데드라인을 어긴다고 아주 큰 일이 나는 것은 아니지만 웬만하면 지켜야 한다.
  - 동영상 스트리밍 중 끊기는 것처럼 불편함을 초래할 수도 있다.
- 일반 프로세스에 비해 높은 priority를 갖도록 해야 한다.



## Thread Scheduling

### Local Scheduling

- 유저 레벨 스레드의 경우 사용자 수준의 스레드 라이브러리에 의해 어떤 스레드를 스케줄할지 결정한다.

### Global Scheduling

- 커널 레벨 스레드의 경우 일반 프로세스와 마찬가지로 커널의 단기 스케줄러가 어떤 스레드를 스케줄할지 결정한다.



## Algorithm Evaluation

### Queueing models

- 확률 분포로 주어지는 arrival rate와 service rate 등을 통해 각종 performance index 값을 계산한다.
- 과거에 많이 사용했다.

### Implementation & Measurement

- 실제 시스템에 알고리즘을 구현, 실제 작업에 대해 성능을 측정해 비교한다.
- 요즘에 많이 사용한다.

### Simulation

- 알고리즘을 모의 프로그램으로 작성 후 trace(simulation의 input 데이터)를 입력으로 하여 결과를 비교한다.
- 두 번째 방법이 너무 어렵기 때문에 가상으로 돌려보는 방법이다.

