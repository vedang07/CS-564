## COMP SCI 564: Database Management Systems: Design and Implementation

**Lecture-17**: October 18, 2019 <br/>

**Topic**: Mid Term RECAP

---

### **1\. RECAP for Mid Term**

```
SQL parser + binder
query compiler + optimizer
query execution
storage structures e.g. b-tree
storage devices
```

```
sharing structured data
    |--> time, apps, users
    |--> schemas, catelogs, "data about data" = metdata
    |--> physical data independence (e.g. a user writing query need not know about indexes and 
         whether it exists or not, it does not affect the creation of query, 
         though it can affect the processing time, which does not impact the user much)
    |--> transactions (multiple actions indivisible: atomic)
    |--> Transaction Properties: ACID
         |--> A = Atomic: "all or nothing" - failure automicity
         |--> C = Consistency: Integrity constraints are met
         |--> I = Isolation: concurrency control, locking - "illusion of single user access" --> Locks: shared, exclusive 
         |--> D = Durability: "fire, flood, insurrection"                                          |       |--> cannot read or write
                                                                                                   |--> can read, cannot write
```                                                                                                 

---
