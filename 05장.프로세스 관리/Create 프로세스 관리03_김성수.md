## 스케줄러(Sheduler)
- 운영체제 코드의 일부(스케줄링을 담당하는 기능의 일부를 표현)

- Long-term scheduler(장기 스케줄러 or job scheduler)
  - 시작 프로세스 중 어떤 것들을 ready queue에 올릴지 결정(New State -> Ready State로 변할 때 admit)
  - 프로세스를 Memory(및 각종자원 할당) 에 주는 문제
  - degree of Multiprogramming을 제어(Memory에 올라가 있는 프로그램 수)
  - Time sharing system에는 보통 장기 스케줄러가 없음(현대의 대부분의 OS가 이에 해당 대신 무조건 Ready 상태로 보냄)

- Short-tem scheduler(단기 스케줄러 or CPU scheduler)
  - 어떤 프로세스를 다음번에 running 시킬지 결정
  - 프로세스에 CPU를 주는 문제
  - 속도가 충분히 빨라야함(millisecond 단위) -> 가장 빈번하게 호출(timer interrupt가 발생할 때 마다)

- Medium-Term Scheduler(중기 스케줄러 or Swapper)
  - 여유 공간 마련을 위해 프로세스를 통째로 메모리에서 디스크로 쫓아냄
  - 프로세스에게 Memory를 뺏는 문제
  - degree of Multiprogramming을 제어

## Suspended(stopped)
- Medium-Term Scheduler에 의해 발생하는 프로세스의 상태(State)
- 외부적인 이유로 프로세스의 수행이 정지된 상태
- 프로세스는 통째로 디스크에서 swap out
  - 사용자가 프로그램을 일시 정지시킨 경우
  - 시스템이 여러가지 이유(예. 메모리에 너무 많은 프로세스가 올라와있을 때)로 인해 프로세스 중단

#### Blocked vs Suspended
Blocked : 프로세스가 실행중인 상태. 자신이 요청한 event가 만족되면 Ready 상태로 복귀
Suspended : 프로세스가 정지된 상태. 외부에서 resume해 주어야 Active
