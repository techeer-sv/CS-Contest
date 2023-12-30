1. **대부분의 RDB는 B-Tree (또는 B+Tree)를 인덱스로 사용합니다. 왜 인덱스 자료구조로 트리를 선택했을까요? 또, 왜 RBT나 AVL Tree는 선택받지 못했을까요?**

- 답 : B-Tree/B+ Tree are much efficient when it becomes to sequential access. Searching data through the database required a lot of sequential read.

<br>

---
2. **레코드 수가 아주 많을 것으로 예상되는 대용량 테이블을 어떻게 설계할 것인지 설명해주세요. 또, 해당 테이블에서 어떻게 쿼리 최적화를 할 것인지 설명해주세요.**

- 답 : Partitioning and Indexing. Since the database will be partitioned into many smaller tables, query optimization should be done using efficient joins and efficient use of indexing.

<br>

---
3. **트랜잭션의 개념을 설명하고, ACID에 대해 최대한 자세히 설명해주세요.**

 - 답 : A transaction is a single atomic operation of one or more queries. Atomicity: all or nothing execution. Consistency: execution of a transaction leaves the DBMS and real world in the same state. Isolation: partial effects of a transaction are hidden from other transactions until committed. Durability: a successful transaction effects survives future system malfunctions.
   
    <br>
   
   3-1. **DB에서 직접 동시성을 제어하는 방법과 어플리케이션 레벨에서 동시성을 제어하는 방법이 무엇이 있는지 각각 설명하고, 두 방법을 비교해주세요.**

   - 답 : DB: Through locking.
         Application level: mutexes?

