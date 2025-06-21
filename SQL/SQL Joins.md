<h2>🔷 What is a Join?</h2>
<blockquote>In SQL, Joins are used to combine rows from two or more tables, based on a related column (called a key).</blockquote>

<hr>

<h3>🔄 <strong>Combine by?</strong></h3>
<ul>
  <li>➡️ <strong>Rows</strong> → SET operations (<code>UNION</code>, <code>INTERSECT</code>, etc.)</li>
  <li>➡️ <strong>Columns</strong> → JOINS (<code>INNER</code>, <code>LEFT</code>, etc.)</li>
</ul>

<hr>

<h2>📚 Types of Joins and Set Operations</h2>

<h3>🔗 JOINS</h3>
<ul>
  <li><strong>INNER JOIN</strong> 🔄 Matching rows</li>
  <li><strong>LEFT JOIN</strong> ◀️ All from left + matched from right</li>
  <li><strong>RIGHT JOIN</strong> ▶️ All from right + matched from left</li>
  <li><strong>FULL JOIN</strong> 🌐 All from both</li>
</ul>

<pre>
INNER JOIN:    A ∩ B
LEFT JOIN:     A ⟕ B
RIGHT JOIN:    A ⟖ B
FULL JOIN:     A ∪ B
</pre>

<h3>🧮 SET OPERATIONS</h3>
<ul>
  <li><strong>UNION</strong>: Combine distinct rows</li>
  <li><strong>UNION ALL</strong>: Include duplicates too</li>
  <li><strong>INTERSECT</strong>: Only common rows</li>
  <li><strong>EXCEPT / MINUS</strong>: Rows in A not in B</li>
</ul>

<pre>
UNION:       A ∪ B
UNION ALL:   A ∪ B (with duplicates)
INTERSECT:   A ∩ B
EXCEPT:      A - B
</pre>

<h3>⚠️ Requirements</h3>
<table>
  <thead><tr><th>Operation</th><th>Requirement</th></tr></thead>
  <tbody>
    <tr><td>Joins</td><td>Need common key columns</td></tr>
    <tr><td>Set Ops</td><td>Same number & type of columns</td></tr>
  </tbody>
</table>

<hr>

<h2>📘 Definition</h2>
<blockquote>SQL Join is the operation where two columns (usually keys) are matched and their records combined into a unified result.</blockquote>

<h2>🧠 When to Use SQL Joins?</h2>
<ul>
  <li>🔄 <strong>Recombine Data</strong> – Merge related data from multiple tables</li>
  <li>➕ <strong>Data Enrichment</strong> – Add extra information</li>
  <li>🔍 <strong>Existence Check</strong> – Filter based on presence in another table</li>
</ul>

<h3>🎯 Ask Yourself</h3>
<table>
  <thead><tr><th>Scenario</th><th>Use JOIN Type</th></tr></thead>
  <tbody>
    <tr><td>Matching Data</td><td>INNER JOIN</td></tr>
    <tr><td>All Data</td><td>FULL JOIN</td></tr>
    <tr><td>Unmatched Data</td><td>LEFT or RIGHT JOIN</td></tr>
  </tbody>
</table>

<pre>
Matching Data:       A ∩ B
All Data:            A ∪ B
Unmatched Data:      A ⟕ B or A ⟖ B
</pre>

<hr>

<h1>🔍 Basic Join Types with Examples</h1>

<h3>1️⃣ No Join</h3>
<blockquote>Display data from two tables separately</blockquote>
<pre><code class="sql">
SELECT * FROM table1;
SELECT * FROM table2;
</code></pre>

<h3>2️⃣ INNER JOIN</h3>
<blockquote>Returns rows where keys match in both tables</blockquote>
<pre><code class="sql">
SELECT *
FROM customers A
INNER JOIN orders B
ON A.customer_id = B.customer_id;
</code></pre>
<ul>
  <li>📌 Default join</li>
  <li>📌 Order doesn't matter</li>
  <li>📌 Use aliases to avoid ambiguity</li>
</ul>

<h3>3️⃣ LEFT JOIN</h3>
<blockquote>All rows from left + matched from right</blockquote>
<pre><code class="sql">
SELECT *
FROM customers A
LEFT JOIN orders B
ON A.customer_id = B.customer_id;
</code></pre>
<p>📌 Left table goes first</p>

<h3>4️⃣ RIGHT JOIN</h3>
<blockquote>All rows from right + matched from left</blockquote>
<pre><code class="sql">
SELECT *
FROM customers A
RIGHT JOIN orders B
ON A.customer_id = B.customer_id;
</code></pre>
<p>📌 Right table goes first</p>
<pre><code class="sql">
-- Equivalent
A LEFT JOIN B = B RIGHT JOIN A
</code></pre>

<h3>5️⃣ FULL JOIN</h3>
<blockquote>Returns all rows from both, filling unmatched with NULLs</blockquote>
<pre><code class="sql">
SELECT *
FROM customers A
FULL JOIN orders B
ON A.customer_id = B.customer_id;
</code></pre>
<p>📌 Order does not matter</p>

<h2>📎 Reference</h2>
<p>Check out the full SQL Notes: <a href="SQL Notes.md">SQL Notes</a></p>
