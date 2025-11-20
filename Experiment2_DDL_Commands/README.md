# Experiment 2: DDL Commands
## AIM
To study and implement DDL commands and different types of constraints.

## THEORY

### 1. CREATE
Used to create a new relation (table).

**Syntax:**
```sql
CREATE TABLE (
  field_1 data_type(size),
  field_2 data_type(size),
  ...
);
```
### 2. ALTER
Used to add, modify, drop, or rename fields in an existing relation.
(a) ADD
```sql
ALTER TABLE std ADD (Address CHAR(10));
```
(b) MODIFY
```sql
ALTER TABLE relation_name MODIFY (field_1 new_data_type(size));
```
(c) DROP
```sql
ALTER TABLE relation_name DROP COLUMN field_name;
```
(d) RENAME
```sql
ALTER TABLE relation_name RENAME COLUMN old_field_name TO new_field_name;
```
### 3. DROP TABLE
Used to permanently delete the structure and data of a table.
```sql
DROP TABLE relation_name;
```
### 4. RENAME
Used to rename an existing database object.
```sql
RENAME TABLE old_relation_name TO new_relation_name;
```
### CONSTRAINTS
Constraints are used to specify rules for the data in a table. If there is any violation between the constraint and the data action, the action is aborted by the constraint. It can be specified when the table is created (using CREATE TABLE) or after it is created (using ALTER TABLE).
### 1. NOT NULL
When a column is defined as NOT NULL, it becomes mandatory to enter a value in that column.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) NOT NULL
);
```
### 2. UNIQUE
Ensures that values in a column are unique.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) UNIQUE
);
```
### 3. CHECK
Specifies a condition that each row must satisfy.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) CHECK (logical_expression)
);
```
### 4. PRIMARY KEY
Used to uniquely identify each record in a table.
Properties:
Must contain unique values.
Cannot be null.
Should contain minimal fields.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) PRIMARY KEY
);
```
### 5. FOREIGN KEY
Used to reference the primary key of another table.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size),
  FOREIGN KEY (column_name) REFERENCES other_table(column)
);
```
### 6. DEFAULT
Used to insert a default value into a column if no value is specified.

Syntax:
```sql
CREATE TABLE Table_Name (
  col_name1 data_type,
  col_name2 data_type,
  col_name3 data_type DEFAULT 'default_value'
);
```

**Question 1**
--

Create a table named Members with the following columns:

MemberID as INTEGER
MemberName as TEXT
JoinDate as DATE

```
create table Members (
MemberID INTEGER ,
MemberName TEXT,
JoinDate DATE);


```

**Output:**

<img width="1661" height="383" alt="Screenshot 2025-11-20 212025" src="https://github.com/user-attachments/assets/42d4c038-b681-4049-9e0d-d4456d7b17c6" />


**Question 2**
---
Write a SQL query to Rename the "city" column to "location" in the "customer" table.

```
alter table customer rename column city to location; 

```

**Output:**

<img width="1713" height="308" alt="Screenshot 2025-11-20 212436" src="https://github.com/user-attachments/assets/24559046-0289-40bb-92fa-91687253f89c" />


**Question 3**
---
Insert the below data into the Student_details table, allowing the Subject and MARKS columns to take their default values.

| RollNo     | Name         | Gender      
| ---------- | ------------ | ----------  
| 204        | Samuel Black | M          

Note: The Subject and MARKS columns will use their default values.

```
insert into Student_details(RollNo,Name,Gender)
values (204,'Samuel Black','M');
```

**Output:**

<img width="1202" height="301" alt="Screenshot 2025-11-20 212444" src="https://github.com/user-attachments/assets/644609e0-45e7-4c14-8f73-14bafa5cdf69" />


**Question 4**
---
Create a table named Products with the following constraints:

ProductID should be the primary key.
ProductName should be NOT NULL.
Price is of real datatype and should be greater than 0.
Stock is of integer datatype and should be greater than or equal to 0.

```
create table Products (
ProductID integer primary key,
ProductName varchar not null,
Price real check(price>0),
Stock integer check(stock>=0));

```

**Output:**

<img width="1258" height="271" alt="Screenshot 2025-11-20 212455" src="https://github.com/user-attachments/assets/31f11c95-ee44-4987-915b-50f5e2b35b4c" />


**Question 5**
---
Insert all students from Archived_students table into the Student_details table.

```
insert into Student_details(RollNo,name,Gender,SUbject,MARKS)
select RollNo,name,Gender,SUbject,MARKS from Archived_students;

```

**Output:**

<img width="1385" height="268" alt="Screenshot 2025-11-20 212508" src="https://github.com/user-attachments/assets/741f2428-3231-4f3a-9d93-38376108eadc" />


**Question 6**
---
Write an SQL query to change the name of the column id to employee_id in the table employee.

```
alter table employee rename column id to employee_id;
```

**Output:**

<img width="1454" height="253" alt="Screenshot 2025-11-20 212517" src="https://github.com/user-attachments/assets/287721fc-3800-437d-8d09-f2633d80aeac" />


**Question 7**
---
Create a table named Orders with the following constraints:
OrderID as INTEGER should be the primary key.
OrderDate as DATE should be not NULL.
CustomerID as INTEGER should be a foreign key referencing Customers(CustomerID).

```
create table Orders(
OrderID integer primary key,
OrderDate date not NULL,
CustomerID integer,
foreign key (CustomerID) references Customers(CustomerID));

```

**Output:**

<img width="1595" height="272" alt="Screenshot 2025-11-20 212526" src="https://github.com/user-attachments/assets/d1e377b8-84de-4b72-95aa-3c209b582df7" />

**Question 8**
---
Create a table named Shipments with the following constraints:
ShipmentID as INTEGER should be the primary key.
ShipmentDate as DATE.
SupplierID as INTEGER should be a foreign key referencing Suppliers(SupplierID).
OrderID as INTEGER should be a foreign key referencing Orders(OrderID).


```

create table Shipments(
ShipmentID integer primary key,
ShipmentDate date,
SupplierID integer,
OrderID integer,
foreign key(SupplierID) references Suppliers(SupplierID),
foreign key(OrderID) references Orders(OrderID));

```

**Output:**

<img width="1435" height="233" alt="Screenshot 2025-11-20 212536" src="https://github.com/user-attachments/assets/25373ed6-4d06-40a0-a8c4-4fd3eb2e57a4" />



**Question 9**
---
In the Employee table, insert a record where some fields are NULL, another record where all fields are filled without any NULL values, and a third record where some fields are filled, and others are left as NULL.


```
insert into Employee(EmployeeID,Name,Position,Department,Salary)
values(5,'George Clark','Consultant',null,null)
,(7,'Noah Davis','Manager','HR',60000),
(8,'Ava Miller','Consultant','IT',null);

```

**Output:**

<img width="1356" height="271" alt="Screenshot 2025-11-20 212545" src="https://github.com/user-attachments/assets/02a64067-842b-4867-96ec-ba2f97f99763" />



**Question 10**
---
create a table named jobs including columns job_id, job_title, min_salary and max_salary, and make sure that, the default value for job_title is blank and min_salary is 8000 and max_salary is NULL will be entered automatically at the time of insertion if no value assigned for the specified columns.

```
create table jobs(
job_id integer primary key,
job_title varchar default '',
min_salary integer default 8000,
max_salary integer default null);

```

**Output:**

<img width="1709" height="302" alt="Screenshot 2025-11-20 212554" src="https://github.com/user-attachments/assets/533b5886-ef84-4c8f-8951-fd6297a84f08" />



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
<img width="1390" height="72" alt="image" src="https://github.com/user-attachments/assets/3053982c-1277-4c8d-b488-f22bfaecc02d" />

