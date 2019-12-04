## COMP SCI 564: Database Management Systems: Design and Implementation

**Lecture-20**: October 28, 2019 <br/>

**Topic**: Transactions

---

```
HINT 1:
same phone number and same number, it is good idea to create an id
as a result, some queries will become easier 

HINT 2:
If you are using LIMIT and TOP for "recent time a book was borowwed", do not use it. Find an appropriate aggrgate function

HINT 3:
Pattron: member of customer of library 
Borrower: who borrows
```

### **1\. Transactions**

```
RECAP Transaction Properties:
     - Atomicity: all or nothing
     - Consistency: 
     - Isolation: like single user, one transaction at a time (Concurrency Control)
     - Durability: fire, flood and insurrection (Logging and Recovery)
```

![](Write&#32;ahead&#32;logging.png)
![](System&#32;failure.png)

```
Logging and Recovery:
     - Write ahead logging
     - Failure classes:
          o txn failure
               - Transaction Manager: List of active transactions
                    o most recent log record ==> linked list 
                OR  o list of all log records
               - CAUSES:
                    o Deadlock
                    o Lack of resources (lack of memory)
                    o User abort request 
               - We assume system is working fine
          o system failure
               - T1, T2 and T4 are winner transactions and will be persisted and durable
               - T3 and T5 are failure transactions and will not be persisted and durable
               - Buffer Manager: list of dirty pages (at checkpoint log analysis)
                    o we apply all the changes for T2, T3, T4 and T5
               - CAUSES:
                    o DB/OS software crash
               - We assume hardware and media are working fine
          o media failure (storage media)
               - CASUSE:
                    o storage failure
               - We assume software & process & memory is fine
     - Write ahead logging and compensation log records (Sample recovery log record below:- )
          Begin transaction
          Update page 7, slot 9: ...
          Update page 4, slot 6: ...
          Rollback
          Rollback
          Commit (nothing)
     - Another recovery log example: (check pdf)
```

---
