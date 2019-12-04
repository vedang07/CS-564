## COMP SCI 564: Database Management Systems: Design and Implementation

**Lecture-32**: December 04, 2019 <br/>

**Topic**: Data Analytics

---

### **1\. Data Analytics**

```
ETL (Extract Transform Load)

src         ---->       ETL         ---->       indexing
pos                                             statistics
web server                                      materialized view
                                                    - indexes
                                                    - "roll ups" = "group by" views
                                                |
                                                |
                                                |
                                                |
                                                |-----> reports
                                                |-----> dashboards
                                                |-----> alerts
                                                |-----> adhoc queries

```
```
Queries
    |---> traditional SQL: join, group by
    |---> Object Relational (OR) Mapping: deeply nested queries
    |---> window functions (SQL) ==> application: time series
    |---> "top" "limit" queries 

UDF: User Defined Functions
        |--> scalar
TVF: Table Valued Functions

R: stats, matrices, graphs
   ETL-light e.g. .csv
```

```
Jim Gray: 
    Syntax-1:
        SELECT City, County, State, Country, Sum(X)
        ...
        ...
        GROUP BY City, County, State, Country WITH Rollup


        City    |   |   |   |   |   | Country | Sum(X)  |
        -------------------------------------------------
        -         -   -   -   -   -     -         5         -------|
        -         -   -   -   -   -     -         7         -------|
        all       -   -   -   -   -     -        12         <------|
        .
        .                                                          |
        all      all  -   -   -   -     -        14         <------|
        .
        .                                                          |
        all     all all all all all    all     2,792        <------|
    
    Syntax-2:
        SELECT City, County, State, Country, Sum(X)
        ...
        ...
        GROUP BY City, County, State, Country WITH Cube
```
![](Cube.png)

---
