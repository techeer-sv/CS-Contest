1. **멀티 프로세스와 멀티 스레드의 개념과 각각의 장단점을 설명해주세요.** 

- 답 : Multiprocess: Multiple processors for a job. (different memory)
        Pro: Isolation and Security
        Con: Resource overhead

    Multithread: multiple thread for a processor (Same memory)
        Pro: Resource efficiency, responsive
        Con: deadlock, security


    <br>
   
    1-1. **멀티 스레드 환경에서 스레드는 많으면 많을수록 좋을까요? 이유와 함께 답변해주세요.**

    - 답 : No. Too many threads can make the system too complex to manage and cause problems.

<br>

---
2. **컨텍스트 스위칭이란 무엇인지, 그리고 컨텍스트 스위칭으로 인한 문제가 무엇이 있는지 최대한 자세하게 설명해주세요.**

- 답 : Context switching is the act of switching contexts, allowing a single CPU to be used in multiple processes or threads. It can cause overhead, latency, and more power consumption. The problems are due to the time and resource used in "switching" the contexts.

<br>

---
3. **데드락에 대해 설명하고, 해결 방법을 아는대로 설명해주세요.**

- 답 : Deadlock is a situation where multiple processes are unable to proceed due to other resources waiting to free others' resources. It is in a state of circular waiting pattern.
It can be resolved by eliminating mutual exclusion, hold and wait, no preemptionm, or circular wait.