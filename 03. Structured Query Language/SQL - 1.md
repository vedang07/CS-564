## COMP SCI 564: Database Management Systems: Design and Implementation

**Lecture-3**: September 11, 2019 <br/>

---

### **1\. Objects and respective tables**

![](Student&#32;Object.png)

---

**Student Table**:              

|  ID  | Name |                      
| ---- | ---- |            
| 1324 | Jane |             
| 5561 | John |             

```
ID => primary key           
```

**Student.address**:

|  ID  | Type   |   City    | Street |  
| ---- | ------ | --------- | ------ |
| 1324 | home   | Barbados  |  Main  |     
| 1324 | remote | Madison   |  Park  |

```
ID and type => primary keys
```

---

## **2\. SQL queries**

**Create query: student**
```
create table student (
    id integer primary key,
    name varchar (35)
)
```

**Insert query: student Jane**
```
Insert into student values(1324, "Jane")
```

**Create query: student.address**
```
create table student,address (
    id integer,
    type varchar (8), check (value in ("home", "work", "remote")),
    city varchar (50) not null,
    street varchar (50),
    primary key (id, type) on delete cascade
    foreign key (id) references student on update cascade
)
```

**Delete query: student with id 1324**
```
delete from student where id = 1324
```

**Update query: student with id 1324**
```
update students set id = 9935 where id = 1324
```

**Select query: find id with student name Jane**
```
select id from student where name = "Jane"
```

**Select query: find city and street of student with student id 1324 and type home**
```
select city, street from student.address where id = 1324 and type = "home"
```

**Select query: find Jane's student id city and street in descending order**
```
select sa.city, sa.street, s.id from student as s, student.address as sa 
    where name = "Jane" and  s.id = sa.id
    order by sa.city, sa.street desc
```

---

### **3\. Relational Algebra**

![](ralational&#32;algebra.png)

---

### 4\. More SQL queries

**Count: number of Janes**
```
select count(*) as number_of_janes from student where name = "Jane"
```

**Output**:

| number_of_janes |
| --------------- |
|        1        |


**Count: number of Janes address**
```
select count(*) as count_of_janes from student as s join student.address as sa on (s.id = sa.id)
    where s.name = "Jane"
```

**Output**:

|  count_of_janes |
| --------------- |
|        2        |

**Count: number of Janes with student ID**
```
select s.id, count(*) as count_of_janes from student as s join student.address as sa on (s.id = sa.id)
    where s.name = "Jane"
    group by s.id
```

**Output**:

|  id  | count_of_janes |
| ---- | -------------- |
| 1324 |       2        |

---
