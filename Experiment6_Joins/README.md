# Experiment 6: Joins

## AIM
To study and implement different types of joins.

## THEORY

SQL Joins are used to combine records from two or more tables based on a related column.

### 1. INNER JOIN
Returns records with matching values in both tables.

**Syntax:**
```sql
SELECT columns
FROM table1
INNER JOIN table2
ON table1.column = table2.column;
```

### 2. LEFT JOIN
Returns all records from the left table, and matched records from the right.

**Syntax:**

```sql
SELECT columns
FROM table1
LEFT JOIN table2
ON table1.column = table2.column;
```
### 3. RIGHT JOIN
Returns all records from the right table, and matched records from the left.

**Syntax:**

```sql
SELECT columns
FROM table1
RIGHT JOIN table2
ON table1.column = table2.column;
```
### 4. FULL OUTER JOIN
Returns all records when there is a match in either left or right table.

**Syntax:**

```sql
SELECT columns
FROM table1
FULL OUTER JOIN table2
ON table1.column = table2.column;
```

**Question 1**
--
<img width="851" height="840" alt="image" src="https://github.com/user-attachments/assets/10a71c10-764a-4904-a0d4-c46dd2eb18fc" />


```sql
SELECT 
    p.first_name AS patient_name,
    d.first_name AS doctor_name
FROM patients p
INNER JOIN doctors d
    ON p.doctor_id = d.doctor_id
WHERE p.discharge_date IS NOT NULL;
```

**Output:**

<img width="879" height="393" alt="image" src="https://github.com/user-attachments/assets/cdfa70d6-4d08-4f3a-921c-41e5bfeecfd3" />


**Question 2**
---
<img width="1366" height="808" alt="image" src="https://github.com/user-attachments/assets/eef5606f-9d5e-4bde-a5cf-cf8bcb423542" />


```sql
SELECT 
    c.cust_name,
    c.city,
    o.ord_no,
    o.ord_date,
    o.purch_amt AS "Order Amount"
FROM customer c
LEFT JOIN orders o
    ON c.customer_id = o.customer_id
ORDER BY o.ord_date ASC;

```

**Output:**

<img width="1074" height="782" alt="image" src="https://github.com/user-attachments/assets/f34f24e9-0369-47ca-bd1e-04d335c138ac" />


**Question 3**
---
<img width="525" height="406" alt="image" src="https://github.com/user-attachments/assets/8d0b000f-3b1a-401b-b025-3e0e9d359bd5" />


```sql
SELECT 
    s.name AS salesman_name,
    c.cust_name AS customer_name
FROM salesman s
LEFT JOIN customer c
    ON s.salesman_id = c.salesman_id;
```

**Output:**

<img width="511" height="603" alt="image" src="https://github.com/user-attachments/assets/94784150-fd72-4acf-a089-b660c1ad51ff" />


**Question 4**
---
<img width="1332" height="470" alt="image" src="https://github.com/user-attachments/assets/0c37230f-00df-427b-8d0a-5e93cb4c2663" />


```sql
SELECT 
    p.date_of_birth,
    a.*
FROM patients p
INNER JOIN appointments a
    ON p.patient_id = a.patient_id
WHERE p.first_name = 'Alice';
```

**Output:**

<img width="1266" height="241" alt="image" src="https://github.com/user-attachments/assets/3f2984d1-b276-4d16-ae18-60e0fc55a220" />


**Question 5**
---
<img width="1268" height="737" alt="image" src="https://github.com/user-attachments/assets/52c3b5d2-7a6d-4480-911e-ad0672ec63c8" />


```sql
SELECT a.cust_name, a.city, b.ord_no,
       b.ord_date, b.purch_amt AS "Order Amount", 
       c.name, c.commission 
FROM customer a 
LEFT OUTER JOIN orders b 
ON a.customer_id = b.customer_id 
LEFT OUTER JOIN salesman c 
ON c.salesman_id = b.salesman_id;

```

**Output:**

<img width="1256" height="596" alt="image" src="https://github.com/user-attachments/assets/55bdbcf1-22c6-4247-afee-b6b1b2d5ce11" />


**Question 6**
---
<img width="549" height="309" alt="image" src="https://github.com/user-attachments/assets/1543d533-e1cf-4c6a-a512-3fa99d8a08f1" />


```sql
SELECT 
    c.cust_name,
    s.name
FROM customer c
LEFT JOIN salesman s
    ON c.salesman_id = s.salesman_id
WHERE c.city = s.city;
```

**Output:**

<img width="526" height="388" alt="image" src="https://github.com/user-attachments/assets/397584d6-b095-40d1-a3d9-af2ad476cf51" />


**Question 7**
---
<img width="555" height="664" alt="image" src="https://github.com/user-attachments/assets/cb7225e7-9293-4e15-95f8-b640fb6bea2a" />


```sql
SELECT 
    c.cust_name,
    c.city AS city,
    c.grade,
    s.name AS Salesman,
    s.city AS city
FROM customer c
LEFT JOIN salesman s
    ON c.salesman_id = s.salesman_id
WHERE c.grade < 300
ORDER BY c.customer_id ASC;

```

**Output:**

<img width="1193" height="518" alt="image" src="https://github.com/user-attachments/assets/91d2aab1-7bc3-4dfc-8178-f30e61b20e28" />


**Question 8**
---
<img width="1345" height="489" alt="image" src="https://github.com/user-attachments/assets/cf4bf997-be84-4466-b06b-3d1d33cc9c73" />


```sql
SELECT 
    p.patient_id,
    p.first_name,
    p.last_name,
    p.date_of_birth,
    p.admission_date,
    p.discharge_date,
    p.doctor_id
FROM patients p
INNER JOIN appointments a
    ON p.patient_id = a.patient_id
WHERE a.appointment_date BETWEEN '2024-02-01' AND '2024-02-28';
```

**Output:**

<img width="1348" height="287" alt="image" src="https://github.com/user-attachments/assets/762f35c0-bace-4576-aeb6-a9d8ac958035" />


**Question 9**
---
<img width="541" height="653" alt="image" src="https://github.com/user-attachments/assets/b470ade9-ce75-43d7-bbd0-801145ea30ab" />


```sql
SELECT 
    c.cust_name,
    c.city AS city,
    c.grade,
    s.name AS Salesman,
    s.city AS city
FROM customer c
INNER JOIN salesman s
    ON c.salesman_id = s.salesman_id
ORDER BY c.customer_id ASC;
```

**Output:**

<img width="1218" height="605" alt="image" src="https://github.com/user-attachments/assets/457fe950-473d-4b7b-9396-b978f694f1e4" />


**Question 10**
---
<img width="776" height="727" alt="image" src="https://github.com/user-attachments/assets/a1f0b52d-0429-4a4e-81f7-475196694fa5" />


```sql
SELECT
    T1.ord_no,
    T1.purch_amt,
    T1.ord_date,
    T2.cust_name,
    T2.city AS customer_city,
    T2.grade,
    T3.name AS salesman_name,
    T3.city AS salesman_city,
    T3.commission
FROM
    orders T1
INNER JOIN
    customer T2
ON
    T1.customer_id = T2.customer_id
INNER JOIN
    salesman T3
ON
    T1.salesman_id = T3.salesman_id;
```

**Output:**

<img width="1351" height="597" alt="image" src="https://github.com/user-attachments/assets/06904e81-90a4-4934-9dc2-1f983bc35539" />



## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
