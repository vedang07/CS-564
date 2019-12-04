## COMP SCI 564: Database Management Systems: Design and Implementation

**Lecture-14**: October 11, 2019 <br/>

---
```
Sample query:

SELECT x 
FROM large_table
GROUP BY x
HAVING count(distinct y) > 1 
```

```
1. Execution Plan:

      |
filter count>1
      |
in-stream aggregation count(distinct y)
      |
sort by x,y with duplicate removal
      |
scan large_table
```

```
2. A better execution plan:

      |
    filter
      |
hash aggregation by x
      |
hash distinct by y
      |
scan large table
```

---

```
3. Hack sample query:

SELECT x 
FROM large_table
GROUP BY x
HAVING count(distinct y) > 1 
<==> min(y) < max(y)
```

```
4. Hack execution plan:
      |
    filter
      |
sort by x with aggregation       (min(y), max(y))
      |
    scan
```

```
5. Better execution plan:
      |
    filter
      |
hash aggregate by x,            min(y), max(y)
      |
    scan
```

---
