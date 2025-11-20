# Experiment 3: DML Commands

## AIM
To study and implement DML (Data Manipulation Language) commands.

## THEORY

### 1. INSERT INTO
Used to add records into a relation.
These are three type of INSERT INTO queries which are as
A)Inserting a single record
**Syntax (Single Row):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES (value_1, value_2, ...);
```
**Syntax (Multiple Rows):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES
(value_1, value_2, ...),
(value_3, value_4, ...);
```
**Syntax (Insert from another table):**
```sql
INSERT INTO table_name SELECT * FROM other_table WHERE condition;
```
### 2. UPDATE
Used to modify records in a relation.
Syntax:
```sql
UPDATE table_name SET column1 = value1, column2 = value2 WHERE condition;
```
### 3. DELETE
Used to delete records from a relation.
**Syntax (All rows):**
```sql
DELETE FROM table_name;
```
**Syntax (Specific condition):**
```sql
DELETE FROM table_name WHERE condition;
```
### 4. SELECT
Used to retrieve records from a table.
**Syntax:**
```sql
SELECT column1, column2 FROM table_name WHERE condition;
```
**Question 1**
--
-- Write a SQL statement to change the email column of employees table with 'Unavailable' for all employees in employees table.

    Employees table
    
    ---------------
    employee_id
    
    first_name
    
    last_name
    
    email
    
    phone_number
    
    hire_date
    
    job_id
    
    salary
    
    commission_pct
    
    manager_id
    
    department_id

```sql
--
 UPDATE employees
 SET email = 'Unavailable';
```

**Output:**

![image](https://github.com/user-attachments/assets/4229fa68-a775-49dc-aa6c-61cbbb7520a3)


**Question 2**
---
-- Write a SQL statement to Increase the selling price by 15% in the products table where quantity in stock is less than 50 and supplier ID is 10.
    
    Products Table 
    
    name          type       
    ----------    ---------- 
    
    product_id     INT PRIMARY KEY        
    
    product_name   VARCHAR(10) 
    
    category       VARCHAR(50) 
    
    cost_price     DECIMAL(10) 
    
    sell_price     DECIMAL(10) 
    
    reorder_lv     INT        
    
    quantity       INT        
    
    supplier_id    INT       

```sql
--
UPDATE products
SET sell_price = sell_price * 1.15
WHERE quantity < 50 AND supplier_id = 10;
```

**Output:**

![image](https://github.com/user-attachments/assets/ddd26284-60b8-47df-98d9-5ad5ffe3af1d)


**Question 3**
---
-- Change the supplier name to upper case where contact person contains ' Singh' in suppliers table.

    name               type
    -----------------  ---------------
    
    supplier_id        INT
    
    supplier_name      VARCHAR(100)
    
    contact_person     VARCHAR(100)
    
    phone_number       VARCHAR(20)
    
    email              VARCHAR(100)
    
    address            VARCHAR(250)

```sql
--
 UPDATE suppliers
SET supplier_name = UPPER(supplier_name)
WHERE contact_person LIKE '% Singh';

```

**Output:**

![image](https://github.com/user-attachments/assets/cc0d6991-114d-4fc4-8768-ab940ed47ca9)


**Question 4**
---
-- Write a SQL statement to Change the category to 'Household' where product name contains 'Detergent' in the products table.

Products Table 

name          type       
----------    ---------- 

    product_id     INT PRIMARY KEY      
    
    product_name   VARCHAR(10) 
    
    category       VARCHAR(50) 
    
    cost_price     DECIMAL(10) 
    
    sell_price     DECIMAL(10) 
    
    reorder_lvl    INT        
    
    quantity       INT        
    
    supplier_id    INT           

```sql
--
UPDATE products
SET category = 'Household'
WHERE product_name LIKE '%Detergent%';
```

**Output:**

![image](https://github.com/user-attachments/assets/42bfcc8e-f75c-48f3-88e1-245bdb8b35c9)


**Question 5**
---
-- Write a SQL query to Delete customers from 'customer' table where 'CUST_CITY' is not 'New York' and 'OUTSTANDING_AMT' is greater than 5000.

Sample table: Customer

    +-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
    |CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
    +-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
    | C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
    | C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
    | C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00 | BBBBSBB      | A008       |
```sql
-- 
DELETE FROM customer
WHERE cust_city != 'New York'
  AND outstanding_amt > 5000;
```

**Output:**

![image](https://github.com/user-attachments/assets/528c7fc3-80b3-4bec-a8fd-9f28fa1a3e63)


**Question 6**
---
-- 
Write a SQL query to Delete customers from 'customer' table where 'CUST_NAME' has exactly 6 characters.

Sample table: Customer
    
    +-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
    |CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
    +-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
    | C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
    | C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
    | C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00 | BBBBSBB      | A008       |

```sql
-- 
DELETE FROM customer
WHERE LENGTH(cust_name) = 6;
```

**Output:**

![image](https://github.com/user-attachments/assets/46efbb4d-b863-48b9-9ef8-fb3020a8caaa)


**Question 7**
---
-- 
Write a SQL query to Delete All Doctors with a NULL Last Name

Sample table: Doctors
    
    attributes : doctor_id, first_name, last_name, specialization
    For example:
    
    Test	Result
    SELECT * FROM doctors;
    doctor_id   first_name  last_name   specialization
    ----------  ----------  ----------  --------------
    1           John        Smith       Cardiology
    2           Emily       Johnson     Orthopedics
    3           Michael     Brown       Pediatrics
    4           Febin                   Cardiology
    doctor_id   first_name  last_name   specialization
    ----------  ----------  ----------  --------------
    1           John        Smith       Cardiology
    2           Emily       Johnson     Orthopedics
    3           Michael     Brown       Pediatrics


```sql
--
DELETE FROM doctors
WHERE last_name IS NULL OR last_name = '';
```

**Output:**

![image](https://github.com/user-attachments/assets/39e97d63-9ee9-47bb-9b19-42eb59bd6187)


**Question 8**
---
-- 
Write a SQL query to delete a doctor from Doctors table whos specialization is 'Cardiology'

Sample table: Doctors
    
    attributes : doctor_id, first_name, last_name, specialization


```sql
-- 
DELETE FROM doctors
WHERE specialization = 'Cardiology';
```

**Output:**

![image](https://github.com/user-attachments/assets/208b8ce5-4566-4332-9a3b-875569885795)


**Question 9**
---
-- 
Write a SQL query to Delete customers from 'customer' table where 'GRADE' is less than 2.

 
    Sample table: Customer
    
    +-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
    |CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
    +-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
    | C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
    | C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
    | C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00 | BBBBSBB      | A008       |

```sql
-- 
DELETE FROM customer
WHERE grade < 2;
```

**Output:**

![image](https://github.com/user-attachments/assets/2928fbd8-e7db-4951-b285-2e78c70f2781)


**Question 10**
---
-- 
Write a SQL query to locate the details of customers with grade values above 100. Return customer_id, cust_name, city, grade, and salesman_id.

Sample table: customer

     customer_id |   cust_name    |    city    | grade | salesman_id
    
    -------------+----------------+------------+-------+-------------
    
            3002 | Nick Rimando   | New York   |   100 |        5001
    
            3007 | Brad Davis     | New York   |   200 |        5001
    
            3005 | Graham Zusi    | California |   200 |        5002

```sql
-- 
SELECT customer_id, cust_name, city, grade, salesman_id
FROM customer
WHERE grade > 100;
```

**Output:**

![image](https://github.com/user-attachments/assets/aee807ac-1c83-4c78-9adb-b38d51189bd0)


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
