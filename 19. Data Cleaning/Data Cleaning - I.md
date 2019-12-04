## COMP SCI 564: Database Management Systems: Design and Implementation

**Lecture-31**: December 02, 2019 <br/>

**Topic**: Data Cleaning

---

### **1\. Data Cleaning**

```
Related Terms: Wrangling

Data Cleaning Steps:
Step-0: Formats 
        e.g. .csv, .xls, .db
Step-1: Normalization and Correction 
        e.g. street address: 
                1210 W Dayton Street, ..., 53706
                1/1210 E Dayton Street 53706
            possible edits: 1210-1/1210, ..., 53706-53706, W-E
            least distant edit to correct: W-E
Step-2: Scaling
        e.g. currency
Step-3: Entity Matching
        e.g. Grafe-Prof. Graefe, Mr. Grafe, Goetz Graefe, Goetz Gråfe
        e.g. Schmitt, schmid, Schmidt
        e.g. John Smythe, J. Smith
Step-4: Randomization / anonymization
```
```
QnA:
--> ETL (Extract, Transform, Load)
```
---