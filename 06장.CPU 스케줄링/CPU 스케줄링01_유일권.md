# 13강. cpu 스케줄링 - 01

## CPU Burst, I/O Burst

- CPU Burst : CPU를 한번 점유했을때 사용하는 시간
- I/O Burst : I/O를 사용하는 시간

## CPU Scheduler & Dispatcher

- **CPU Scheduling이 필요한 이유**
    - 여러 종류의 process가 섞여 있기 때문에 CPU 스케줄링이 필요하다.
    - I/O 작업 같은경우 Interactive job이기 때문에 적절한 response를 제공해야한다.
    - CPU와 I/O 장치 등 시스템 자원을 골고루 효율적으로 사용해야 한다.
- CPU scheduler
    - Ready 상태의 프로세스 중에서 이번에 CPU에 줄 프로세스를 고른다.
- CPU Dispatcher
    - CPU의 제어권을 CPU scheduler에 의해 선택된 프로세스에게 넘긴다.
    - 이 과정을 context switch라고 한다.
- CPU 스케줄링이 필요한 경우는 프로세스에게 다음과 같은 상태 변화가 있는 경우이다.
    1. Running -> Blocked(예 : I/O 요청 시스템 콜)
    2. Running -> Ready(예 : 할당시간만료 timer interrupt)
    3. Blocked -> Ready(예 : I/O 완료 후 interrupt)
    4. Terminate (종료)
    
    위 1~4의 스케줄링은 nonpreemptive(강제가 아니라 자진 반납)
    
    나머지 스케줄링은 모두 preemptive(강제 반납)
    

## Scheduling Criteria(성능 척도)

스케줄링을 하기위하여 프로세스들의 우선순의 등을 정하기 위한 자료들

- CPU utilization(이용률) : 전체 시간중 CPU가 놀지않고 일한 시간의 비율
- Throughput : 단위 시간당 처리량
- Turnaround time(소요시간, 반환시간) : 기다린 모든 시간과 cpu 사용시간의 모든 합
- Waiting time(대기 시간) : Ready Queue에서 기다린 시간의 합
- Response time(응답 시간) : 최초로 cpu를 얻기 까지 걸리는 시간