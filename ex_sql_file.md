A. Data Definition Language (DDL)
CREATE TABLE - Creates a new table.

sql
Copy
Edit
CREATE TABLE employees (
    id INT PRIMARY KEY,
    name VARCHAR(50),
    age INT,
    department VARCHAR(50),
    salary DECIMAL(10,2),
    joining_date DATE
);
ALTER TABLE - Modifies an existing table.

sql
Copy
Edit
ALTER TABLE employees ADD COLUMN email VARCHAR(100);
DROP TABLE - Deletes a table permanently.

sql
Copy
Edit
DROP TABLE employees;
TRUNCATE TABLE - Deletes all records but keeps the structure.

sql
Copy
Edit
TRUNCATE TABLE employees;
B. Data Manipulation Language (DML)
INSERT INTO - Adds records into a table.

sql
Copy
Edit
INSERT INTO employees (id, name, age, department, salary, joining_date)
VALUES (1, 'Alice', 25, 'HR', 50000, '2020-03-15');
UPDATE - Modifies existing records.

sql
Copy
Edit
UPDATE employees SET salary = 75000 WHERE id = 2;
DELETE FROM - Removes records.

sql
Copy
Edit
DELETE FROM employees WHERE id = 5;
C. Data Query Language (DQL)
SELECT - Retrieves data from the table.

sql
Copy
Edit
SELECT * FROM employees;
WHERE Clause - Filters records.

sql
Copy
Edit
SELECT name, department FROM employees WHERE age > 30;
ORDER BY - Sorts records.

sql
Copy
Edit
SELECT * FROM employees ORDER BY salary DESC;
GROUP BY & HAVING - Groups results and filters aggregated values.

sql
Copy
Edit
SELECT department, AVG(salary) FROM employees GROUP BY department HAVING AVG(salary) > 60000;
LIMIT - Restricts the number of rows returned.

sql
Copy
Edit
SELECT * FROM employees LIMIT 3;
D. Data Control Language (DCL)
GRANT - Gives privileges.

sql
Copy
Edit
GRANT SELECT, INSERT ON employees TO 'user1';
REVOKE - Removes privileges.

sql
Copy
Edit
REVOKE INSERT ON employees FROM 'user1';
E. Transaction Control Language (TCL)
COMMIT - Saves a transaction permanently.

sql
Copy
Edit
BEGIN;
UPDATE employees SET salary = 60000 WHERE department = 'HR';
COMMIT;
ROLLBACK - Undoes a transaction.

sql
Copy
Edit
BEGIN;
DELETE FROM employees WHERE department = 'Sales';
ROLLBACK;
SAVEPOINT - Creates a save point in a transaction.

sql
Copy
Edit
SAVEPOINT before_update;
UPDATE employees SET salary = 90000 WHERE id = 3;
ROLLBACK TO before_update;
F. Advanced SQL Queries
JOINs

INNER JOIN (Returns matching records from both tables)

sql
Copy
Edit
SELECT employees.name, departments.department_name
FROM employees
INNER JOIN departments ON employees.department = departments.id;
LEFT JOIN (Returns all records from left table, matched ones from right)

sql
Copy
Edit
SELECT employees.name, departments.department_name
FROM employees
LEFT JOIN departments ON employees.department = departments.id;
RIGHT JOIN (Returns all records from right table, matched ones from left)

sql
Copy
Edit
SELECT employees.name, departments.department_name
FROM employees
RIGHT JOIN departments ON employees.department = departments.id;
Subqueries

sql
Copy
Edit
SELECT name FROM employees WHERE salary > (SELECT AVG(salary) FROM employees);
CASE Statement

sql
Copy
Edit
SELECT name, salary,
    CASE 
        WHEN salary > 70000 THEN 'High'
        WHEN salary BETWEEN 50000 AND 70000 THEN 'Medium'
        ELSE 'Low'
    END AS salary_category
FROM employees;
4. Practice Dataset
You can create and populate this dataset in any SQL database:

sql
Copy
Edit
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