## COMP SCI 564: Database Management Systems: Design and Implementation

**Lecture-25**: November 13, 2019 <br/>

**Topic**: Key Value Stores

---

### **1\. RECAP**

```
What's special/different with KVS?
- no transactions (as compared to transactions in traditional databases)
- easier queries (as compared to SQL)
```

```
 a b ......... z
|---------------|
|---------------|
|               |
|---------------| --> scan rows
|---------------| stored as unit   [row ~~ record]
|               |

index e.g. b-trees

where predicate: a.x + a.y <= a.z => table scan

a.x = 5                => index

      a b ......... z
     |--------|-|----| -|
   |-|--------|-|----|  |-> z = 1 | same value multiple times in column => rum-length encoding
   | |        | |    | -|
|- | |--------|-|----| -|
|  | |--------|-|----|  |-> z = 2
|  |-|        | |    | -|
|             | |
|              |--> scan only columns
|--> zones e.g. 3MB/1col
|    min+max value
|--> e.g. sorted on order data ["zone maps"]
     min+min of ship data

[ (1) Hence, if we have to find such rows, where the predicate holds true, we have to scan through whole table to get results (if stored by rows) ]
[     But in column stores (KVL), we store as columns, it will be faster to check for which rows predicate holds true.                            ]
[     - It is advantages bcoz we will be scanning only a fraction of table                                                                        ]

(1) scan only needed columns
(2) dictionary compressoon
(3) rum-length encoding
    |--> leading sort columns &
    |--> dominant values

e.g. of one column store: vertica
Which product to buy: depends on data
```

### **2\. How to make search faster**

```
e.g. 
SELECT a,b,c,d,x,y,z
FROM T
WHERE x + y <= z

plan: predicate evaluation -----> fetch for "select"

1% of all rows  : row store => 200 rows/page    => table scan   -| for "select" clause
                  col store => 5000 values/page => column scans -| 


e.g. 
SELECT a,b,c,d,x,y,z
FROM T
WHERE x + y <= z AND r^2 < t^2

- late materialization (fetch as late as possible during query execution)
```

### **3\. ROS & WOS**

```
ROS: Read optimized store   => column format, on storage
WOS: Write optimized store  => row format, in memory if possible
```

---