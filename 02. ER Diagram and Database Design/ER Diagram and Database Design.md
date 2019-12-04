## COMP SCI 564: Database Management Systems: Design and Implementation

**Lecture-2**: September 9, 2019 <br/>

---

### **1\. Example of objects in university:**

```
Students 
Courses
Events, eg graduation
Enrollment
Professors, other faculty
Building
Grade
Classrooms
Mascot (university may not track this)
Passwords
Jobs
Library
Resources
```

---

### **2\. What does university stores about about Students?**

```
Student-id
Major
Name
List of classes with grade, credit, term
GPA
```

---

### **3\. Entity Relationship diagram:**

![](ER&#32;diagram.png)

---

```
Q. How Information is stored?
Ans. In form of tables (rows and columns).
```

### **4\. Representation of Objects in table:**

**Student**:

| ID | Gender | First Name | Middle Name | Family Name |
| -- |:------:| :---------:|:-----------:|:-----------:|
| -- | ------ | ---------- | ----------- | ----------- |

```
ID => Primary Key
```

---

**Course**:

| Dept  | Course No |    Title   |     Room    |     Time    | Lecture Employee ID  |
| ----- |:---------:| :---------:|:-----------:|:-----------:| :-------------------:|                    
| ----- | --------- | ---------- | ----------- | ----------- | ---------------------|

```
Dept and Course No => Primary Key
Lecture Employee ID => Forign Key
```

---

**Enrollment**:

| Grade | Stu. Id  | Course No.  | Course Dept.  | Term |
| ----- |:--------:| :----------:|:------------: |:----:|
| ----- | -------- | ----------- | ------------- | ---- |

```
Stu. Id => Foreign Key
Course No. and Course Dept. => Foreign Key
Stu. Id and Course No., Course Dept. and Term => Primary Key
```

---

**Lectures**:

| Emp. ID |  Name  | 
| ------- |:------:|
| ------- | ------ |

---

### **5\. Functional Dependency**

```
Functional Dependency is
    - Multiple values are functionally dependent on single value (e.g. In Student table, all values are dependent on Stu. ID)
    - Multiple values are functionally dependent dependent on multiple values (In Enrollment table, all values are dependent on Stu. Id and Course No., Course Dept. and Term) 
```

---