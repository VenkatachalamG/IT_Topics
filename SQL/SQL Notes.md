# 📘 SQL Notes

---

## 📘 Definition of SQL

**SQL (Structured Query Language)** is used to **communicate with databases**.

- Helps retrieve, insert, update, and delete data  
- Acts as a bridge between user/application and the database

---

## ❓ Why Use a Database?

- Can store **huge amounts of data**  
- **More secure** than file storage  
- **Fast and efficient** data storage and retrieval

---

## 💾 DBMS (Database Management System)

Software that:

- Handles all requests to a database from various sources  
- Manages the **priority** of requests  
- Ensures proper **execution** and data access  

---

## 🖥️ What is a Server?

- **Powerful machines** available *24/7*  
- They **host databases**  
- Can be **physical** or hosted on a **Cloud Service Provider (CSP)**

---

## 🗃️ Types of Databases

### 1. Relational
- Tables with **rows and columns**
- Tables can relate to each other using **keys**
- SQL-based

### 2. Key-Value
- Stores data in **key–value pairs** (like a dictionary)
- Fast for **simple lookups**

### 3. Column-Based
- Groups data by **columns**
- Efficient for **large datasets and analytics**

### 4. Graph
- Stores **relationships** between data
- Best for **networks**, **recommendations**

### 5. Document
- Stores data as **documents** (e.g., JSON, BSON)
- Schema-less and flexible

---

### 🔍 Examples:

| Type       | Example DBs                         |
|------------|--------------------------------------|
| Relational | Microsoft SQL, PostgreSQL            |
| Key-Value  | Redis, Amazon DynamoDB               |
| Column     | Apache Cassandra, Amazon Redshift    |
| Graph      | Neo4j                                |
| Document   | MongoDB                              |

---

## 🧱 Database Hierarchy

SERVER
└── DATABASES
└── SCHEMAS (e.g., TEACHERS, STUDENTS)
└── TABLES
└── ROWS & COLUMNS

pgsql
Copy
Edit

---

## 📄 Tables

- A **collection of rows (records)** and **columns (fields)**
- Each **row** = one **entity**
- Each **column** = one **attribute/field**
- **Cell** = Intersection of row and column
- Contains a **Primary Key** (unique identifier)
- Holds various data types: `Numeric`, `Text`, `Date`, `Time`, etc.

---

## ⚙️ Types of SQL Commands

---

### 1. DDL – Data Definition Language

*Used to define or modify database structure.*

```sql
-- Create a new table
CREATE TABLE students (
    id INT PRIMARY KEY,
    name VARCHAR(50)
);

-- Alter a table
ALTER TABLE students ADD age INT;

-- Drop a table
DROP TABLE students;
🛑 Rule
CREATE
Attempting to CREATE a table that already exists will throw an error.

ALTER
ALTER allows structural changes like adding or removing columns.

DROP
DROP will remove the structure and all data from the table.

2. DML – Data Manipulation Language
Used to modify data in tables.

💻 SQL Examples
sql
Copy
Edit
-- Insert data
INSERT INTO students (id, name)
VALUES (1, 'John');

-- Update data
UPDATE students
SET name = 'Alice'
WHERE id = 1;

-- Delete data
DELETE FROM students
WHERE id = 1;
🔧 Command Summary
INSERT – Add a new record

UPDATE – Modify existing data

DELETE – Remove a record

⚠️ Rules
Always use WHERE with UPDATE and DELETE to avoid affecting all rows.

VALUES must match the order and type of columns in the table.

3. DQL – Data Query Language
Used to retrieve data from tables.

💻 SQL Examples
sql
Copy
Edit
-- Select all columns
SELECT * FROM students;

-- Select specific column
SELECT name FROM students;
📋 Command Summary
SELECT – Used to fetch data from tables

Can be combined with clauses: WHERE, ORDER BY, GROUP BY, HAVING, LIMIT, etc.

⚠️ Rules
Use * to select all columns, or list specific columns for better performance.

Combine SELECT with conditions to filter, sort, and aggregate data.

📌 Quick Summary of SQL Commands
Category	Command	Purpose
DDL	CREATE	Create new tables/databases
ALTER	Modify structure of tables
DROP	Delete tables/databases
DML	INSERT	Add new data
UPDATE	Change existing data
DELETE	Remove data
DQL	SELECT	Query and retrieve data

📎 Reference Link
To check SQL Commands, click here:
SQL Command <!-- Replace `#` with the actual URL if available -->