<h1>🧩 SQL Set Operations</h1>

<hr>

<h2>📌 Definition</h2>
<blockquote>
Set operations in SQL combine the result of multiple queries into a single result set.
</blockquote>

<hr>

<h2>🧾 SQL Set Operator Syntax</h2>

<p><strong>General Syntax:</strong></p>

<pre><code>query
&lt;set operator&gt;
query
</code></pre>

<h3>🧠 Example:</h3>

<pre><code>SELECT f_name, l_name
FROM customers

UNION

SELECT id, order_date
FROM orders
</code></pre>

<hr>

<h2>✅ Rules for Using SQL Set Operators</h2>

<h3>🔹 Rule 1 → SQL Clauses</h3>
<ul>
  <li>Set operators can be used with: <code>WHERE</code>, <code>JOIN</code>, <code>GROUP BY</code>, <code>HAVING</code></li>
  <li>❗ <strong>Exception</strong>: <code>ORDER BY</code> can be used <strong>only once</strong> and <strong>at the end</strong> of the full query</li>
</ul>

<h4>✅ Example:</h4>

<pre><code>SELECT f_name, l_name
FROM customers
JOIN ...
WHERE ...

UNION

SELECT f_name, l_name
FROM employees
JOIN ...
WHERE ...

ORDER BY f_name;
</code></pre>

<hr>

<h3>🔹 Rule 2 → Column Numbers</h3>
<ul>
  <li>Each query must return the <strong>same number of columns</strong>.</li>
</ul>

<hr>

<h3>🔹 Rule 3 → Data Types</h3>
<ul>
  <li>Corresponding columns <strong>must have compatible data types</strong>.</li>
</ul>

<h4>⚠️ Example:</h4>

<pre><code>-- varchar type
SELECT f_name, l_name
FROM customers

UNION

-- INT type causes mismatch
SELECT f_name, e_id
FROM employees
</code></pre>

<hr>

<h3>🔹 Rule 4 → Order of Columns</h3>
<ul>
  <li>Column order must be <strong>exactly the same</strong> in all queries.</li>
</ul>

<hr>

<h3>🔹 Rule 5 → Aliases</h3>
<ul>
  <li><strong>First query</strong> determines the <strong>column names</strong> of the result set.</li>
  <li>✅ If using aliases, <strong>use them in the first SELECT</strong>.</li>
</ul>

<hr>

<h3>🔹 Rule 6 → Correct Columns</h3>
<ul>
  <li>SQL <strong>does not understand</strong> the meaning of content in columns.</li>
  <li>You must ensure the <strong>correct column selection</strong> manually.</li>
</ul>

<hr>

<h2>🧮 Types of Set Operators</h2>

<h3>① UNION</h3>
<blockquote>Returns all <strong>distinct</strong> rows from both queries.</blockquote>
<ul>
  <li>📝 Query order does <strong>not</strong> matter.</li>
</ul>

<h3>② UNION ALL</h3>
<blockquote>Returns all rows from both queries <strong>including duplicates</strong>.</blockquote>
<ul>
  <li>📝 Use <code>UNION ALL</code> when:
    <ul>
      <li>You want <strong>faster results</strong></li>
      <li>You <strong>don't care</strong> about duplicates</li>
    </ul>
  </li>
  <li>You can check for duplicates <strong>afterward</strong> using filtering logic.</li>
</ul>

<h3>③ EXCEPT</h3>
<blockquote>Returns rows from the <strong>first query</strong> that are <strong>not</strong> in the second.</blockquote>
<ul>
  <li>🧠 <strong>Order of queries is important</strong></li>
</ul>

<h3>④ INTERSECT</h3>
<blockquote>Returns rows that are <strong>common</strong> to both queries.</blockquote>

<hr>

<h2>💡 Why Use Set Operators?</h2>

<ul>
  <li>🔁 Remove <strong>query redundancy</strong></li>
  <li>📦 Combine information into a <strong>single result</strong></li>
  <li>⚡ Improve <strong>performance</strong> or <strong>archiving</strong> by splitting data into multiple tables</li>
</ul>

<hr>

<h2>📉 Visualization</h2>

<pre><code>
Multiple Tables
   ↓
Set Operation
   ↓
One Simple Table
   ↓
Report
</code></pre>

<hr>

<h2>⚠️ Notes and Extra Tips</h2>

<ul>
  <li>🚫 Do <strong>not</strong> use <code>ORDER BY</code> in intermediate queries involving set operators</li>
  <li>🔍 Use aliases like <code>AS SourceTable</code> to trace errors back to the source</li>
  <li>✅ Use <code>EXCEPT</code> for:
    <ul>
      <li>✔️ Data completeness checks</li>
      <li>✔️ Data migration validation</li>
    </ul>
  </li>
</ul>

<h3>🧪 Example Use of <code>EXCEPT</code> for Data Validation</h3>

<pre><code>
Database A          Database B
 TABLE 1    ─────→   TABLE 2

Validation:
TABLE 1
 EXCEPT
TABLE 2   →  Empty = Correct

TABLE 2
 EXCEPT
TABLE 1   →  Empty = Correct
</code></pre>

<h2>📎 Reference</h2>
<p>Check out the full SQL Notes: <a href="SQL Notes.md">SQL Notes</a></p>
