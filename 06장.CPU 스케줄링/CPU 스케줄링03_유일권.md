# 15강. cpu 스케줄링 - 03

## Multilevel Queue

- Ready Queue를 여러개로 분할
    - foreground(Interective)
    - background(Batch-no human interaction)
- 각 큐는 독립적인 스케줄링 알고리즘을 가짐
    - foreground : RR
    - background : FCFS
- 큐에 대한 스케줄링이 필요
    - Fixed priority scheduling
        - 모든 foreground를 처리하고, background를 처리한다.
        - Starvation(기아)의 우려가 있다.
    - Time Slice
        - 각 큐에 CPU Time을 적절한 비율로 할당

## Multilevel Feedback Queue

- 프로세스가 다른 큐로 이동 가능
- 에이징(aging)을 이와 같은 방식으로 구현할 수 있다.
- Mulitilevel-feedback-queue scheduler를 정의하는 파라미터들
    - Queue의 수
    - 각 큐의 scheduling algorithm
    - 프로세스를 상위 큐로 보내는 기준
    - 프로세스를 하위 큐로 내쫒는 기준
    - 프로세스가 CPU 서비스를 받으려 할 때 들어갈 큐를 결정하는 기준