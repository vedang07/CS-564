## COMP SCI 564: Database Management Systems: Design and Implementation

**Lecture-10**: September 30, 2019 <br/>

---

### **1\. Query execution algorithms**

```
Selection & Projection --> scan file tables, storage structures

Q. How can we make scanning faster?
Ans. Couple of suggestions: 
        - cache, buffer pool
        - asynchronous I/O ~ read-ahead
        - large read

- sort and index
```

### **2. Primary Secondary Indexes**:

![](primary-secondary&#32;indexes.png)

### **3. Dealing with duplicates**:

```
Duplicate row removals: 
                - sort
                - distinct rows in runs
                - hash table = in-memory index
                    o if output size <= memory available
                - distribution sort on hash value (it will give equal distribution)

Grouping:
    - e.g. avg(grade) by student id
    - for execution of the query, we use same above algorithm, i.e. sort rows based on student id and,
      instead of removal of duplicates, we calculate average of grade for same course id

Algorithms:

- in-stream
- in-sort   -|->    distinct
- hash      -|      aggregation (grouping)
```

### **4. Dealing with Joins**

```
Join: student join enrollment using (stdid)

1. Naive nested loops:
    for each student
        for each enrollment             --|--> index search
            if (match) then output      --|         => index nested loops

2. Block nested loops:

3. F1 lookup join = block index nlj (NESTED LOOP JOIN)

Q. If we have an index on smaller/larger join/data out of two inputs?
Ans. NESTED LOOP JOIN

Q. What if we sort the input of 1st loop?
Ans. index search will become efficient 

Q. What if both inputs are sorted?
Ans. MERGE JOIN (unofficial name: poor man's merge join)

Q. Neither sorted nor indexed?
Ans. HASH JOIN

4. HASH JOIN:
    for each student                -| --> build phase
        insert into hash table      -|
    for each enrollment             -| --> probe phase
        insert into hash table      -|

```

---
