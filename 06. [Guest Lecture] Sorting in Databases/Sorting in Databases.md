## COMP SCI 564: Database Management Systems: Design and Implementation

**Guest Lecturer**: Thanh Do

**Lecture-9**: September 25, 2019 <br/>

**Sorting in databases**

**Father of algorithms**: Donald E. Knuth

---
```
Q. How do max. people sort in C++? </br>
Ans. std::sort()
```
---

**Agenda**:
```
1. Use-cases of sorting in data processing
2. In-memory sort - run generation
3. External merge sort
4. Parallel sort
```

---

**1\. Use-cases of sorting**

```
- index creation
- searching
- database operations
```

---

**2\. Algorithms for in-memory sort**

```
- quick sort (Comment: most commonly used (std::sort))
- priority sort 
- tree of loser (see donald knuth, the art of computer programming, volume 3) (Comment: by far the most efficient in my experience)
```

---

**3\. Quick Sort**

```
- Worst Case: When data is already sorted => O(n^2) 
```

**4\. Tree of loser**

```

- loser stays at bottom and winner moves up

```

**5\. External merge sort**

```
- not everything fits in main memory

Solution: 
    o sort in parts => produces n parts (each sorted)
    o take n sorted parts and sort it completely 
        - example:
            5, 4, 4, 3, 2, 1, 1 --|     |----|
                                  |     |1, 1|
                                  | --> |    | --> 0, 1, 1, 1, 2, 2, 3, 3, 4, 4, 4, 5, 6, 6
                                  |     |1, 0|
            6, 6, 4, 3, 2, 1, 0 --|     |----|
                                      fan-in = 4
    We sort parts which fit in memory
    and we sort everything by sorting sorted parts (by loading partially)
```

**6\.** Merge strategies

```
1. 

-----------  -|
-----------   |
-----------   |    --|
-----------  -|      |  => bad strategy
-----------  --    --|

-----------  -|
-----------  -|    --|
-----------  --      |
-----------  --      |  => good strategy
-----------  --    --|

constraint, fan-in = 4

2. 

-----------
----------
-------
----    --| => sort two shorted => good strategy
--      --|

```

**7\. Graceful degradation in external merge sort**

```
Example: 
    Input size: 1,010 records
    Output size: 1,000 records

Q.   How much many records to be written to disk for sorting?
Ans. Typical anser 1,010 (i.e. we spill the entrie input)

Solution: Spill as to disk as much needed. Optimal strategy: spill only 10 records
```

**8\. Distributed Sort**:

```
Problem: How to search a very large amount of data that cannot fit in one machine?

Solution: shuffle data suring sort: many to one exchange

eg.

Sorted stream:   |----------------------------------------------------|

Unsorted stream: |----------------------------------------------------|

Solution:

==> 1-way of doing:

Sorted stream:   |----------------------------------------------------|
                                             |
                                             |
                                           Merge
                                             |
                       ------------------------------------------------ 
                       |             |               |                |
                     Sort          Sort            Sort             Sort
                       |             |               |                |
Unsorted stream: |-----------| |------------| |-------------| |----------------|


==> Better way of sorting:


Sorted stream:   |--------------------------|  |------------------------|
                          |                                      |
                          |                                      |
                        Merge                                  Merge
                          |                                      |
                          |          |--------------------------------|                           
                       |-------------|---------------|                | 
                       |             |               |                |
                     Sort          Sort            Sort             Sort
                       |             |               |                |
Unsorted stream: |-----------| |------------| |-------------| |----------------|

Shuffle data before sort

```

**Other topis**:

```
1. Double buffering in external merge sort (see cow book
2. Normalized keys, offset-value code (see Goetz's computing paper))
3. Distributed sort in real world (MapReduce, Presto, Hadoop, ...)
```

**Note**: Slide is available for this content

---
