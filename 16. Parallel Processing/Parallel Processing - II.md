## COMP SCI 564: Database Management Systems: Design and Implementation

**Lecture-28**: November 20, 2019 <br/>

**Topic**: Parallel Processing

---

### **1\. RECAP**

```
Query processing:
    - Pipelining: also called vertical parallelization
    - Partitioning: horizontal parallelization
        o load imbalance

Transaction processing:
    - concurrency control
    - data partitioning

Distributed transaction: two phase commit
    - use  co-ordinator            participant
        |--> query update    ---->
                             <----
        
        |--> please commit   (vote to commit)
             (don't abort)   ---->
                             (yes) : "I will do what you say"
                             <----
                             (no)
                             <----
                             (decision commit by record)
                             ---->
    - If all participants say yes, make a decision to commit, and orders everyone to "commit!"
    - During a reboot of a participant after a "yes", participant comes back up and recovers to the point it said "yes"
    - In two phase commit, 2 phases are:
        o everyone agrees to commit
        o everyone actually commits
    - Two phase commit is super expensive (cockroach DB do the same)
```

### **2\. Reliability**
```
    - Redundancy
        o mirroring
        o log shipping
    - Recovery algorithms
```

### **3\. Cloud Computing**
```
    - Principal motivation: economy of scale 
                            (surplus equipment)
        o virtualization (vendor: VMWare)
            - utilization
            - migration (load management)
    
    Web tier        : manage logging, shhopping basket, cookies
    Data management : relational database, key value store 
    Storage         : file system, 

3 tier architecture data center might have central services as follows:
- networking
- monitoring
- ACL service: Access control list
.
.
.


```
```
Data management tier
    e.g. cloud AWS Aurora - uses "log shipping to storage"
```
---
