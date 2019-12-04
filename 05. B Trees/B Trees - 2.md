## COMP SCI 564: Database Management Systems: Design and Implementation

**Lecture-8**: September 23, 2019 

### 1\. **Binary Search**:

```
Advantages of above data structure: 
1. It is very fast.
   For e.g. for 1,000,000,000 (1 billion records), it can find a page in 30 tries (log(N)/log(2))
2. It is very efficient.
3. Easy insertion/deletion/update (Chances of free pages)
```

```
Q. How we can make the search more faster?
Ans. We cache the keys
```

It leads to the invention of B-Trees

---

### 2\. **B-Trees**

**Properties**:
```
1. Nodes of k to 2k entries (expected average = 70%)
2. Uniform depth (meaning: distance from root to leaf)
```

**B-Trees on**:
```
    - hash values
    - space filling courses
```
---