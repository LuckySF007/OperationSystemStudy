## CPU-burst Time

- CPU-burst : 한 번 동안 CPU를 연속적으로 사용하는 시간

- CPU bound job : CPU를 오래 사용(계산 위주)
- I/O bound job : CPU보다 I/O를 더 오래 사용
  - CPU를 짧게 사용하기 때문에 잠깐만 CPU를 줘도 OK
  - 주로 사람과 상호작용을 하기 때문에 빠른 응답이 필요
  - CPU 스케줄링 시 우선 순위

## CPU Scheduler & Dispatcher

- CPU Scheduler
  - Ready 상태의 Process 중에서 이번에 CPU를 줄 Process를 고른다.
- Dispatcher
  - CPU의 제어권을 CPU scheduler에 의해 선택된 프로세스에게 넘긴다.(Context switch)
- CPU 스케줄링이 필요한 경우는 프로세스에게 다음과 같은 상태 변화가 있는 경우이다.

  - Running -> Blocked(예 : I/O 요청 시스템 콜)
  - Running -> Ready(예 : 할당시간만료 timer interrupt)
  - Blocked -> Ready(예 : I/O 완료 후 interrupt)
  - Terminate (종료)

- 위의 4가지 경우의 스케줄링은 nonpreemptive(강제로 빼앗지 않고 자진 반납)
- 나머지의 경우 preemptive(강제로 빼았음)

## Scheduling Criteria(성능 척도)

- CPU Utilization
- Throughput : 처리량
- Turnaround time(소요시간, 반환시간) : 기다린 모든 시간과 cpu 사용시간의 합
- Waiting time(대기 시간) : ready queue에서 기다린 시간의 총합
- Response time(응답 시간) : 최초로 cpu를 얻기 까지 걸리는 시간
