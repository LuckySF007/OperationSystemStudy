# CPU 스케줄링 02

## CPU Scheduling Algorithm

### FCFS(First-Come First-Served)

- non-preemptive
- 먼저 온 프로세스가 먼저 CPU를 사용(선착순)
- 프로세스가 순서에 따라 average wait time의 편차가 심하다.
- Convoy effect : burst time 이 짧은 process의 순서가 burst time 이 긴 process 뒤의 순서일 경우 매우 오래 기다려야 하는 상황

### SJF(Shortest-Job-First)

- 대기 시간 측면에서는 optimal 하다. (minimum average waiting time을 보장)
- CPU burst time이 가장 짧은 프로세스를 제일 먼저 스케줄
- Non-preemtive : 일단 CPU를 잡으면 이번 CPU burst가 완료될 때까지 CPU를 preemption 당하지 않음
- Preemptive : 현재 수행중인 프로세스의 남은 burst time보다 더 짧은 CPU burst time을 가지는 프로세스가 도착하면 CPU를 빼았김. 이 방법을 Shortest-Remaining-Time-First(SRTF)이라고도 부름.
- Preemptive가 더 optimal한 방법
- Starvation : 효율성만 생각 하다 보니 Long Cpu burst time을 가진 process는 영원히 CPU를 얻지 못할 수도 있음.
- Queue에 들어오는 시점에 Cpu burst time을 알 수 없다. 과거를 통해서 추정(estimate)!
- 추정 = T_(n+1) = a*T_n + (1-a)T_n  ⇒ n+1번째를 예측하고 싶다면 n번째의 이미 알고 있는 값을 가중치를 두어 예측 (오래된 예측보다 최근의 예측을 더 많이 반영함) (exponential averaging)

### Priority Scheduling

- 우선 순위가 높은 프로세스에게 cpu를 할당
- smallest integer = highest priority
- preemptive, nonpreemptive 두 가지로 구현 가능
- SJF는 일종의 Priority scheduling이다.(우선순위가 Cpu burst time 에 해당)
- Starvation 문제를 동일하게 지니고 있음
- Aging을 통해 해결(시간이 지날수록 우선순위를 증가시킴)

### Round Robin

- 각 프로세스는 동일한 크기의 할당 시간(time quantum)을 가짐. 통상적으로 10-100 millisecond.
- 보통 I/O bound job은 한번에 처리해서 나가고 CPU bound job은 여러 번 할당된다.(이 범위 안에 할당 시간이 적당함.)
- 할당 시간이 지나면 프로세스는 preempted 당하고 ready queue의 제일 뒤에 가서 줄을 다시 선다.
- 할당 시간이 너무 긴 경우 → FCFS // 할당 시간이 너무 짧은 경우 → Context switch 오버 헤드가 크다.
- 일반적으로 SJF에 비해 Average Turnaround time은 길지만 Response time(첫 번째로  CPU를 얻기 까지의 대기 시간)이 짧다. → Interacive한 환경에서 응답 시간은 매우 중요. (짧은 job 긴 job이 섞여있을 때 효과적임)