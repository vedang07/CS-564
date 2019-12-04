## COMP SCI 564: Database Management Systems: Design and Implementation

**Lecture-5**: September 16, 2019 <br/>

---

### **1\. Nested queries**:

```
select ...  ==> list of column expressions
                e.g. count (..), today() - st.dob

from ...    ==> list of table expressions
                e.g. table_1 join table_2 on (..)
```

---

### 2\. SQL queries

```
Q. Find students with atleast one F grade in a course
Ans. select st.id, st.name from student as st where exists (select * from enrollment as e where grade = "F" and e.stid = st.stid)

Q. Find students with who do not have F grade in any course
Ans.a. select st.id, st.name from student as st where not exists (select * from enrollment as e where grade = "F" and e.stid = st.stid)
Ans.b. select st.id, st.name from student as st where not in (select e.stid from enrollment where grade = "F")

Q. Students with all databases courses
Ans. select st.id, st.name from studentas st 
        where not exists (select * from course where title like "%database%" 
        and not exist (select * from enrollment as e where e.stid == st.id and c.no = e.no and c.dept = e.dept))
```


```
Other ways of writing nested queries:
    - with st as (select * from student where ...)
        select * from st where ...

    - create new st as (select ... from ... where ...)
```

```
Q. Calculate GPA of each student
Ans. select st.id, st.name, (select avg(grade) from enrollment as e where e.stid = st.stid) as gpa from student as st
```

---

### **3\. Clauses**: 
```
select
from
where
group by
order by
having    --------------> eg. having count(*) > 5 
                          eg. select stid from enrollment group by stid having count(*) > 5 (i.e student enrolled in more than 5 courses)
```

---

![](Clauses&#32;&&#32;relation&#32;algebra.png)

---

### **3\. Nested queries with joins**: 

```
Q. Find all students with grade A, AB and B

Ans. select e.stid, e.grade 
            from (select * from enrollment where grade in ("A", "AB", "B") as e right outer join students as st using (stid))

```

**Sample Output**:

| stid | dept |   no | grade | stid | name |  dob |
| ---- | ---- | ---- | ----- | ---- | ---- | ---- |
|   4  |  17  | 524  |   AB  |   4  |  Joe | 2013 |  
| null | null | null | null  |   7  | Josh | 2012 | 


---