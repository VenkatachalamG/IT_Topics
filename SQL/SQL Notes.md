<h1>📘 SQL Notes</h1>

<hr>

<h2>📘 Definition of SQL</h2>

<p><strong>SQL (Structured Query Language)</strong> is used to <strong>communicate with databases</strong>.</p>

<ul>
  <li>Helps retrieve, insert, update, and delete data</li>
  <li>Acts as a bridge between user/application and the database</li>
</ul>

<hr>

<h2>❓ Why Use a Database?</h2>

<ul>
  <li>Can store <strong>huge amounts of data</strong></li>
  <li><strong>More secure</strong> than file storage</li>
  <li><strong>Fast and efficient</strong> data storage and retrieval</li>
</ul>

<hr>

<h2>💾 DBMS (Database Management System)</h2>

<p>Software that:</p>

<ul>
  <li>Handles all requests to a database from various sources</li>
  <li>Manages the <strong>priority</strong> of requests</li>
  <li>Ensures proper <strong>execution</strong> and data access</li>
</ul>

<hr>

<h2>🖥️ What is a Server?</h2>

<ul>
  <li><strong>Powerful machines</strong> available <em>24/7</em></li>
  <li>They <strong>host databases</strong></li>
  <li>Can be <strong>physical</strong> or hosted on a <strong>Cloud Service Provider (CSP)</strong></li>
</ul>

<hr>

<h2>🗃️ Types of Databases</h2>

<h3>1. Relational</h3>
<ul><li>Tables with <strong>rows and columns</strong></li>
<li>Tables can relate using <strong>keys</strong></li>
<li>SQL-based</li></ul>

<h3>2. Key-Value</h3>
<ul><li>Stores data in <strong>key–value pairs</strong></li>
<li>Fast for <strong>simple lookups</strong></li></ul>

<h3>3. Column-Based</h3>
<ul><li>Groups data by <strong>columns</strong></li>
<li>Efficient for <strong>large datasets and analytics</strong></li></ul>

<h3>4. Graph</h3>
<ul><li>Stores <strong>relationships</strong> between data</li>
<li>Best for <strong>networks</strong>, <strong>recommendations</strong></li></ul>

<h3>5. Document</h3>
<ul><li>Stores data as <strong>documents</strong> (e.g., JSON, BSON)</li>
<li>Schema-less and flexible</li></ul>

<h3>🔍 Examples:</h3>

<table>
  <thead>
    <tr>
      <th>Type</th>
      <th>Example DBs</th>
    </tr>
  </thead>
  <tbody>
    <tr><td>Relational</td><td>Microsoft SQL, PostgreSQL</td></tr>
    <tr><td>Key-Value</td><td>Redis, Amazon DynamoDB</td></tr>
    <tr><td>Column</td><td>Apache Cassandra, Amazon Redshift</td></tr>
    <tr><td>Graph</td><td>Neo4j</td></tr>
    <tr><td>Document</td><td>MongoDB</td></tr>
  </tbody>
</table>

<hr>

<h2>🧱 Database Hierarchy</h2>

<pre>
SERVER
└── DATABASES
    └── SCHEMAS (e.g., TEACHERS, STUDENTS)
        └── TABLES
            └── ROWS & COLUMNS
</pre>

<hr>

<h2>📄 Tables</h2>

<ul>
  <li>A <strong>collection of rows (records)</strong> and <strong>columns (fields)</strong></li>
  <li>Each <strong>row</strong> = one <strong>entity</strong></li>
  <li>Each <strong>column</strong> = one <strong>attribute/field</strong></li>
  <li><strong>Cell</strong> = Intersection of row and column</li>
  <li>Contains a <strong>Primary Key</strong> (unique identifier)</li>
  <li>Holds various data types: <code>Numeric</code>, <code>Text</code>, <code>Date</code>, <code>Time</code>, etc.</li>
</ul>

<hr>

<h2>⚙️ Types of SQL Commands</h2>

<h3>1. DDL – Data Definition Language</h3>
<p><em>Used to define or modify database structure.</em></p>

<pre><code>-- Create a new table
CREATE TABLE students (
    id INT PRIMARY KEY,
    name VARCHAR(50)
);

-- Alter a table
ALTER TABLE students ADD age INT;

-- Drop a table
DROP TABLE students;
</code></pre>

<h4>🛑 Rule</h4>
<ul>
  <li><strong>CREATE</strong> – Attempting to create a table that already exists will throw an error.</li>
  <li><strong>ALTER</strong> – Allows structural changes like adding/removing columns.</li>
  <li><strong>DROP</strong> – Deletes the table structure and all data inside.</li>
</ul>

<h3>2. DML – Data Manipulation Language</h3>
<p><em>Used to modify data in tables.</em></p>

<pre><code>-- Insert data
INSERT INTO students (id, name)
VALUES (1, 'John');

-- Update data
UPDATE students
SET name = 'Alice'
WHERE id = 1;

-- Delete data
DELETE FROM students
WHERE id = 1;
</code></pre>

<h4>🔧 Command Summary</h4>
<ul>
  <li><strong>INSERT</strong> – Add a new record</li>
  <li><strong>UPDATE</strong> – Modify existing data</li>
  <li><strong>DELETE</strong> – Remove a record</li>
</ul>

<h4>⚠️ Rules</h4>
<ul>
  <li>Always use <code>WHERE</code> with <code>UPDATE</code> and <code>DELETE</code> to avoid affecting all rows.</li>
  <li><code>VALUES</code> must match the order and type of columns in the table.</li>
</ul>

<h3>3. DQL – Data Query Language</h3>
<p><em>Used to retrieve data from tables.</em></p>

<pre><code>-- Select all columns
SELECT * FROM students;

-- Select specific column
SELECT name FROM students;
</code></pre>

<h4>📋 Command Summary</h4>
<ul>
  <li><strong>SELECT</strong> – Used to fetch data from tables</li>
  <li>Can be combined with clauses: <code>WHERE</code>, <code>ORDER BY</code>, <code>GROUP BY</code>, <code>HAVING</code>, <code>LIMIT</code>, etc.</li>
</ul>

<h4>⚠️ Rules</h4>
<ul>
  <li>Use <code>*</code> to select all columns, or list specific ones for performance and clarity.</li>
  <li>Combine <code>SELECT</code> with filters to get targeted data.</li>
</ul>

<hr>

<h2>📌 Quick Summary of SQL Commands</h2>

<table>
  <thead>
    <tr>
      <th>Category</th>
      <th>Command</th>
      <th>Purpose</th>
    </tr>
  </thead>
  <tbody>
    <tr><td>DDL</td><td>CREATE</td><td>Create new tables/databases</td></tr>
    <tr><td>DDL</td><td>ALTER</td><td>Modify structure of tables</td></tr>
    <tr><td>DDL</td><td>DROP</td><td>Delete tables/databases</td></tr>
    <tr><td>DML</td><td>INSERT</td><td>Add new data</td></tr>
    <tr><td>DML</td><td>UPDATE</td><td>Change existing data</td></tr>
    <tr><td>DML</td><td>DELETE</td><td>Remove data</td></tr>
    <tr><td>DQL</td><td>SELECT</td><td>Query and retrieve data</td></tr>
  </tbody>
</table>

<p>📎 Reference Link<br>
To check SQL Commands, click here: <a href="SQL Commands">SQL Command</a></p>