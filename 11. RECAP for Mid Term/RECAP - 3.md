## COMP SCI 564: Database Management Systems: Design and Implementation

**Lecture-19**: October 23, 2019 <br/>

**Topic**: Mid Term RECAP

**Exam time**: Friday to Friday

---

### **1\. RECAP for Mid Term**

```
Part - Lineitem - Order - Customer - Nation
       count>=5                     (France)

SELECT p_name, p_partkey
FROM part, lineitem, order, customer, nation
WHERE n_name = "France" AND p_partkey = l_partkey AND l_orderkey = o_orderkey AND o_orderkey = c_custkey AND c_nationkey = n_nationkey
GROUP BY p_partkey, p_name
having count(*) >= 5
```

![](Relational&#32;Algebra.png)

```
SELECT p_name, p_part_key
FROM part, (SELECT l_partkey, count(*) as ct
            FROM lineitem, orders, customer, nation
            WHERE ... (join clauses) and name = "France"
            GROUP BY l.partkey) as c
WHERE c.ct >=5 AND l.partkey = p.partkey

```

---
