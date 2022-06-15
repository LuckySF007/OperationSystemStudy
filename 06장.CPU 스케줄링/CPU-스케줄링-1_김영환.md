# 운영체제 - CPU 스케줄링 1

> CPU burst  🔛  I/O burst

- CPU bound job, I/O bound Job이 섞여 있기 때문에 CPU 스케줄링은 대단히 중요하다.



## CPU-burst Time 분포

- 대체로 I/O bound job이 CPU를 받는 시간(burst duration)이 더 짧다.
  - I/O 작업은 일단 CPU를 길게 사용하지 않고, 사용자에게 직관적인 경험을 주기 위해 이렇게 한다.



## 프로세스 특성 분류

### I/O bound process

- CPU를 잡고 계산하는 시간보다 I/O에 많은 시간이 필요한 job
- many short CPU bursts

### CPU-burst process

- 계산 위주의 job
- few very long CPU bursts



## CPU Scheduler & Dispatcher

### CPU Scheduler

- Ready 상태의 프로세스 중에서 이번에 CPU를 줄 프로세스를 고른다.

### Dispatcher

- CPU의 제어권을 CPU Scheduler에 의해 선택된 프로세스에게 넘긴다.
- 이 과정을 **Context Switch**라고 한다.

### 스케줄링이 필요한 경우

1. **Running -> Blocked**
   - 예: I/O 요청하는 시스템 콜
2. **Running -> Ready**
   - 예: 할당시간 만료로 timer interrupt
3. **Blocked -> Ready**
   - 예: I/O 완료 후 인터럽트
4. **Terminate**

- 1, 4는 **nonpreemptive** (자진 반납)
- 다른 모든 스케줄링은 **preemptive** (강제로 빼앗음)



## 스케줄링 성능척도 Scheduling Criteria

- CPU utilization. **이용률**
  - 이용률이 높을수록 좋다.
- Throughput. **처리량**
  - 처리량이 많을수록 좋다.
- Turnaround time. **소요시간, 반환시간**
  - 'ready queue에서 기다린 시간 + CPU running 시간' 만큼의 값을 가진다. (CPU를 기다린 시간 + CPU를 사용한 시간)
  - 시간은 짧을수록 좋다.
- Waiting time. **대기시간**
  - CPU를 사용하러 와서 기다린 시간의 합(ready queue에서 줄 선 대기시간의 합)
  - 시간은 짧을수록 좋다.
- Response time. **응답시간**
  - I/O가 끝나고 CPU burst로 돌아와서 처음 응답까지 걸리는 시간
  - 시간은 짧을수록 좋다.
