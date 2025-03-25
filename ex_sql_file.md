# SQL Tutorial

## A. Data Definition Language (DDL)

### 1. CREATE TABLE - Creates a new table.
```sql
CREATE TABLE employees (
    id INT PRIMARY KEY,
    name VARCHAR(50),
    age INT,
    department VARCHAR(50),
    salary DECIMAL(10,2),
    joining_date DATE
);
```

### 2. ALTER TABLE - Modifies an existing table.
```sql
ALTER TABLE employees ADD COLUMN email VARCHAR(100);
```

### 3. DROP TABLE - Deletes a table permanently.
```sql
DROP TABLE employees;
```

### 4. TRUNCATE TABLE - Deletes all records but keeps the structure.
```sql
TRUNCATE TABLE employees;
```

## B. Data Manipulation Language (DML)

### 5. INSERT INTO - Adds records into a table.
```sql
INSERT INTO employees (id, name, age, department, salary, joining_date)
VALUES (1, 'Alice', 25, 'HR', 50000, '2020-03-15');
```

### 6. UPDATE - Modifies existing records.
```sql
UPDATE employees SET salary = 75000 WHERE id = 2;
```

### 7. DELETE FROM - Removes records.
```sql
DELETE FROM employees WHERE id = 5;
```

## C. Data Query Language (DQL)

### 8. SELECT - Retrieves data from the table.
```sql
SELECT * FROM employees;
```

### 9. WHERE Clause - Filters records.
```sql
SELECT name, department FROM employees WHERE age > 30;
```

### 10. ORDER BY - Sorts records.
```sql
SELECT * FROM employees ORDER BY salary DESC;
```

### 11. GROUP BY & HAVING - Groups results and filters aggregated values.
```sql
SELECT department, AVG(salary) FROM employees GROUP BY department HAVING AVG(salary) > 60000;
```

### 12. LIMIT - Restricts the number of rows returned.
```sql
SELECT * FROM employees LIMIT 3;
```

## D. Data Control Language (DCL)

### 13. GRANT - Gives privileges.
```sql
GRANT SELECT, INSERT ON employees TO 'user1';
```

### 14. REVOKE - Removes privileges.
```sql
REVOKE INSERT ON employees FROM 'user1';
```

## E. Transaction Control Language (TCL)

### 15. COMMIT - Saves a transaction permanently.
```sql
BEGIN;
UPDATE employees SET salary = 60000 WHERE department = 'HR';
COMMIT;
```

### 16. ROLLBACK - Undoes a transaction.
```sql
BEGIN;
DELETE FROM employees WHERE department = 'Sales';
ROLLBACK;
```

### 17. SAVEPOINT - Creates a save point in a transaction.
```sql
SAVEPOINT before_update;
UPDATE employees SET salary = 90000 WHERE id = 3;
ROLLBACK TO before_update;
```

## F. Advanced SQL Queries

### 18. JOINs

#### INNER JOIN (Returns matching records from both tables)
```sql
SELECT employees.name, departments.department_name
FROM employees
INNER JOIN departments ON employees.department = departments.id;
```

#### LEFT JOIN (Returns all records from left table, matched ones from right)
```sql
SELECT employees.name, departments.department_name
FROM employees
LEFT JOIN departments ON employees.department = departments.id;
```

#### RIGHT JOIN (Returns all records from right table, matched ones from left)
```sql
SELECT employees.name, departments.department_name
FROM employees
RIGHT JOIN departments ON employees.department = departments.id;
```

### 19. Subqueries
```sql
SELECT name FROM employees WHERE salary > (SELECT AVG(salary) FROM employees);
```

### 20. CASE Statement
```sql
SELECT name, salary,
    CASE 
        WHEN salary > 70000 THEN 'High'
        WHEN salary BETWEEN 50000 AND 70000 THEN 'Medium'
        ELSE 'Low'
    END AS salary_category
FROM employees;
```

## 21. Practice Dataset
You can create and populate this dataset in any SQL database:

```sql
CREATE TABLE employees (
    id INT PRIMARY KEY,
    name VARCHAR(50),
    age INT,
    department VARCHAR(50),
    salary DECIMAL(10,2),
    joining_date DATE
);

INSERT INTO employees VALUES
(1, 'Alice', 25, 'HR', 50000, '2020-03-15'),
(2, 'Bob', 30, 'IT', 70000, '2018-06-20'),
(3, 'Carol', 28, 'Sales', 55000, '2019-09-10'),
(4, 'Dave', 35, 'IT', 80000, '2015-11-23'),
(5, 'Eve', 26, 'Marketing', 60000, '2021-07-30');
