## COMP SCI 564: Database Management Systems: Design and Implementation

**Lecture-21**: October 30, 2019 <br/>

**Topic**: Transactions

---

### **1\. Write ahead log**

```
    - LOG: any & all changes in the persistent DB
    - WRITE AHEAD: log first, modify the DB
    - STABLE STORAGE: mirroring
```

### 2\. How to recover from Transaction failure?

```
    - Which of the 3 (or combination) failures has occurred
        o Transaction Failure: Rollback the transaction
        o scan this transaction's log records, log the rollback, update back
        o Page Log Sequence Number (Page LSN): in page header, most recent change in the page
            - LSN is nothing but byte address within the log file (tradional model)
```
![](txns&#32;recovery.png)

### 3\. System Failure
```
    - memory
    + rec log
    + database (slightly out of date)
    - incomplete transactions
```

### 4\. How to recover from system failure? How does restart happens?
```
    - log analysis + redo + undo
      |----------|   |----------|
          |               |- DB contents
          |- checkpoint log record

        o LOG ANALYSIS: 
            - checkpoint log record            
                o active transactions, most recent log record (LSN)
                o dirty pages in buffer pool (Page LSN in buffer pool)
```

---