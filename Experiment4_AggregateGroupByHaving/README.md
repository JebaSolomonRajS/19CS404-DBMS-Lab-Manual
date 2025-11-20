# Experiment 4: Aggregate Functions, Group By and Having Clause

## AIM
To study and implement aggregate functions, GROUP BY, and HAVING clause with suitable examples.

## THEORY

### Aggregate Functions
These perform calculations on a set of values and return a single value.

- **MIN()** – Smallest value  
- **MAX()** – Largest value  
- **COUNT()** – Number of rows  
- **SUM()** – Total of values  
- **AVG()** – Average of values

**Syntax:**
```sql
SELECT AGG_FUNC(column_name) FROM table_name WHERE condition;
```
### GROUP BY
Groups records with the same values in specified columns.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name;
```
### HAVING
Filters the grouped records based on aggregate conditions.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name
HAVING condition;
```

**Question 1**
<img width="768" height="662" alt="image" src="https://github.com/user-attachments/assets/3489df39-2bc5-48bd-b78e-6f84da8c3e1e" />


```sql
SELECT 
    DATE(AppointmentDateTime) AS AppointmentDate,
    COUNT(*) AS TotalAppointments
FROM Appointments
GROUP BY DATE(AppointmentDateTime)
ORDER BY AppointmentDate;
```

**Output:**

<img width="837" height="682" alt="image" src="https://github.com/user-attachments/assets/9cb2c044-cd55-4777-b7f4-f23c9fec1057" />


**Question 2**
---
<img width="1060" height="587" alt="image" src="https://github.com/user-attachments/assets/e0cb19db-3aa8-4e83-917b-59342226547f" />


```sql
SELECT 
    strftime('%Y-%m', Date) AS Month,
    COUNT(*) AS TotalRecords
FROM MedicalRecords
GROUP BY strftime('%Y-%m', Date)
ORDER BY Month;
```

**Output:**


<img width="845" height="507" alt="image" src="https://github.com/user-attachments/assets/79ccf751-8ac0-445b-9fa1-25ff58ec614d" />


**Question 3**
---

<img width="849" height="576" alt="image" src="https://github.com/user-attachments/assets/224949d6-b5ec-4a09-886c-0cbf47e9d645" />


```sql
SELECT 
    SUBSTR(ValidityPeriod, 1, 4) AS ValidityYear,
    COUNT(DISTINCT PatientID) AS TotalPatients
FROM Insurance
GROUP BY SUBSTR(ValidityPeriod, 1, 4);
```

**Output:**


<img width="835" height="439" alt="image" src="https://github.com/user-attachments/assets/004e9bad-9d75-4e53-9556-db8050678128" />


**Question 4**
---

<img width="850" height="492" alt="image" src="https://github.com/user-attachments/assets/32b6b23b-df3e-4f7f-a8a3-e06621bde463" />


```sql
SELECT name AS Employee_Name, age AS Age
FROM employee
ORDER BY age ASC
LIMIT 1;
```

**Output:**


<img width="843" height="385" alt="image" src="https://github.com/user-attachments/assets/f19fc39a-81e8-4ec0-bf04-1e285c92e198" />


**Question 5**
---

<img width="832" height="504" alt="image" src="https://github.com/user-attachments/assets/4564f8e7-a0ce-4f04-a7e3-29338b7512be" />


```sql
SELECT COUNT(DISTINCT salesman_id) AS COUNT
FROM orders;
```

**Output:**


<img width="854" height="363" alt="image" src="https://github.com/user-attachments/assets/0659346a-1c7f-418d-ac7e-507df67acfdb" />


**Question 6**
---

<img width="790" height="513" alt="image" src="https://github.com/user-attachments/assets/20bbd609-5b67-4fcf-8d23-09d6319c52e7" />


```sql
SELECT (MAX(age) - MIN(age)) AS age_difference
FROM employee;
```

**Output:**


<img width="837" height="364" alt="image" src="https://github.com/user-attachments/assets/088a70d1-2b80-44c9-839b-183d8d114b12" />


**Question 7**
---

<img width="856" height="649" alt="image" src="https://github.com/user-attachments/assets/ee48eb94-3a41-44ba-a02e-a920ee5e936b" />


```sql
SELECT SUM(inventory) AS total
FROM fruits
WHERE unit = 'LB';
```

**Output:**


<img width="850" height="374" alt="image" src="https://github.com/user-attachments/assets/4618b535-db1f-4f29-8b1b-dffed69d9ab5" />


**Question 8**
---

<img width="871" height="653" alt="image" src="https://github.com/user-attachments/assets/d6f69406-d681-41ba-9c0e-e7b1216a210a" />


```sql
SELECT occupation, MIN(workhour) AS "MIN(workhour)"
FROM employee1
GROUP BY occupation
HAVING MIN(workhour) > 8;
```

**Output:**


<img width="859" height="540" alt="image" src="https://github.com/user-attachments/assets/b4c3cf22-1166-4903-bfce-dbb095e8fe7d" />


**Question 9**
---

<img width="860" height="589" alt="image" src="https://github.com/user-attachments/assets/cc9404e6-ebff-4053-8a00-b89239d21fe7" />


```sql
SELECT age, MIN(income) AS "MIN(income)"
FROM employee
GROUP BY age
HAVING MIN(income) < 400000;
```

**Output:**


<img width="753" height="437" alt="image" src="https://github.com/user-attachments/assets/f52606af-b9e4-42a4-8e82-a2b157eaf3fe" />


**Question 10**
---

<img width="854" height="657" alt="image" src="https://github.com/user-attachments/assets/e6976cf9-f306-487a-8349-006b10e2a396" />


```sql
SELECT address, SUM(salary) AS "SUM(salary)"
FROM customer1
GROUP BY address
HAVING SUM(salary) > 2000;
```

**Output:**


<img width="863" height="545" alt="image" src="https://github.com/user-attachments/assets/e05c62b1-1b21-4f4a-aa06-de43de20caac" />



## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
