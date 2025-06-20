<h1>SELECT</h1>
<p>Used to retrieve data from tables.</p>
<pre><code class="sql">
SELECT [columns / *] FROM [table_name];
-- * selects all columns
</code></pre>

<h2>WHERE Clause</h2>
<p>Filters data based on a condition.</p>
<pre><code class="sql">
SELECT name FROM customers
WHERE country = 'India';
</code></pre>

<h2>ORDER BY Clause</h2>
<p>Sorts query results.</p>
<pre><code class="sql">
SELECT [record]
FROM [table_name]
ORDER BY [field] [ASC | DESC];
</code></pre>
<p><b>⚠️ Rule:</b> Default is <b>ASC</b> (ascending), but always mention ASC/DESC to avoid confusion.</p>

<h2>GROUP BY Clause</h2>
<p>Used to aggregate rows with the same value and return grouped records.</p>
<pre><code class="sql">
SELECT country, SUM(score)
FROM customers
GROUP BY country;
</code></pre>

<h2>Aliasing in GROUP BY</h2>
<pre><code class="sql">
SELECT country, SUM(score) AS total, COUNT(id)
FROM customers
GROUP BY COUNT(id), country;
</code></pre>
<ul>
    <li><code>AS total</code> gives a name to the aggregated field</li>
    <li>Alias is only for the output, doesn’t affect the table</li>
    <li><code>COUNT()</code> can be used for unique fields like <code>id</code>, <code>name</code>, etc.</li>
</ul>
<p><b>⚠️ Rule:</b> All selected fields must be in the <code>GROUP BY</code> clause or it will throw an error.</p>

<h2>HAVING Clause</h2>
<p>Used to filter groups after aggregation.</p>
<pre><code class="sql">
SELECT [columns/*]
FROM [table_name]
WHERE [condition]
GROUP BY [field_name / column]
HAVING [condition];
</code></pre>
<ul>
    <li>Works with aggregate functions: <code>COUNT()</code>, <code>SUM()</code>, <code>AVG()</code>, etc.</li>
    <li>Comes after <code>GROUP BY</code> in query order</li>
    <li>Filters aggregated results like WHERE does for individual rows</li>
</ul>
<p><b>⚠️ Rule:</b> You cannot use <code>HAVING</code> without <code>GROUP BY</code> unless you're aggregating the entire table.</p>

<h2>DISTINCT</h2>
<p>Used to return only unique values.</p>
<pre><code class="sql">
SELECT DISTINCT [field / column(s)]
FROM [table_name];
</code></pre>
<ul>
    <li>Eliminates duplicate rows</li>
    <li>Can be used with one or more columns</li>
    <li>Applies to all columns listed after it</li>
</ul>
<pre><code class="sql">
SELECT DISTINCT name FROM employees;
</code></pre>
<p><b>⚠️ Rule:</b> <code>DISTINCT</code> applies to all selected columns, not just the first one.</p>

<h2>TOP</h2>
<p>Limits the number of rows returned.</p>
<pre><code class="sql">
SELECT TOP (n)
[field / column(s)]
FROM [table_name];
</code></pre>
<pre><code class="sql">
SELECT TOP 5 * FROM employees ORDER BY salary DESC;
</code></pre>
<ul>
    <li>Commonly used for previewing or pagination</li>
    <li>Works best with <code>ORDER BY</code></li>
</ul>
<p><b>⚠️ Rule:</b> Without <code>ORDER BY</code>, the rows returned by <code>TOP</code> are not consistent.</p>

<h2>CREATE</h2>
<p>Used to create new database objects.</p>
<pre><code class="sql">
CREATE TABLE [table_name] (
    column1 datatype,
    column2 datatype,
    ...
);
</code></pre>
<ul>
    <li>Creates tables, views, indexes, etc.</li>
    <li>Must include column names and their data types</li>
    <li>Can include constraints: <code>PRIMARY KEY</code>, <code>NOT NULL</code>, <code>UNIQUE</code>, etc.</li>
</ul>
<p><b>⚠️ Rule:</b> <code>CREATE TABLE</code> fails if table already exists (unless <code>IF NOT EXISTS</code> is used).</p>

<h2>DROP</h2>
<p>Used to permanently remove database objects.</p>
<pre><code class="sql">
-- Drop table
DROP TABLE [table_name];

-- Drop column
ALTER TABLE [table_name] DROP COLUMN [column_name];
</code></pre>
<pre><code class="sql">
-- Example 1
DROP TABLE employees;

-- Example 2
ALTER TABLE employees DROP COLUMN salary;
</code></pre>
<p><b>⚠️ Rule:</b> 
<ul>
    <li><code>DROP TABLE</code> removes both structure and data permanently</li>
    <li><code>DROP COLUMN</code> may not be supported in older DBs</li>
    <li>Use <code>IF EXISTS</code> to avoid errors</li>
</ul>
</p>

<h2>INSERT</h2>
<p>Used to add new rows to a table.</p>
<pre><code class="sql">
-- All columns
INSERT INTO [table_name]
VALUES (value1, value2, ...);

-- Specific columns
INSERT INTO [table_name] (column1, column2)
VALUES (value1, value2);
</code></pre>
<pre><code class="sql">
-- Example
INSERT INTO employees (id, name, salary)
VALUES (101, 'Alice', 50000);
</code></pre>
<p><b>⚠️ Rule:</b> 
<ul>
    <li>If columns not specified, values must match all columns in order</li>
    <li>Use <code>NULL</code> if column allows it</li>
</ul>
</p>

<h2>UPDATE</h2>
<p>Used to modify existing rows in a table.</p>
<pre><code class="sql">
UPDATE [table_name]
SET column1 = value1, column2 = value2
WHERE [condition];
</code></pre>
<pre><code class="sql">
-- Example
UPDATE employees
SET salary = 60000
WHERE id = 101;
</code></pre>
<p><b>⚠️ Rule:</b> 
<ul>
    <li>Always use <code>WHERE</code> to avoid updating all rows</li>
    <li>You can use subqueries or expressions in <code>SET</code></li>
</ul>
</p>

<h2>DELETE & TRUNCATE</h2>
<p>Used to remove rows from a table.</p>
<pre><code class="sql">
-- Delete specific rows
DELETE FROM [table_name]
WHERE [condition];

-- Delete all rows
TRUNCATE TABLE [table_name];
</code></pre>
<pre><code class="sql">
-- Example
DELETE FROM employees WHERE id = 101;
TRUNCATE TABLE employees;
</code></pre>
<p><b>⚠️ Rule:</b> 
<ul>
    <li><code>DELETE</code> can be rolled back; <code>TRUNCATE</code> often cannot</li>
    <li><code>TRUNCATE</code> resets auto-increment values</li>
    <li><code>DELETE</code> is row-by-row, slower but safer</li>
    <li>Use <code>WHERE</code> to limit deletions in <code>DELETE</code></li>
</ul>
</p>

<h1>📦 Summary Table</h1>
<table>
    <thead>
        <tr>
            <th>Clause / Command</th>
            <th>Purpose</th>
        </tr>
    </thead>
    <tbody>
        <tr><td>SELECT</td><td>Retrieve data</td></tr>
        <tr><td>WHERE</td><td>Filter records</td></tr>
        <tr><td>ORDER BY</td><td>Sort data</td></tr>
        <tr><td>GROUP BY</td><td>Group rows for aggregation</td></tr>
        <tr><td>HAVING</td><td>Filter after aggregation</td></tr>
        <tr><td>DISTINCT</td><td>Eliminate duplicates</td></tr>
        <tr><td>TOP</td><td>Limit number of rows</td></tr>
        <tr><td>CREATE</td><td>Create tables and objects</td></tr>
        <tr><td>DROP</td><td>Delete tables or columns</td></tr>
        <tr><td>INSERT</td><td>Add new rows</td></tr>
        <tr><td>UPDATE</td><td>Modify data</td></tr>
        <tr><td>DELETE</td><td>Remove specific data</td></tr>
        <tr><td>TRUNCATE</td><td>Quickly delete all rows</td></tr>
    </tbody>
</table>

<h2>📎 Reference</h2>
<p>Check out the SQL notes here: <a href="SQL/SQL Notes.md">SQL Notes</a></p>
