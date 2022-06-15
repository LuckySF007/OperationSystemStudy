# 06장.CPU 스케줄링 - 01

## 사용자 프로그램 수행 과정은 CPU와 I/O 작업의 반복

- 일종의 사이클처럼 CPU와 I/O 장치를 번갈아 사용하며 프로그램 수행
- cpu 명령(cpu burst)은 빠른 명령인데 비해 I/O 작업(I/O burst)은 커널에 의해 입출력 작업을 진행하는 비교적 느린 단계

<br>

## CPU-burst Time의 분포

- cpu 바운드 프로세스 : I/O작업을 거의 수행하지 않아 cpu burst가 길게 나타나는 프로세스 (few very long cpu bursts), 계산 위주의 job
- I/O 바운드 프로세스 : I/O 요청이 빈번해 cpu burst가 짧게 나타나는 프로세스 (many short cpu bursts)
- 프로그램마다 cpu bust와 I/O burst가 차지하는 비율이 균일하지 않음 → cpu burst가 균일하지 않아 스케줄링 필요
- 여러 종류의 job(프로세스)이 섞여있기 때문에 CPU 스케줄링이 필요
- Interactive job에게 적절한 response 제공 요망
- CPU와 I/O 장치 등 시스템 자원을 골고루 효율적으로 사용
- cpu burst가 짧은 프로세스(I/O 바운드 프로세스)에게 우선적으로 cpu를 사용할 수 있도록 스케줄링 하는것이 효율적

<br>

## CPU Scheduler & Dispatcher

- cpu 스케줄러 : 준비 상태의 프로세스 중 어떤 프로세스에게 cpu를 할당할지 결정하는 os의 코드
    - cpu 스케줄링이 필요한 경우
        - Running → Blocked (ex. I/O 요청하는 시스템 콜)
        - Running → Ready (ex. 할당시간 만료로 타이머 인터럽트 발생)
        - Blocked → Ready (ex. I/O 완료 후 인터럽트 발생)
        - Terminate
    - 스케줄링 방식
        - 비선점형(nonpreemptive) 방식 : cpu를 획득한 프로세스가 cpu를 스스로 반납하기 전까지는 강제로 뺏기지 않는 방법
        - 선점형(preemptive) 방식 : 프로세스가 cpu를 계속 사용하고 싶어도 강제로 빼았는 방법
- 디스패처
    - context switch(문맥 교환) : cpu의 제어권을 cpu 스케줄러에 의해 선택된 프로세스에게 넘김

<br>

## 스케줄링의 성능 척도

- cpu 이용률(cpu utilization) : 전체 시간 중에서 cpu가 일한 시간의 비율 → 최대한 휴면 상태에 머무르지 않게 하는 것이 스케줄링의 중요한 목표
- 처리량(throughput) : 주어진 시간 동안 준비 큐에서 기다리고 있는 프로세스 중 몇개를 끝마쳤는지(cpu burst를 완료한 프로세스 개수) → 처리량이 많은 것이 스케줄링의 목표
- 소요시간, 반환시간(Turnaround time) : 프로세스가 cpu를 요청한 시점부터 자신이 원하는만큼 cpu를 다쓰고 cpu burst가 끝날때까지 걸린 시간 → 준비 큐에서 기다린 시간 + 실제로 cpu를 사용한 시간
- 대기 시간(waiting time) : cpu burst 기간 중 프로세스가 준비 큐에서 cpu를 얻기위해 기다린 시간의 합
- 응답 시간(response time) : 프로세스가 준비 큐에 들어온 후 첫번째 cpu를 얻을때까지 기다린 시간 → 타이머 인터럽트가 자주 발생할수록 응답시간 향상(대화형 시스템에 적합한 성능 척도)