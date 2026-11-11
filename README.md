# SQL – Complete Learning Guide

## 📚 Introduction to SQL

**SQL (Structured Query Language)** is a standard programming language used to communicate with relational database management systems (RDBMS).

SQL allows us to create databases, store data, retrieve information, modify existing records, and manage transactions.

### Why SQL?

SQL is widely used in:
- Data Analytics
- Data Science
- Business Intelligence
- Data Engineering
- Database Management
- Backend Development
- Reporting and Dashboard Development

### Popular SQL Databases

1. MySQL
2. PostgreSQL
3. Microsoft SQL Server
4. Oracle Database
5. SQLite

---

# 1. SQL Command Categories

SQL commands are generally classified into the following categories:

| Category | Full Form | Purpose |
|---|---|---|
| DDL | Data Definition Language | Defines database structure |
| DML | Data Manipulation Language | Modifies table records |
| DQL | Data Query Language | Retrieves data |
| TCL | Transaction Control Language | Manages transactions |
| DCL | Data Control Language | Controls database permissions |

In this guide, we will focus on DDL, DML, DQL, TCL, SQL Clauses, and Ranking Functions.

---

# 2. DDL – Data Definition Language

## 2.1 What is DDL?

DDL stands for **Data Definition Language**.

DDL commands are used to define, create, and modify the structure of database objects such as tables, databases, and schemas.

DDL primarily deals with the structure of a database rather than individual records.

### Important DDL Commands

1. CREATE
2. ALTER
3. DROP
4. TRUNCATE
5. RENAME

## 2.2 CREATE

### Theory

The CREATE command is used to create new database objects such as databases, tables, and views.

### Syntax

**Creating a Database**

```sql
CREATE DATABASE database_name;
```

**Creating a Table**

```sql
CREATE TABLE table_name (
    column1 datatype,
    column2 datatype,
    column3 datatype
);
```

### Example 1: Creating a Database

```sql
CREATE DATABASE CompanyDB;
```

### Example 2: Creating an Employee Table

```sql
CREATE TABLE Employees (
    EmployeeID INT PRIMARY KEY,
    EmployeeName VARCHAR(100),
    Department VARCHAR(50),
    Salary DECIMAL(10,2),
    JoiningDate DATE
);
```

### Scenario-Based Example

**Scenario:** A company wants to maintain employee information in a database.

First, create a database called `CompanyDB`, then create an `Employees` table to store employee details.

```sql
CREATE DATABASE CompanyDB;

USE CompanyDB;

CREATE TABLE Employees (
    EmployeeID INT PRIMARY KEY,
    EmployeeName VARCHAR(100),
    Department VARCHAR(50),
    Salary DECIMAL(10,2),
    JoiningDate DATE
);
```

## 2.3 ALTER

### Theory

The ALTER command is used to modify the existing structure of a table.

We can:
- Add new columns.
- Modify existing column definitions.
- Drop existing columns.
- Rename columns (syntax depends on the database).

### Syntax

**Add a Column**

```sql
ALTER TABLE table_name
ADD column_name datatype;
```

**Modify a Column**

```sql
ALTER TABLE table_name
MODIFY column_name new_datatype;
```

**Drop a Column**

```sql
ALTER TABLE table_name
DROP COLUMN column_name;
```

**Rename a Column**

```sql
ALTER TABLE table_name
RENAME COLUMN old_name TO new_name;
```

### Examples

**Example 1: Add a new column**

```sql
ALTER TABLE Employees
ADD Email VARCHAR(100);
```

**Example 2: Modify a column**

```sql
ALTER TABLE Employees
MODIFY EmployeeName VARCHAR(150);
```

*Note: MODIFY is supported in MySQL. SQL Server and PostgreSQL use different syntax.*

**Example 3: Drop a column**

```sql
ALTER TABLE Employees
DROP COLUMN Email;
```

**Example 4: Rename a column**

```sql
ALTER TABLE Employees
RENAME COLUMN EmployeeName TO FullName;
```

### Scenario-Based Example

**Scenario:** The HR department wants to store employee email addresses in the existing Employees table.

Instead of creating a new table, add an Email column to the existing table.

```sql
ALTER TABLE Employees
ADD Email VARCHAR(100);
```

## 2.4 DROP

### Theory

The DROP command is used to permanently remove database objects such as tables and databases.

When a table is dropped, its structure and stored records are removed.

### Syntax

```sql
DROP TABLE table_name;
```

To drop a database:

```sql
DROP DATABASE database_name;
```

### Examples

```sql
DROP TABLE Employees;
```

```sql
DROP DATABASE CompanyDB;
```

### Scenario-Based Example

**Scenario:** A company has discontinued an old employee management system and no longer needs its temporary employee table.

```sql
DROP TABLE TemporaryEmployees;
```

**Important:** DROP removes the entire table, including its structure and data.

## 2.5 TRUNCATE

### Theory

The TRUNCATE command is used to remove all records from an existing table while keeping its table structure.

Unlike DROP, TRUNCATE does not remove the table itself.

### Syntax

```sql
TRUNCATE TABLE table_name;
```

### Example

```sql
TRUNCATE TABLE Employees;
```

### Scenario-Based Example

**Scenario:** A company conducts annual employee training. After the training is completed, the temporary training attendance records need to be cleared, but the table structure must remain available for the next training session.

```sql
TRUNCATE TABLE TrainingAttendance;
```

**Important Points:**
- Removes all rows.
- Retains the table structure.
- Does not support a WHERE condition.
- Rollback behavior depends on the database system and transaction settings.

## 2.6 RENAME

### Theory

The RENAME command is used to change the name of an existing table.

### Syntax

```sql
RENAME TABLE old_table_name TO new_table_name;
```

### Example

```sql
RENAME TABLE Employees TO EmployeeDetails;
```

### Scenario-Based Example

**Scenario:** A company wants to rename the Employees table to EmployeeDetails to make its purpose clearer.

```sql
RENAME TABLE Employees TO EmployeeDetails;
```

### DDL Summary

| Command | Purpose |
|---|---|
| CREATE | Creates database objects |
| ALTER | Modifies table structure |
| DROP | Removes database objects |
| TRUNCATE | Removes all records but retains structure |
| RENAME | Changes the name of a database object |

---

# 3. DML – Data Manipulation Language

## 3.1 What is DML?

DML stands for **Data Manipulation Language**.

DML commands are used to insert, modify, and delete records stored inside database tables.

Unlike DDL, which deals with table structure, DML focuses on the actual data.

### Important DML Commands

1. INSERT
2. UPDATE
3. DELETE

## 3.2 INSERT

### Theory

The INSERT command is used to add new records into an existing table.

### Syntax

**Insert a Single Record**

```sql
INSERT INTO table_name
(column1, column2, column3)
VALUES
(value1, value2, value3);
```

**Insert Multiple Records**

```sql
INSERT INTO table_name
(column1, column2, column3)
VALUES
(value1, value2, value3),
(value4, value5, value6);
```

### Examples

```sql
INSERT INTO Employees
(EmployeeID, EmployeeName, Department, Salary, JoiningDate)
VALUES
(101, 'Rahul', 'IT', 50000, '2024-01-15');
```

**Inserting Multiple Records**

```sql
INSERT INTO Employees
(EmployeeID, EmployeeName, Department, Salary, JoiningDate)
VALUES
(102, 'Priya', 'HR', 45000, '2023-05-10'),
(103, 'Kiran', 'IT', 60000, '2022-08-20'),
(104, 'Anjali', 'Finance', 55000, '2024-03-12');
```

### Scenario-Based Example

**Scenario:** A new employee joins the IT department with an annual salary of ₹6,00,000.

The HR department needs to insert the employee details into the Employees table.

```sql
INSERT INTO Employees
(EmployeeID, EmployeeName, Department, Salary, JoiningDate)
VALUES
(105, 'Arjun', 'IT', 600000, '2025-01-10');
```

## 3.3 UPDATE

### Theory

The UPDATE command is used to modify existing records in a table.

We can update one or multiple columns based on a specified condition.

### Syntax

```sql
UPDATE table_name
SET column_name = new_value
WHERE condition;
```

### Examples

**Example 1: Update one column**

```sql
UPDATE Employees
SET Salary = 65000
WHERE EmployeeID = 101;
```

**Example 2: Update multiple columns**

```sql
UPDATE Employees
SET Department = 'Data Analytics',
    Salary = 75000
WHERE EmployeeID = 103;
```

### Scenario-Based Example

**Scenario:** An employee named Rahul receives a salary increment from ₹50,000 to ₹60,000.

```sql
UPDATE Employees
SET Salary = 60000
WHERE EmployeeName = 'Rahul';
```

**Important:** Always use the WHERE condition carefully. Without WHERE, all records in the table will be updated.

## 3.4 DELETE

### Theory

The DELETE command is used to remove specific records or all records from a table.

We can use the WHERE condition to delete particular records.

### Syntax

```sql
DELETE FROM table_name
WHERE condition;
```

### Examples

**Example 1: Delete a specific employee**

```sql
DELETE FROM Employees
WHERE EmployeeID = 105;
```

**Example 2: Delete employees from a particular department**

```sql
DELETE FROM Employees
WHERE Department = 'HR';
```

**Example 3: Delete all records**

```sql
DELETE FROM Employees;
```

### Scenario-Based Example

**Scenario:** An employee leaves the organization, and HR wants to remove the employee's record from the Employees table.

```sql
DELETE FROM Employees
WHERE EmployeeID = 102;
```

**Important:** DELETE without WHERE removes all rows. The table structure remains unchanged.

### DML Summary

| Command | Purpose |
|---|---|
| INSERT | Adds new records |
| UPDATE | Modifies existing records |
| DELETE | Removes records |

---

# 4. DQL – Data Query Language

## 4.1 What is DQL?

DQL stands for **Data Query Language**.

DQL is used to retrieve information from database tables without changing the existing data.

The primary DQL command is:

1. SELECT

## 4.2 SELECT

### Theory

The SELECT command is used to retrieve data from one or more database tables.

It allows us to retrieve all columns or only the specific columns required.

### Syntax

**Retrieve All Columns**

```sql
SELECT *
FROM table_name;
```

**Retrieve Specific Columns**

```sql
SELECT column1, column2
FROM table_name;
```

### Examples

**Example 1: Retrieve all employee records**

```sql
SELECT *
FROM Employees;
```

**Example 2: Retrieve employee names and salaries**

```sql
SELECT EmployeeName, Salary
FROM Employees;
```

**Example 3: Retrieve employee details from the IT department**

```sql
SELECT *
FROM Employees
WHERE Department = 'IT';
```

### Scenario-Based Example

**Scenario:** The HR manager wants to see the names and salaries of all employees working in the IT department.

```sql
SELECT EmployeeName, Salary
FROM Employees
WHERE Department = 'IT';
```

## 4.3 DISTINCT

### Theory

DISTINCT is used to retrieve only unique values from a column or a combination of columns.

It eliminates duplicate records from the result set.

### Syntax

```sql
SELECT DISTINCT column_name
FROM table_name;
```

### Example

```sql
SELECT DISTINCT Department
FROM Employees;
```

### Scenario-Based Example

**Scenario:** The management team wants to identify all unique departments available in the organization.

```sql
SELECT DISTINCT Department
FROM Employees;
```

## 4.4 Aggregate Functions

### Theory

Aggregate functions perform calculations on multiple rows and return a single result for each group or for the entire result set.

### Important Aggregate Functions

**1. COUNT()**

Counts the number of records.

```sql
SELECT COUNT(*)
FROM Employees;
```

Scenario: Find the total number of employees.

```sql
SELECT COUNT(*) AS TotalEmployees
FROM Employees;
```

**2. SUM()**

Calculates the total of numeric values.

```sql
SELECT SUM(Salary)
FROM Employees;
```

Scenario: Calculate the total salary expenditure.

```sql
SELECT SUM(Salary) AS TotalSalary
FROM Employees;
```

**3. AVG()**

Calculates the average value.

```sql
SELECT AVG(Salary)
FROM Employees;
```

Scenario: Find the average employee salary.

```sql
SELECT AVG(Salary) AS AverageSalary
FROM Employees;
```

**4. MIN()**

Returns the minimum value.

```sql
SELECT MIN(Salary)
FROM Employees;
```

Scenario: Find the lowest employee salary.

```sql
SELECT MIN(Salary) AS MinimumSalary
FROM Employees;
```

**5. MAX()**

Returns the maximum value.

```sql
SELECT MAX(Salary)
FROM Employees;
```

Scenario: Find the highest employee salary.

```sql
SELECT MAX(Salary) AS MaximumSalary
FROM Employees;
```

### Aggregate Functions Summary

| Function | Description |
|---|---|
| COUNT() | Counts records |
| SUM() | Calculates total |
| AVG() | Calculates average |
| MIN() | Returns minimum |
| MAX() | Returns maximum |

---

# 5. SQL CLAUSES

## 5.1 What are SQL Clauses?

SQL clauses are specific components of SQL statements used to filter, group, sort, and organize data.

They help us retrieve meaningful information from large datasets.

### Important SQL Clauses

1. WHERE
2. GROUP BY
3. HAVING
4. ORDER BY
5. LIMIT
6. OFFSET
7. DISTINCT
8. TOP
9. LIKE
10. BETWEEN
11. IN
12. IS NULL

## 5.2 WHERE Clause

### Theory

WHERE is used to filter records based on a specified condition.

Only records satisfying the condition are returned.

### Syntax

```sql
SELECT column_name
FROM table_name
WHERE condition;
```

### Examples

**Example 1: Employees earning more than ₹50,000**

```sql
SELECT *
FROM Employees
WHERE Salary > 50000;
```

**Example 2: Employees belonging to the IT department**

```sql
SELECT *
FROM Employees
WHERE Department = 'IT';
```

**Example 3: Employees earning less than ₹60,000**

```sql
SELECT *
FROM Employees
WHERE Salary < 60000;
```

### Scenario

The HR manager wants to identify employees whose salary is greater than ₹50,000.

```sql
SELECT EmployeeName, Salary
FROM Employees
WHERE Salary > 50000;
```

## 5.3 GROUP BY Clause

### Theory

GROUP BY is used to group records that have the same values in one or more columns.

It is commonly used with aggregate functions such as COUNT(), SUM(), AVG(), MIN(), and MAX().

### Syntax

```sql
SELECT column_name, aggregate_function(column_name)
FROM table_name
GROUP BY column_name;
```

### Examples

**Example 1: Count employees in each department**

```sql
SELECT Department, COUNT(*) AS TotalEmployees
FROM Employees
GROUP BY Department;
```

**Example 2: Calculate the average salary for each department**

```sql
SELECT Department, AVG(Salary) AS AverageSalary
FROM Employees
GROUP BY Department;
```

**Example 3: Find the total salary expenditure of each department**

```sql
SELECT Department, SUM(Salary) AS TotalSalary
FROM Employees
GROUP BY Department;
```

### Scenario

The management team wants to identify how many employees are working in each department.

```sql
SELECT Department, COUNT(*) AS EmployeeCount
FROM Employees
GROUP BY Department;
```

## 5.4 HAVING Clause

### Theory

HAVING is used to filter grouped records based on aggregate conditions.

It is generally used with GROUP BY.

### Difference Between WHERE and HAVING

| WHERE | HAVING |
|---|---|
| Filters individual rows | Filters groups |
| Applied before GROUP BY | Applied after GROUP BY |
| Commonly used with normal conditions | Commonly used with aggregate conditions |
| Cannot directly filter aggregate results at the same query level | Can filter aggregate results |

### Syntax

```sql
SELECT column_name, aggregate_function(column_name)
FROM table_name
GROUP BY column_name
HAVING condition;
```

### Examples

**Example 1: Departments having more than 5 employees**

```sql
SELECT Department, COUNT(*) AS TotalEmployees
FROM Employees
GROUP BY Department
HAVING COUNT(*) > 5;
```

**Example 2: Departments having an average salary greater than ₹50,000**

```sql
SELECT Department, AVG(Salary) AS AverageSalary
FROM Employees
GROUP BY Department
HAVING AVG(Salary) > 50000;
```

### Scenario

The management team wants to identify departments where the total salary expenditure exceeds ₹2,00,000.

```sql
SELECT Department, SUM(Salary) AS TotalSalary
FROM Employees
GROUP BY Department
HAVING SUM(Salary) > 200000;
```

## 5.5 ORDER BY Clause

### Theory

ORDER BY is used to sort the result set based on one or more columns.

It supports two sorting directions:

- ASC – Ascending order.
- DESC – Descending order.

ASC is the default sorting order.

### Syntax

```sql
SELECT *
FROM table_name
ORDER BY column_name ASC;
```

### Examples

**Example 1: Sort employees by salary in ascending order**

```sql
SELECT *
FROM Employees
ORDER BY Salary ASC;
```

**Example 2: Sort employees by salary in descending order**

```sql
SELECT *
FROM Employees
ORDER BY Salary DESC;
```

**Example 3: Sort by department and salary**

```sql
SELECT *
FROM Employees
ORDER BY Department ASC, Salary DESC;
```

### Scenario

The HR manager wants to identify the highest-paid employees first.

```sql
SELECT EmployeeName, Salary
FROM Employees
ORDER BY Salary DESC;
```

## 5.6 LIMIT Clause

### Theory

LIMIT is used to restrict the number of records returned by a query.

It is supported by MySQL, PostgreSQL, and SQLite.

### Syntax

```sql
SELECT *
FROM table_name
LIMIT number;
```

### Examples

**Example 1: Retrieve the first 5 employees**

```sql
SELECT *
FROM Employees
LIMIT 5;
```

**Example 2: Retrieve the top 3 highest-paid employees**

```sql
SELECT *
FROM Employees
ORDER BY Salary DESC
LIMIT 3;
```

### Scenario

The HR manager wants to identify the top 3 highest-paid employees.

```sql
SELECT EmployeeName, Salary
FROM Employees
ORDER BY Salary DESC
LIMIT 3;
```

## 5.7 OFFSET Clause

### Theory

OFFSET is used to skip a specified number of records before returning the remaining result set.

It is commonly used for pagination.

### Syntax

```sql
SELECT *
FROM table_name
LIMIT number OFFSET number;
```

### Example

```sql
SELECT *
FROM Employees
LIMIT 5 OFFSET 10;
```

This query skips the first 10 records and retrieves the next 5 records.

### Scenario

A company has 1000 employee records. The HR manager wants to display employees in pages of 10 records each.

**Page 1**

```sql
SELECT *
FROM Employees
LIMIT 10 OFFSET 0;
```

**Page 2**

```sql
SELECT *
FROM Employees
LIMIT 10 OFFSET 10;
```

**Page 3**

```sql
SELECT *
FROM Employees
LIMIT 10 OFFSET 20;
```

## 5.8 LIKE Operator

### Theory

LIKE is used to search for a specific pattern in a column.

It is commonly used with two wildcard characters:

- `%` – Represents zero or more characters.
- `_` – Represents exactly one character.

### Syntax

```sql
SELECT *
FROM table_name
WHERE column_name LIKE 'pattern';
```

### Examples

**Example 1: Names starting with A**

```sql
SELECT *
FROM Employees
WHERE EmployeeName LIKE 'A%';
```

**Example 2: Names ending with a**

```sql
SELECT *
FROM Employees
WHERE EmployeeName LIKE '%a';
```

**Example 3: Names containing an**

```sql
SELECT *
FROM Employees
WHERE EmployeeName LIKE '%an%';
```

**Example 4: Names where the second character is a**

```sql
SELECT *
FROM Employees
WHERE EmployeeName LIKE '_a%';
```

### Scenario

The HR manager wants to find all employees whose names start with the letter 'A'.

```sql
SELECT *
FROM Employees
WHERE EmployeeName LIKE 'A%';
```

## 5.9 BETWEEN Operator

### Theory

BETWEEN is used to retrieve records within a specified range.

It includes both the starting and ending values.

### Syntax

```sql
SELECT *
FROM table_name
WHERE column_name BETWEEN value1 AND value2;
```

### Examples

**Example 1: Employees earning between ₹30,000 and ₹60,000**

```sql
SELECT *
FROM Employees
WHERE Salary BETWEEN 30000 AND 60000;
```

**Example 2: Employees who joined between two dates**

```sql
SELECT *
FROM Employees
WHERE JoiningDate BETWEEN '2023-01-01' AND '2024-12-31';
```

### Scenario

The finance department wants to identify employees whose salaries fall between ₹40,000 and ₹70,000.

```sql
SELECT EmployeeName, Salary
FROM Employees
WHERE Salary BETWEEN 40000 AND 70000;
```

## 5.10 IN Operator

### Theory

IN is used to check whether a column value matches any value in a specified list.

It is an alternative to writing multiple OR conditions.

### Syntax

```sql
SELECT *
FROM table_name
WHERE column_name IN (value1, value2, value3);
```

### Examples

```sql
SELECT *
FROM Employees
WHERE Department IN ('IT', 'HR', 'Finance');
```

### Scenario

The company wants to retrieve employees working in the IT, HR, and Finance departments.

```sql
SELECT *
FROM Employees
WHERE Department IN ('IT', 'HR', 'Finance');
```

## 5.11 IS NULL

### Theory

IS NULL is used to identify records where a column contains NULL values.

NULL represents missing or unknown information.

We should use IS NULL rather than the equality operator (= NULL).

### Syntax

```sql
SELECT *
FROM table_name
WHERE column_name IS NULL;
```

### Examples

```sql
SELECT *
FROM Employees
WHERE Email IS NULL;
```

To retrieve records where values are not NULL:

```sql
SELECT *
FROM Employees
WHERE Email IS NOT NULL;
```

### Scenario

The HR manager wants to identify employees whose email addresses have not been provided.

```sql
SELECT EmployeeName
FROM Employees
WHERE Email IS NULL;
```

## 5.12 AND, OR, NOT Operators

### AND

Returns records when all specified conditions are true.

```sql
SELECT *
FROM Employees
WHERE Department = 'IT'
AND Salary > 50000;
```

### OR

Returns records when at least one condition is true.

```sql
SELECT *
FROM Employees
WHERE Department = 'IT'
OR Department = 'HR';
```

### NOT

Negates a specified condition.

```sql
SELECT *
FROM Employees
WHERE NOT Department = 'HR';
```

### Scenario

Find employees who work in IT and earn more than ₹50,000.

```sql
SELECT *
FROM Employees
WHERE Department = 'IT'
AND Salary > 50000;
```

---

# 6. SQL RANKING FUNCTIONS

## 6.1 What are Ranking Functions?

Ranking functions are SQL window functions used to assign a numerical rank to each row based on a specified ordering condition.

They are especially useful in Data Analytics and reporting when we need to identify:

- Highest-paid employees.
- Top-performing students.
- Department-wise rankings.
- Top 3 or Top 5 records.
- Employees with the second-highest salary.
- Ranking based on sales performance.

### Important Ranking Functions

1. ROW_NUMBER()
2. RANK()
3. DENSE_RANK()
4. NTILE()

Ranking functions are generally used with the OVER() clause.

## 6.2 Understanding the OVER() Clause

### Theory

The OVER() clause defines the set of rows over which a window function operates.

It can contain:

- PARTITION BY – Divides records into groups.
- ORDER BY – Defines the ranking order.

### Syntax

```sql
SELECT
    column_name,
    RANK() OVER (
        PARTITION BY column_name
        ORDER BY column_name DESC
    ) AS Ranking
FROM table_name;
```

### PARTITION BY

PARTITION BY divides the result set into separate groups.

Ranking starts again from 1 for each partition.

Example:

```sql
SELECT
    EmployeeName,
    Department,
    Salary,
    RANK() OVER (
        PARTITION BY Department
        ORDER BY Salary DESC
    ) AS DepartmentRank
FROM Employees;
```

This query ranks employees separately within each department.

### ORDER BY Inside OVER()

ORDER BY determines how rows are ranked.

```sql
RANK() OVER (ORDER BY Salary DESC)
```

This ranks employees from highest salary to lowest salary.

---

## 6.3 ROW_NUMBER()

### Theory

ROW_NUMBER() assigns a unique sequential number to every row based on the specified ordering.

Even when two or more employees have the same salary, each employee receives a different row number.

### Syntax

```sql
SELECT
    column_name,
    ROW_NUMBER() OVER (
        ORDER BY column_name DESC
    ) AS RowNumber
FROM table_name;
```

### Example

```sql
SELECT
    EmployeeName,
    Salary,
    ROW_NUMBER() OVER (
        ORDER BY Salary DESC
    ) AS RowNumber
FROM Employees;
```

### Sample Output

| EmployeeName | Salary | RowNumber |
|---|---:|---:|
| Rahul | 80000 | 1 |
| Priya | 70000 | 2 |
| Kiran | 70000 | 3 |
| Anjali | 60000 | 4 |
| Arjun | 50000 | 5 |

### Scenario-Based Example

**Scenario:** A company wants to assign a unique position number to every employee based on salary, even when multiple employees have the same salary.

```sql
SELECT
    EmployeeName,
    Salary,
    ROW_NUMBER() OVER (
        ORDER BY Salary DESC, EmployeeID ASC
    ) AS EmployeePosition
FROM Employees;
```

---

## 6.4 RANK()

### Theory

RANK() assigns the same rank to records with identical values.

However, it skips the next rank when duplicate values occur.

### Syntax

```sql
SELECT
    column_name,
    RANK() OVER (
        ORDER BY column_name DESC
    ) AS Ranking
FROM table_name;
```

### Example

```sql
SELECT
    EmployeeName,
    Salary,
    RANK() OVER (
        ORDER BY Salary DESC
    ) AS SalaryRank
FROM Employees;
```

### Sample Output

| EmployeeName | Salary | SalaryRank |
|---|---:|---:|
| Rahul | 80000 | 1 |
| Priya | 70000 | 2 |
| Kiran | 70000 | 2 |
| Anjali | 60000 | 4 |
| Arjun | 50000 | 5 |

### Explanation

- Rahul receives rank 1.
- Priya and Kiran both receive rank 2.
- Rank 3 is skipped.
- Anjali receives rank 4.
- Arjun receives rank 5.

### Scenario-Based Example

**Scenario:** A company wants to rank employees according to salary. Employees with equal salaries should receive the same rank.

```sql
SELECT
    EmployeeName,
    Salary,
    RANK() OVER (
        ORDER BY Salary DESC
    ) AS SalaryRank
FROM Employees;
```

---

## 6.5 DENSE_RANK()

### Theory

DENSE_RANK() assigns the same rank to records with identical values.

Unlike RANK(), it does not skip the next rank after duplicate values.

### Syntax

```sql
SELECT
    column_name,
    DENSE_RANK() OVER (
        ORDER BY column_name DESC
    ) AS DenseRanking
FROM table_name;
```

### Example

```sql
SELECT
    EmployeeName,
    Salary,
    DENSE_RANK() OVER (
        ORDER BY Salary DESC
    ) AS SalaryRank
FROM Employees;
```

### Sample Output

| EmployeeName | Salary | SalaryRank |
|---|---:|---:|
| Rahul | 80000 | 1 |
| Priya | 70000 | 2 |
| Kiran | 70000 | 2 |
| Anjali | 60000 | 3 |
| Arjun | 50000 | 4 |

### Explanation

- Rahul receives rank 1.
- Priya and Kiran receive rank 2.
- Anjali receives rank 3.
- Arjun receives rank 4.

No rank is skipped.

### Scenario-Based Example

**Scenario:** The HR manager wants to identify the salary ranking of all employees without skipping ranks when multiple employees have the same salary.

```sql
SELECT
    EmployeeName,
    Salary,
    DENSE_RANK() OVER (
        ORDER BY Salary DESC
    ) AS SalaryRank
FROM Employees;
```

---

## 6.6 NTILE()

### Theory

NTILE() divides the rows into a specified number of approximately equal groups or buckets.

It assigns a bucket number to each row.

For example:
- NTILE(2) divides records into 2 groups.
- NTILE(3) divides records into 3 groups.
- NTILE(4) divides records into 4 groups.

### Syntax

```sql
SELECT
    column_name,
    NTILE(number_of_groups) OVER (
        ORDER BY column_name DESC
    ) AS BucketNumber
FROM table_name;
```

### Example

```sql
SELECT
    EmployeeName,
    Salary,
    NTILE(4) OVER (
        ORDER BY Salary DESC
    ) AS SalaryGroup
FROM Employees;
```

### Sample Output

| EmployeeName | Salary | SalaryGroup |
|---|---:|---:|
| Rahul | 80000 | 1 |
| Priya | 70000 | 1 |
| Kiran | 70000 | 2 |
| Anjali | 60000 | 3 |
| Arjun | 50000 | 4 |

*Note: When rows cannot be divided equally, some buckets contain one more row than others. NTILE distributes rows based on the ordering; it does not necessarily preserve identical salary values in the same bucket.*

### Scenario-Based Example

**Scenario:** An organization wants to divide employees into four performance groups based on their salary ranking.

```sql
SELECT
    EmployeeName,
    Salary,
    NTILE(4) OVER (
        ORDER BY Salary DESC
    ) AS SalaryCategory
FROM Employees;
```

---

## 6.7 Difference Between ROW_NUMBER(), RANK(), and DENSE_RANK()

Consider the following employee salary data:

| Employee | Salary |
|---|---:|
| A | 90000 |
| B | 80000 |
| C | 80000 |
| D | 70000 |
| E | 60000 |

### Comparison

| Employee | Salary | ROW_NUMBER | RANK | DENSE_RANK |
|---|---:|---:|---:|---:|
| A | 90000 | 1 | 1 | 1 |
| B | 80000 | 2 | 2 | 2 |
| C | 80000 | 3 | 2 | 2 |
| D | 70000 | 4 | 4 | 3 |
| E | 60000 | 5 | 5 | 4 |

### Key Differences

| Function | Duplicate Values | Skips Ranks |
|---|---|---|
| ROW_NUMBER() | Assigns unique numbers | No |
| RANK() | Assigns the same rank | Yes |
| DENSE_RANK() | Assigns the same rank | No |

### Important Interview Question

**Question: What is the difference between RANK() and DENSE_RANK()?**

Answer:

RANK() assigns the same rank to duplicate values but skips the subsequent rank numbers.

DENSE_RANK() also assigns the same rank to duplicate values but does not skip subsequent rank numbers.

---

# 7. Scenario-Based Ranking Queries

These are some of the most frequently used SQL ranking problems in interviews and real-world analytics.

## Scenario 1: Find the Highest-Paid Employee

```sql
SELECT *
FROM Employees
ORDER BY Salary DESC
LIMIT 1;
```

## Scenario 2: Find the Second-Highest Salary

```sql
SELECT MAX(Salary) AS SecondHighestSalary
FROM Employees
WHERE Salary < (
    SELECT MAX(Salary)
    FROM Employees
);
```

## Scenario 3: Find the Nth Highest Salary

Using DENSE_RANK():

```sql
SELECT *
FROM (
    SELECT
        EmployeeID,
        EmployeeName,
        Salary,
        DENSE_RANK() OVER (
            ORDER BY Salary DESC
        ) AS SalaryRank
    FROM Employees
) AS RankedEmployees
WHERE SalaryRank = 3;
```

This query identifies employees earning the third-highest distinct salary.

## Scenario 4: Find the Top 3 Employees in Each Department

```sql
SELECT *
FROM (
    SELECT
        EmployeeID,
        EmployeeName,
        Department,
        Salary,
        RANK() OVER (
            PARTITION BY Department
            ORDER BY Salary DESC
        ) AS DepartmentRank
    FROM Employees
) AS RankedEmployees
WHERE DepartmentRank <= 3;
```

## Scenario 5: Find Employees Having Duplicate Salaries

```sql
SELECT Salary, COUNT(*) AS EmployeeCount
FROM Employees
GROUP BY Salary
HAVING COUNT(*) > 1;
```

## Scenario 6: Find the Highest-Paid Employee in Each Department

```sql
SELECT *
FROM (
    SELECT
        EmployeeName,
        Department,
        Salary,
        ROW_NUMBER() OVER (
            PARTITION BY Department
            ORDER BY Salary DESC, EmployeeID ASC
        ) AS RowNum
    FROM Employees
) AS RankedEmployees
WHERE RowNum = 1;
```

---

# 8. SQL Logical Query Processing Order

SQL queries are written in a particular syntax order, but the database logically processes the clauses in a different order.

### Logical Processing Order

1. FROM
2. ON
3. JOIN
4. WHERE
5. GROUP BY
6. HAVING
7. SELECT
8. DISTINCT
9. ORDER BY
10. LIMIT / OFFSET

### Example

```sql
SELECT
    Department,
    AVG(Salary) AS AverageSalary
FROM Employees
WHERE Salary > 30000
GROUP BY Department
HAVING AVG(Salary) > 50000
ORDER BY AverageSalary DESC
LIMIT 5;
```

### Explanation

- FROM: Identifies the Employees table.
- WHERE: Filters employees earning more than 30,000.
- GROUP BY: Groups employees department-wise.
- HAVING: Keeps departments with an average salary above 50,000.
- SELECT: Retrieves department and average salary.
- ORDER BY: Sorts departments by average salary in descending order.
- LIMIT: Returns only the first 5 results.

---

# 9. Complete SQL Query Syntax

The following represents a common SELECT query structure:

```sql
SELECT [DISTINCT] column1, column2,
       AGGREGATE_FUNCTION(column3)

FROM table_name

JOIN another_table
ON table_name.id = another_table.id

WHERE condition

GROUP BY column1, column2

HAVING aggregate_condition

ORDER BY column1 ASC

LIMIT number OFFSET number;
```

*Note: JOIN, ON, LIMIT, and OFFSET syntax and availability can vary between database systems.*

---

# 10. Important Differences in SQL

## 10.1 DELETE vs TRUNCATE vs DROP

| Feature | DELETE | TRUNCATE | DROP |
|---|---|---|---|
| Removes records | Yes | Yes | Yes |
| Removes table structure | No | No | Yes |
| WHERE condition | Yes | No | No |
| Removes selected records | Yes | No | Entire table |
| Table remains available | Yes | Yes | No |
| Rollback support | Depends on transaction and database | Database-dependent | Database-dependent |

## 10.2 DDL vs DML vs DQL vs TCL

| Feature | DDL | DML | DQL | TCL |
|---|---|---|---|---|
| Full Form | Data Definition Language | Data Manipulation Language | Data Query Language | Transaction Control Language |
| Purpose | Structure management | Data modification | Data retrieval | Transaction management |
| Commands | CREATE, ALTER, DROP, TRUNCATE, RENAME | INSERT, UPDATE, DELETE | SELECT | COMMIT, ROLLBACK, SAVEPOINT |

---

# 11. TCL – Transaction Control Language

## 11.1 What is TCL?

TCL stands for **Transaction Control Language**.

TCL commands are used to manage transactions in a database.

A transaction is a logical unit of work that contains one or more SQL operations.

TCL helps maintain data consistency and integrity by controlling whether changes should be permanently saved or reversed.

### Important TCL Commands

1. COMMIT
2. ROLLBACK
3. SAVEPOINT

## 11.2 COMMIT

### Theory

COMMIT is used to permanently save the changes made during a transaction.

Once a transaction is committed, its changes become permanent according to the database's transaction behavior.

### Syntax

```sql
COMMIT;
```

### Example

```sql
START TRANSACTION;

UPDATE Employees
SET Salary = 70000
WHERE EmployeeID = 101;

COMMIT;
```

### Scenario-Based Example

**Scenario:** An employee receives a salary increment. After verifying the updated salary, the HR manager wants to save the changes permanently.

```sql
START TRANSACTION;

UPDATE Employees
SET Salary = 70000
WHERE EmployeeID = 101;

COMMIT;
```

## 11.3 ROLLBACK

### Theory

ROLLBACK is used to undo changes made during the current uncommitted transaction.

It restores the database to the state before the transaction began, or to the most recent savepoint when used with a savepoint.

### Syntax

```sql
ROLLBACK;
```

### Example

```sql
START TRANSACTION;

UPDATE Employees
SET Salary = 100000
WHERE EmployeeID = 101;

ROLLBACK;
```

### Scenario-Based Example

**Scenario:** The HR manager accidentally updates an employee's salary to ₹1,00,000 instead of ₹60,000. Before committing the transaction, they identify the mistake and roll back the changes.

```sql
START TRANSACTION;

UPDATE Employees
SET Salary = 100000
WHERE EmployeeID = 101;

ROLLBACK;
```

## 11.4 SAVEPOINT

### Theory

SAVEPOINT is used to create a temporary checkpoint inside a transaction.

It allows us to roll back only a specific part of a transaction instead of undoing the entire transaction.

### Syntax

```sql
SAVEPOINT savepoint_name;
```

To roll back to a savepoint:

```sql
ROLLBACK TO SAVEPOINT savepoint_name;
```

### Example

```sql
START TRANSACTION;

UPDATE Employees
SET Salary = 60000
WHERE EmployeeID = 101;

SAVEPOINT SalaryUpdated;

UPDATE Employees
SET Salary = 75000
WHERE EmployeeID = 102;

SAVEPOINT SecondSalaryUpdated;

ROLLBACK TO SAVEPOINT SalaryUpdated;

COMMIT;
```

### Explanation

1. A transaction is started.
2. Employee 101's salary is updated.
3. A savepoint is created.
4. Employee 102's salary is updated.
5. Another savepoint is created.
6. The transaction is rolled back to the first savepoint.
7. Employee 102's update is undone.
8. Employee 101's update remains.
9. COMMIT saves the remaining transaction changes.

### Scenario-Based Example

**Scenario:** A company updates the salaries of two employees. After updating the second employee's salary, HR identifies an error. They want to undo only the second employee's update while keeping the first employee's update.

```sql
START TRANSACTION;

UPDATE Employees
SET Salary = 65000
WHERE EmployeeID = 101;

SAVEPOINT FirstEmployeeUpdated;

UPDATE Employees
SET Salary = 80000
WHERE EmployeeID = 102;

ROLLBACK TO SAVEPOINT FirstEmployeeUpdated;

COMMIT;
```

### TCL Summary

| Command | Purpose |
|---|---|
| COMMIT | Permanently saves transaction changes |
| ROLLBACK | Undoes uncommitted changes |
| SAVEPOINT | Creates a checkpoint within a transaction |

### Important Note

Transaction behavior for DDL statements, TRUNCATE, and SAVEPOINT differs across database systems. For example, MySQL may implicitly commit certain DDL statements, whereas PostgreSQL supports transactional DDL in many cases.

---

# 12. Practice Dataset for SQL

Use the following table to practice the concepts explained above.

## Create Employee Table

```sql
CREATE TABLE Employees (
    EmployeeID INT PRIMARY KEY,
    EmployeeName VARCHAR(100),
    Department VARCHAR(50),
    Salary DECIMAL(10,2),
    JoiningDate DATE,
    City VARCHAR(50)
);
```

## Insert Sample Records

```sql
INSERT INTO Employees
(EmployeeID, EmployeeName, Department, Salary, JoiningDate, City)
VALUES
(101, 'Rahul', 'IT', 90000, '2022-01-15', 'Hyderabad'),
(102, 'Priya', 'HR', 80000, '2021-05-10', 'Bangalore'),
(103, 'Kiran', 'IT', 80000, '2023-03-20', 'Hyderabad'),
(104, 'Anjali', 'Finance', 70000, '2020-08-12', 'Chennai'),
(105, 'Arjun', 'IT', 60000, '2024-01-10', 'Hyderabad'),
(106, 'Sneha', 'HR', 60000, '2022-06-15', 'Bangalore'),
(107, 'Vikram', 'Finance', 50000, '2023-09-01', 'Chennai'),
(108, 'Meera', 'IT', 50000, '2021-11-25', 'Hyderabad'),
(109, 'Rohit', 'Finance', 40000, '2024-02-05', 'Mumbai'),
(110, 'Divya', 'HR', 40000, '2023-07-18', 'Bangalore');
```

---

# 13. SQL Practice Questions

Practice the following questions using the Employees table.

## Basic SQL Questions

1. Retrieve all records from the Employees table.
2. Retrieve only EmployeeName and Salary.
3. Find employees working in the IT department.
4. Find employees earning more than 50,000.
5. Find employees earning less than 60,000.
6. Display employees in ascending order of salary.
7. Display employees in descending order of salary.
8. Find employees working in Hyderabad.
9. Retrieve the first five employee records.
10. Find employees who joined after 2022.

## Aggregate Function Questions

11. Find the total number of employees.
12. Calculate the total salary of all employees.
13. Calculate the average salary.
14. Find the highest salary.
15. Find the lowest salary.
16. Count the number of employees in each department.
17. Calculate the average salary department-wise.
18. Find the total salary expenditure of each department.

## SQL Clause Questions

19. Find departments having more than two employees.
20. Find departments where average salary is greater than 60,000.
21. Retrieve employees whose names start with 'R'.
22. Find employees whose salary is between 40,000 and 80,000.
23. Retrieve employees working in IT or HR.
24. Find employees who are not from Hyderabad.
25. Retrieve employees whose names contain the letter 'a'.

## Ranking Function Questions

26. Assign a unique row number to every employee based on salary.
27. Rank employees based on salary using RANK().
28. Rank employees based on salary using DENSE_RANK().
29. Find the second-highest salary.
30. Find the third-highest distinct salary.
31. Find the highest-paid employee in each department.
32. Find the top three employees in each department.
33. Identify employees having duplicate salaries.
34. Divide employees into four salary groups using NTILE().
35. Find employees who share the same salary rank.

---

# 14. Real-World SQL Interview Scenarios

Here are additional problems commonly encountered in SQL interviews and analytics projects.

### Scenario 1: Employee Salary Analysis

A company wants to identify employees whose salaries are higher than the average salary of the entire organization.

```sql
SELECT *
FROM Employees
WHERE Salary > (
    SELECT AVG(Salary)
    FROM Employees
);
```

### Scenario 2: Department-Wise Highest Salary

Find the highest salary in every department.

```sql
SELECT
    Department,
    MAX(Salary) AS HighestSalary
FROM Employees
GROUP BY Department;
```

### Scenario 3: Second-Highest Salary in Each Department

```sql
SELECT *
FROM (
    SELECT
        EmployeeName,
        Department,
        Salary,
        DENSE_RANK() OVER (
            PARTITION BY Department
            ORDER BY Salary DESC
        ) AS SalaryRank
    FROM Employees
) AS DepartmentRanking
WHERE SalaryRank = 2;
```

### Scenario 4: Find Employees Earning More Than Their Department Average

```sql
SELECT *
FROM (
    SELECT
        EmployeeName,
        Department,
        Salary,
        AVG(Salary) OVER (
            PARTITION BY Department
        ) AS DepartmentAverage
    FROM Employees
) AS EmployeeAnalysis
WHERE Salary > DepartmentAverage;
```

### Scenario 5: Find the Number of Employees in Each City

```sql
SELECT
    City,
    COUNT(*) AS EmployeeCount
FROM Employees
GROUP BY City;
```

---

# 15. Important SQL Best Practices

1. Always use meaningful database and table names.
2. Prefer specifying column names when using INSERT.
3. Use WHERE conditions carefully in UPDATE and DELETE statements.
4. Avoid using SELECT * in production queries when only specific columns are required.
5. Use appropriate data types for each column.
6. Define PRIMARY KEY constraints to uniquely identify records.
7. Use FOREIGN KEY constraints to maintain relationships between tables.
8. Use aliases to make query outputs more readable.
9. Use transactions when performing multiple related data modifications.
10. Use EXPLAIN or the database's query-plan tools to analyze query performance.
11. Use indexes appropriately for frequently searched columns.
12. Always test destructive queries before executing them on production databases.

---

# 16. Quick SQL Revision Sheet

| Topic | Command / Function | Purpose |
|---|---|---|
| DDL | CREATE | Create database objects |
| DDL | ALTER | Modify structure |
| DDL | DROP | Remove database objects |
| DDL | TRUNCATE | Remove all records |
| DDL | RENAME | Rename objects |
| DML | INSERT | Insert records |
| DML | UPDATE | Update records |
| DML | DELETE | Delete records |
| DQL | SELECT | Retrieve records |
| DQL | DISTINCT | Retrieve unique values |
| Aggregate | COUNT() | Count records |
| Aggregate | SUM() | Calculate total |
| Aggregate | AVG() | Calculate average |
| Aggregate | MIN() | Find minimum |
| Aggregate | MAX() | Find maximum |
| Clause | WHERE | Filter records |
| Clause | GROUP BY | Group records |
| Clause | HAVING | Filter groups |
| Clause | ORDER BY | Sort records |
| Clause | LIMIT | Restrict records |
| Clause | OFFSET | Skip records |
| Operator | LIKE | Pattern matching |
| Operator | BETWEEN | Range filtering |
| Operator | IN | Match multiple values |
| Operator | IS NULL | Find missing values |
| Ranking | ROW_NUMBER() | Unique sequential numbering |
| Ranking | RANK() | Ranking with skipped numbers |
| Ranking | DENSE_RANK() | Ranking without skipped numbers |
| Ranking | NTILE() | Divide records into buckets |
| TCL | COMMIT | Save transaction |
| TCL | ROLLBACK | Undo transaction |
| TCL | SAVEPOINT | Create transaction checkpoint |

---

# Conclusion

SQL is one of the most important skills for anyone working in Data Analytics, Data Science, Data Engineering, and Business Intelligence.

Understanding DDL, DML, DQL, TCL, SQL Clauses, Aggregate Functions, and Ranking Functions provides a strong foundation for working with relational databases.

**Recommended Learning Approach:**

1. Understand DDL operations and table creation.
2. Practice DML operations with INSERT, UPDATE, and DELETE.
3. Master SELECT statements and aggregate functions.
4. Practice SQL clauses and filtering conditions.
5. Understand the difference between WHERE and HAVING.
6. Learn ranking functions and window functions.
7. Solve real-world scenario-based SQL interview questions.

**Practice consistently. Writing SQL queries yourself is the best way to master SQL!**

---

**Happy Learning! 🚀**

**SQL | Data Analytics | Data Science | Database Management**
