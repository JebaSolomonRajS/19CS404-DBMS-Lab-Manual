# Experiment 10: PL/SQL – Triggers

## AIM
To write and execute PL/SQL trigger programs for automating actions in response to specific table events like INSERT, UPDATE, or DELETE.

---

## THEORY

A **trigger** is a stored PL/SQL block that is automatically executed or fired when a specified event occurs on a table or view. Triggers can be used for enforcing business rules, auditing changes, or automatic updates.

### Types of Triggers:
- **Before Trigger**: Executes before the operation (INSERT, UPDATE, DELETE).
- **After Trigger**: Executes after the operation.
- **Row-level Trigger**: Executes for each affected row.
- **Statement-level Trigger**: Executes once for the triggering statement.

**Basic Syntax:**
```sql
CREATE OR REPLACE TRIGGER trigger_name
BEFORE|AFTER INSERT|UPDATE|DELETE ON table_name
[FOR EACH ROW]
BEGIN
   -- trigger logic
END;
```

## 1. Write a trigger to log every insertion into a table.
**Steps:**
- Create two tables: `employees` (for storing data) and `employee_log` (for logging the inserts).
- Write an **AFTER INSERT** trigger on the `employees` table to log the new data into the `employee_log` table.
# program
```
CREATE OR REPLACE TRIGGER trg_emp_insert_log
AFTER INSERT ON employees
FOR EACH ROW
BEGIN
    INSERT INTO employee_log (emp_id, emp_name, salary)
    VALUES (:NEW.emp_id, :NEW.emp_name, :NEW.salary);
END;
```

**Expected Output:**
- A new entry is added to the `employee_log` table each time a new record is inserted into the `employees` table.
<img width="621" height="219" alt="image" src="https://github.com/user-attachments/assets/2c14460d-a9f2-4ec5-829b-27277100ba1e" />


---

## 2. Write a trigger to prevent deletion of records from a sensitive table.
**Steps:**
- Write a **BEFORE DELETE** trigger aon the `sensitive_data` table.
- Use `RAISE_APPLICATION_ERROR` to prevent deletion and issue a custom error message.
# program
```
CREATE OR REPLACE TRIGGER trg_no_delete_sensitive
BEFORE DELETE ON sensitive_data
BEGIN
    RAISE_APPLICATION_ERROR(-20001, 'ERROR: Deletion not allowed on this table.');
END;
```

**Expected Output:**
- If an attempt is made to delete a record from `sensitive_data`, an error message is raised, e.g., `ERROR: Deletion not allowed on this table.`
<img width="627" height="180" alt="image" src="https://github.com/user-attachments/assets/a224844d-29ca-4309-afec-aacde6b890e1" />


---

## 3. Write a trigger to automatically update a `last_modified` timestamp.
**Steps:**
- Add a `last_modified` column to the `products` table.
- Write a **BEFORE UPDATE** trigger on the `products` table to set the `last_modified` column to the current timestamp whenever an update occurs.
# program
```
CREATE OR REPLACE TRIGGER trg_products_last_modified
BEFORE UPDATE ON products
FOR EACH ROW
BEGIN
    :NEW.last_modified := CURRENT_TIMESTAMP;
END;
```

**Expected Output:**
- The `last_modified` column in the `products` table is updated automatically to the current date and time when any record is updated.
<img width="657" height="214" alt="image" src="https://github.com/user-attachments/assets/35dd1d1a-05cc-4062-b7da-0fc5927ee431" />


---

## 4. Write a trigger to keep track of the number of updates made to a table.
**Steps:**
- Create an `audit_log` table with a counter column.
- Write an **AFTER UPDATE** trigger on the `customer_orders` table to increment the counter in the `audit_log` table every time a record is updated.
# program
```
CREATE OR REPLACE TRIGGER trg_update_counter
AFTER UPDATE ON customer_orders
BEGIN
    UPDATE audit_log
    SET update_counter = update_counter + 1;
END;
```

**Expected Output:**
- The `audit_log` table will maintain a count of how many updates have been made to the `customer_orders` table.
- 
<img width="701" height="208" alt="image" src="https://github.com/user-attachments/assets/d179c7cb-13b4-4592-b753-936cac46c810" />

---

## 5. Write a trigger that checks a condition before allowing insertion into a table.
**Steps:**
- Write a **BEFORE INSERT** trigger on the `employees` table to check if the inserted salary meets a specific condition (e.g., salary must be greater than 3000).
- If the condition is not met, raise an error to prevent the insert.
# program
```
CREATE OR REPLACE TRIGGER trg_check_salary
BEFORE INSERT ON employees
FOR EACH ROW
BEGIN
    IF :NEW.salary < 3000 THEN
        RAISE_APPLICATION_ERROR(-20002, 'ERROR: Salary below minimum threshold');
    END IF;
END;
```

**Expected Output:**
- If the inserted salary in the `employees` table is below the condition (e.g., salary < 3000), the insert operation is blocked, and an error message is raised, such as: `ERROR: Salary below minimum threshold.`
<img width="597" height="113" alt="image" src="https://github.com/user-attachments/assets/2ed5a183-36cc-4182-93d8-ff720ddfeb63" />

## RESULT
Thus, the PL/SQL trigger programs were written and executed successfully.
