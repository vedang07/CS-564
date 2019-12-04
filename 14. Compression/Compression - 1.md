## COMP SCI 564: Database Management Systems: Design and Implementation

**Lecture-24**: November 8, 2019 <br/>

**Topic**: Compression

---

### **1\. RECAP**

```
- Sharing structured data:
    o schema, metadata
    o transactions, ACID, Concurrency Control, Locks, Log, Recovery
    o Physical data independence

- What all we have discussed?                                        level of abstractions               
    o SQL: create table, select                                             |   
    o Query Optimization: relational algebra                                |
    o Query Execution: sorting, join algorithms, query execution plan       |
    o Indexes, Btrees                                                       |
    o Transactions                                                          |
    o Hardware                                                              v  (higher abstraction)
```

### **2\. Compression**
```
0) Jerry    5   two complete records
   Jerry    9

==> Techniques:
1) Dictionery encoding      "Michael"   47
2) Prefix truncate              ++ compression
    0 Jerry\0 5                 -- linear search
    6         9
3) distinct key-value + list    ++ compressions
              |-------|         ++ binary search 
   e.g. Jerry | 5 | 9 |
              |-------|

4) Numeric Deltas within sorted lists
   e.g. Michael     392     1234567890, 1234565882
                                             +2008

5) BitMap for dense sets

e.g. 
   |-------------------------------|
   | 0 0 0 1 1 0 0 1 1 0 0 1 0 0 1 |
   |-------------------------------|
     ^
     |
1234567890
```

### **3\. Index structures**

```
B-Trees - Sorted, Range queries

Hash Index - access spread
             uniformly distribution, hash value sets
             tree of hash tables ??

B-Tree on hash values using interpolation search
```

### **4\. Key Value Stores ~~ No SQL**

```
- put (key, value)
- get (key) --> value

++ concurrency control, recovery
-- transactions, physical data independence

++ scalability & performance
```
---
