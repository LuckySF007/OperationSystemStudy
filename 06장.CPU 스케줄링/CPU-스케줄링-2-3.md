---
layout: post
title: "[OS] 운영체제 - CPU 스케줄링 2, 3"
subtitle: "운영체제와 정보기술의 원리"
categories: [Study, 운영체제]
tags: [운영체제, Study, 운영체제와 정보기술의 원리]
comments: true
header-img:
typora-root-url: ../
---

# 운영체제 - CPU 스케줄링 2, 3

## 스케줄링 알고리즘

### FCFS (First-Come First-Served)

- 먼저 들어온 것을 먼저 처리한다.
- CPU 스케줄링에서는 매우 비효율적인 방식이다.
- Convoy effect : 긴 시간의 프로세스 뒤에 짧은 시간의 프로세스가 위치하는 현상(매우 오래 기다려야 함)

### SJF (Shortest Job First)

- 각 프로세스의 다음 번 CPU burst time을 스케줄링에 활용하는 방식이다.
- 가장 짧은 프로세스를 제일 먼저 스케줄링 한다.
- 두 가지 방식이 존재한다.
  - NonPreemptive
    - CPU를 잡으면 해당 순차의 CPU burst가 완료될 때까지 CPU를 선점당하지 않는다.
  - Preemptive
    - 현재 수행중인 프로세스의 남은 burst time보다 더 짧은 CPU burst time을 가지는 새로운 프로세스가 도착 시 CPU를 선점당한다.
    - SRTF (Shortest-Remaining-Time-First)라고도 부른다.
- 주어진 프로세스들에 대해 Minimum Average Waiting Time을 보장한다.
- 치명적인 약점
  - Starvation
    - 너무 효율성만 생각해 짧은 프로세스부터 처리하다보니, 긴 프로세스들은 영원히 처리되지 못할 수도 있게 되었다.
  - 다음 번 CPU burst time을 예측하기 어렵다.
    - 해당 순차에서 다음 번 CPU burst time을 미리 알고 스케줄링 하는 것은 불가능하다.
    - 미리 알 수 없기에, 그 대안으로 과거 CPU burst time들을 이용해 추정한 값을 사용할 수 있다.

### Priority Scheduling

- highest priority를 가진 프로세스에게 CPU를 할당한다.
- 두 가지 방식이 존재한다.
  - NonPreemptive
    - 우선 순위가 더 높은 프로세스가 들어와도 선점당하지 않는다.
  - Preemptive
    - 우선 순위가 더 높은 프로세스가 도착 시 선점당한다.
- SJF도 일종의 priority schduling이라 할 수 있다.(우선순서 = 다음 CPU burst 예측 시간)
- 약점
  - Starvation
    - 우선 순위가 낮은 프로세스는 영원히 실행이 안 될 수가 있다.
  - 해결책
    - Aging : 시간에 따라 프로세스의 우선 순위를 증가시켜준다.

### Round Robin (RR)

- 각 프로세스는 동일한 크기의 할당 시간(time quantum)을 가진다.
- 할당 시간이 지나면 CPU 선점을 빼앗긴다. 선점당한 후 Ready Queue의 제일 뒤에 가서 다시 줄을 선다.
- Ready Queue에 N개의 프로세스가 존재하고 할당 시간이 Q인 경우, 어떤 프로세스도 `(N-1) * Q` 이상 기다리지 않는다.
- Performance
  - Q가 크면 : FCFS
  - Q가 작으면 : context switch가 너무 자주 일어나 오버헤드가 커진다.
  - 일반적으로 SJF보다 average turnaround time이 길지만 response time은 더 짧다.

### Multilevel Queue

- Ready Queue를 여러 개로 분할
  - foreground (interactive)
  - background (batch - no human interaction)
- 각 큐는 독립적인 스케줄링 알고리즘을 가진다.
  - foreground - RR
  - background - FCFS
- 큐에 대한 스케줄링 필요
  - foreground에 완전한 우선순위를 부여
    - background의 starvation이 발생할 수 있다.
  - Time slice
    - 각 큐에 CPU time을 적절한 비율로 할당한다.
    - background의 starvation 문제를 해결할 수 있다.
    - 예를 들어 80%는 foreground의 RR에, 20%는 background의 FCFS에 할당

### Multilevel Feedback Queue

- multilevel queue와 달리 프로세스가 다른 Ready Queue를 옮겨다니는 것이 가능하다.
- Aging과 같은 방식을 통해 우선순위가 낮은 큐도 실행될 수 있도록 할 수 있다.
