# 📘 SQL Syntax Reference Guide

A comprehensive summary of essential SQL commands, rules, and examples.

---

## 🔎 SELECT

**Used to retrieve data.**

```sql
SELECT [columns / *] FROM [table_name];
-- * selects all columns
🔍 WHERE Clause
Filters data based on condition.

sql
Copy
Edit
SELECT name FROM customers
WHERE country = 'India';
📊 ORDER BY Clause
Sorts data.

sql
Copy
Edit
SELECT [record]
FROM [table_name]
ORDER BY [field] [ASC | DESC];
⚠️ Rule:
Default is ASC (ascending), but always mention ASC/DESC to avoid confusion.

🧮 GROUP BY Clause
Used to aggregate rows with the same value and return grouped records.

sql
Copy
Edit
SELECT country, SUM(score)
FROM customers
GROUP BY country;
✏️ Aliasing in GROUP BY
sql
Copy
Edit
SELECT country, SUM(score) AS total, COUNT(id) 
FROM customers
GROUP BY COUNT(id), country;
AS total gives a name to the aggregated field

Alias is only for the output, doesn’t affect the table

COUNT can be used for unique fields like id, name, etc.

⚠️ Rule:
All selected fields must be in the GROUP BY clause or it will throw an error.

🧱 HAVING Clause
Used to filter groups after aggregation.

sql
Copy
Edit
SELECT [columns/*]
FROM [table_name]
WHERE [condition]
GROUP BY [field_name / column]
HAVING [condition];
Works with aggregate functions: COUNT(), SUM(), AVG(), etc.

Comes after GROUP BY in query order

Filters aggregated results like WHERE does for individual rows

⚠️ Rule:
You cannot use HAVING without GROUP BY unless you're aggregating the entire table.

🔁 DISTINCT
Used to return only unique values.

sql
Copy
Edit
SELECT DISTINCT [field / column(s)]
FROM [table_name];
Eliminates duplicate rows

Can be used with one or more columns

Applies to all columns listed after it

Example:
SELECT DISTINCT name FROM employees;

⚠️ Rule:
DISTINCT applies to all selected columns, not just the first one.

🔢 TOP
Limits the number of rows returned.

sql
Copy
Edit
SELECT TOP (n)
[field / column(s)]
FROM [table_name];
Example:
SELECT TOP 5 * FROM employees ORDER BY salary DESC;

Commonly used for previewing or pagination

Works best with ORDER BY

⚠️ Rule:
Without ORDER BY, the rows returned by TOP are not consistent

🏗️ CREATE
Used to create new database objects.

sql
Copy
Edit
CREATE TABLE [table_name] (
    column1 datatype,
    column2 datatype,
    ...
);
Creates tables, views, indexes, etc.

Must include column names and their data types

Can include constraints: PRIMARY KEY, NOT NULL, UNIQUE, etc.

⚠️ Rule:
CREATE TABLE fails if table already exists (unless IF NOT EXISTS is used)

🗑️ DROP
Used to permanently remove database objects.

sql
Copy
Edit
-- Drop table
DROP TABLE [table_name];

-- Drop column
ALTER TABLE [table_name] DROP COLUMN [column_name];
Example 1:

sql
Copy
Edit
DROP TABLE employees;
Example 2:

sql
Copy
Edit
ALTER TABLE employees DROP COLUMN salary;
⚠️ Rule:
DROP TABLE removes both structure and data permanently

DROP COLUMN may not be supported in older DBs

Use IF EXISTS to avoid errors

➕ INSERT
Used to add new rows to a table.

sql
Copy
Edit
-- All columns
INSERT INTO [table_name]
VALUES (value1, value2, ...);

-- Specific columns
INSERT INTO [table_name] (column1, column2)
VALUES (value1, value2);
Example:

sql
Copy
Edit
INSERT INTO employees (id, name, salary)
VALUES (101, 'Alice', 50000);
⚠️ Rule:
If columns not specified, values must match all columns in order

Use NULL if column allows it

🛠️ UPDATE
Used to modify existing rows in a table.

sql
Copy
Edit
UPDATE [table_name]
SET column1 = value1, column2 = value2
WHERE [condition];
Example:

sql
Copy
Edit
UPDATE employees
SET salary = 60000
WHERE id = 101;
⚠️ Rule:
Always use WHERE to avoid updating all rows

You can use subqueries or expressions in SET

🧹 DELETE & TRUNCATE
Used to remove rows from a table.

sql
Copy
Edit
-- Delete specific rows
DELETE FROM [table_name]
WHERE [condition];

-- Delete all rows
TRUNCATE TABLE [table_name];
Example:

sql
Copy
Edit
DELETE FROM employees WHERE id = 101;
TRUNCATE TABLE employees;
⚠️ Rule:
DELETE can be rolled back; TRUNCATE often cannot

TRUNCATE resets auto-increment values

DELETE is row-by-row, slower but safer

Use WHERE to limit deletions in DELETE

📦 Summary Table
Clause / Command	Purpose
SELECT	Retrieve data
WHERE	Filter records
ORDER BY	Sort data
GROUP BY	Group rows for aggregation
HAVING	Filter after aggregation
DISTINCT	Eliminate duplicates
TOP	Limit number of rows
CREATE	Create tables and objects
DROP	Delete tables or columns
INSERT	Add new rows
UPDATE	Modify data
DELETE	Remove specific data
TRUNCATE	Quickly delete all rows

📎 Reference
Check out more on SQL commands here: