<h1>🧩 SQL Conditionals & Operators</h1>

<hr>

<h2>📝 Definition</h2>
<p>
  SQL conditionals are special operators used to <strong>filter</strong> and <strong>evaluate</strong> columns
  based on conditions.
</p>

<hr>

<h2>🔧 Types of SQL Operators</h2>
<ul>
  <li><strong>Comparison Operators</strong>: <code>=</code>, <code>&lt;</code>, <code>&gt;</code>, <code>&gt;=</code>, <code>&lt;=</code>, <code>!=</code>, <code>&lt;&gt;</code></li>
  <li><strong>Logical Operators</strong>: <code>AND</code>, <code>OR</code>, <code>NOT</code></li>
  <li><strong>Range Operator</strong>: <code>BETWEEN</code></li>
  <li><strong>Membership Operators</strong>: <code>IN</code>, <code>NOT IN</code></li>
  <li><strong>Search Operator</strong>: <code>LIKE</code></li>
</ul>

<hr>

<h2>⚖️ Comparison Operators</h2>

<p><strong>Purpose:</strong> Used to compare two values.</p>

<p><strong>Syntax:</strong></p>
<pre><code>
&lt;expression&gt; &lt;operator&gt; &lt;expression&gt;
</code></pre>

<h3>📌 Example Queries</h3>
<pre><code class="sql">
-- Employees with name 'John'
SELECT * FROM employees
WHERE first_name = 'John';

-- Products with price not equal to 500
SELECT name, price FROM products
WHERE price != 500;

-- Customers older than 30
SELECT * FROM customers
WHERE age > 30;

-- Books cheaper than or equal to ₹400
SELECT title, price FROM books
WHERE price <= 400;
</code></pre>

<hr>

<h2>🧠 Logical Operators</h2>

<p>Combine multiple conditions using boolean logic.</p>

<ul>
  <li><strong>AND</strong> – Returns <code>TRUE</code> only if all conditions are <code>TRUE</code></li>
  <li><strong>OR</strong> – Returns <code>TRUE</code> if any condition is <code>TRUE</code></li>
  <li><strong>NOT</strong> – Reverses the logical result</li>
</ul>

<h3>✅ Example Queries</h3>
<pre><code class="sql">
-- High-scoring students from India
SELECT * FROM students
WHERE country = 'India' AND score > 90;

-- Employees in HR or Admin department
SELECT * FROM employees
WHERE department = 'HR' OR department = 'Admin';

-- Customers not from USA
SELECT * FROM customers
WHERE NOT country = 'USA';
</code></pre>

<hr>

<h2>📏 Range Operator – BETWEEN</h2>

<p><strong>Purpose:</strong> Checks if a value falls within a range.</p>

<pre><code class="sql">
-- Products priced between 1000 and 3000
SELECT name, price FROM products
WHERE price BETWEEN 1000 AND 3000;

-- Alternate of BETWEEN operator is to use Comparison Operators
SELECT name, marks FROM students
WHERE marks >=70 AND marks <= 90;
</code></pre>

<hr>

<h2>🧮 Membership Operators – IN / NOT IN</h2>

<p><strong>IN</strong> – Returns <code>TRUE</code> if the value exists in the list</p>
<p><strong>NOT IN</strong> – Returns <code>TRUE</code> if the value does <em>not</em> exist in the list</p>

<pre><code class="sql">
-- Customers from selected countries
SELECT * FROM customers
WHERE country IN ('USA', 'Canada', 'UK');

-- Exclude certain job roles
SELECT * FROM employees
WHERE role NOT IN ('Intern', 'Contractor');
</code></pre>

<hr>

<h2>🔎 Search Operator – LIKE</h2>

<p><strong>Purpose:</strong> Used to search for patterns in a column.</p>

<pre><code class="sql">
-- Names starting with 'M'
SELECT * FROM students
WHERE first_name LIKE 'M%';

-- Emails containing 'gmail'
SELECT * FROM users
WHERE email LIKE '%gmail%';

-- Names ending in 'son'
SELECT * FROM customers
WHERE last_name LIKE '%son';
</code></pre>

<h3>🧷 Wildcard Symbols:</h3>
<ul>
  <li><code>%</code> → Zero or more characters</li>
  <li><code>_</code> → Exactly one character</li>
</ul>

<h3>💡 LIKE Pattern Matching Table:</h3>

<table>
  <thead>
    <tr>
      <th>Pattern</th>
      <th>Matches</th>
      <th>Doesn't Match</th>
    </tr>
  </thead>
  <tbody>
    <tr><td><code>M%</code></td><td>Maria, Ma, M</td><td>Emma</td></tr>
    <tr><td><code>%in</code></td><td>Martin, Vin</td><td>Jasmine</td></tr>
    <tr><td><code>%a%</code></td><td>Maria, Peter, Rayn</td><td>R</td></tr>
    <tr><td><code>%r%</code></td><td>Rayn</td><td>Alice</td></tr>
  </tbody>
</table>
