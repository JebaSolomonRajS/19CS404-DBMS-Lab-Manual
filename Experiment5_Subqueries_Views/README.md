# Experiment 5: Subqueries and Views

## AIM
To study and implement subqueries and views.

## THEORY

### Subqueries
A subquery is a query inside another SQL query and is embedded in:
- WHERE clause
- HAVING clause
- FROM clause

**Types:**
- **Single-row subquery**:
  Sub queries can also return more than one value. Such results should be made use along with the operators in and any.
- **Multiple-row subquery**:
  Here more than one subquery is used. These multiple sub queries are combined by means of ‘and’ & ‘or’ keywords.
- **Correlated subquery**:
  A subquery is evaluated once for the entire parent statement whereas a correlated Sub query is evaluated once per row processed by the parent statement.

**Example:**
```sql
SELECT * FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);
```
### Views
A view is a virtual table based on the result of an SQL SELECT query.
**Create View:**
```sql
CREATE VIEW view_name AS
SELECT column1, column2 FROM table_name WHERE condition;
```
**Drop View:**
```sql
DROP VIEW view_name;
```

**Question 1**
--
<img width="970" height="765" alt="image" src="https://github.com/user-attachments/assets/10641c6a-68b0-4cd1-a3ad-db302db793a9" />


```sql
SELECT *
FROM CUSTOMERS
WHERE AGE < 30;

```

**Output:**

<img width="1263" height="624" alt="image" src="https://github.com/user-attachments/assets/16908297-1fb7-44a6-95ee-58aeef7f2aca" />


**Question 2**
---
<img width="1349" height="501" alt="image" src="https://github.com/user-attachments/assets/c4184aed-b1e2-40bd-9555-45654d0448e3" />


```sql
SELECT grade, COUNT(*)
FROM customer
WHERE grade > (
    SELECT AVG(grade)
    FROM customer
    WHERE city = 'New York'
)
GROUP BY grade;

```

**Output:**

<img width="1257" height="356" alt="image" src="https://github.com/user-attachments/assets/23cdab88-235f-4019-b290-c2aea5cc8469" />


**Question 3**
---
<img width="1185" height="782" alt="image" src="https://github.com/user-attachments/assets/95965a57-6692-4895-a8a8-452a359043ce" />


```sql
SELECT ord_no, purch_amt, ord_date, customer_id, salesman_id
FROM orders
WHERE salesman_id IN (
    SELECT salesman_id
    FROM salesman
    WHERE city = 'New York'
);

```

**Output:**

<img width="1253" height="524" alt="image" src="https://github.com/user-attachments/assets/743faaf4-2aba-4fe1-863e-76c954d3a782" />


**Question 4**
---
<img width="1255" height="658" alt="image" src="https://github.com/user-attachments/assets/43735056-b740-467b-88fd-0a134cc2717b" />


```sql
SELECT student_name, grade
FROM grades g
WHERE grade = (
    SELECT MIN(grade)
    FROM grades
    WHERE subject = g.subject
);


```

**Output:**

<img width="1098" height="491" alt="image" src="https://github.com/user-attachments/assets/1ed5594e-ff80-463c-977f-bd86bd8162c7" />


**Question 5**
---
<img width="987" height="494" alt="image" src="https://github.com/user-attachments/assets/d59156bf-8680-4091-8d86-4e72c518dbf7" />


```sql
SELECT medication_id, medication_name, dosage
FROM Medications
WHERE dosage = (
    SELECT MAX(dosage)
    FROM Medications
);

```

**Output:**

<img width="1203" height="406" alt="image" src="https://github.com/user-attachments/assets/e61ff2e3-ac79-4a31-ae2a-163937342555" />


**Question 6**
---
<img width="1213" height="621" alt="image" src="https://github.com/user-attachments/assets/daec5f67-8c8c-4dfb-9752-157b1c680811" />

```sql
SELECT ord_no, purch_amt, ord_date, customer_id, salesman_id
FROM orders
WHERE purch_amt > (
    SELECT AVG(purch_amt)
    FROM orders
    WHERE ord_date = '2012-10-10'
);

```

**Output:**

<img width="1262" height="493" alt="image" src="https://github.com/user-attachments/assets/7d952dc5-ca97-4b50-9fa0-b9f05e9dbb7e" />


**Question 7**
---
<img width="1268" height="826" alt="image" src="https://github.com/user-attachments/assets/af122372-a601-43a9-81d6-f099fce222fc" />


```sql
SELECT ord_no, purch_amt, ord_date, salesman_id
FROM orders
WHERE salesman_id IN (
    SELECT salesman_id
    FROM salesman
    WHERE commission = (
        SELECT MAX(commission)
        FROM salesman
    )
);

```

**Output:**
<img width="1062" height="458" alt="image" src="https://github.com/user-attachments/assets/07bb7d9d-d679-4f04-9dc9-32192805b2ec" />


**Question 8**
---
<img width="1285" height="647" alt="image" src="https://github.com/user-attachments/assets/a2fdb41e-6938-45ad-8c56-49f27995c029" />


```sql
SELECT student_name, grade
FROM grades g
WHERE grade = (
    SELECT MAX(grade)
    FROM grades
    WHERE subject = g.subject
);

```

**Output:**

<img width="1056" height="503" alt="image" src="https://github.com/user-attachments/assets/86bcb407-a4f6-4914-9533-aebaef64aa6e" />


**Question 9**
---
<img width="1247" height="734" alt="image" src="https://github.com/user-attachments/assets/5d5e1194-0d52-40ef-8127-8dfce50aa280" />


```sql
SELECT *
FROM grades g
WHERE grade = (
    SELECT MAX(grade)
    FROM grades
    WHERE subject = g.subject
);

```

**Output:**

<img width="1235" height="389" alt="image" src="https://github.com/user-attachments/assets/a8a32bfd-1b7a-42b4-a829-6ee7c0012ed1" />


**Question 10**
---
<img width="1167" height="521" alt="image" src="https://github.com/user-attachments/assets/3c064905-1c66-4682-98db-99d4436c535e" />


```sql
SELECT *
FROM customer
WHERE city <> (
    SELECT city
    FROM customer
    WHERE id = (SELECT MAX(id) FROM customer)
);

```

**Output:**

<img width="1258" height="549" alt="image" src="https://github.com/user-attachments/assets/909c3053-96fd-4376-bbe5-bec141227af1" />



## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.
