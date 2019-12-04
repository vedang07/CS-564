## COMP SCI 564: Database Management Systems: Design and Implementation

**Lecture-4**: September 13, 2019 <br/>

---

### **1\. SQL Query for creating course table**: 

```
create table course (
    no int,
    dept varchar(30),
    office char(24),
    primary key (no, dept)
)
```

**Data types**: int, char(n), varchar(n), date, datetime, bool(??), money(??), numeric (n,m)

**Integrity Constraints** (in SQL): primary key, foreign key, unique, not null, check (value ...)

**Till Now**: Dept, Course, Enrollment and Student is covered

---

**Questions**:

```
Q.1. How many students are there with the name of Jane?
Ans. select count(*) as count_of_janes from student where name = "Jane"

Q.2. How many students with each distinct name?
Ans. Select count(*), name from student group by name;

TIP: Whichever column is there in group by clause, should also be there in select clause.

Q.3. List of names without duplicates
Ans3.1. select distinct name from student;
Ans3.2: select name from student group by name;

Q.4. How many distinct students we have in each department & its courses?
(x) Ans4.1. select e.dept, count(distinct e.id) from course as c join enrollment as e on (c.dept = e.dept and c.no and e.no) group by e.dept
(x) Ans4.2. select e.dept, count(distinct e.id) from course as c join enrollment as e using (dept, no) groupby e.dept
(x) Ans4.3. select e.dept, count(distinct e.id) from course as c join enrollment as e where c.dept = e.dept and c.no = e.no group by e.dept

(√) select e.dept, count(distince id) from enrollment as e groupby e.dept;

With department name: select d.name, d.dept, count(distinct e.id) from dept as d, enrollment as e where d.dept = e.dept group by d.dept, d.name; 

Q.5. For each department (and name), how many students do we teach?

Ans. Select d.dept, d.name, count(distince s.name) from from students as s, enrollment as e, course as c, dept as d where s.id = e.id and e.dept=c.dept and e.no=c.no and c.dept = de.dept group by d.dept, d.name
```
---
