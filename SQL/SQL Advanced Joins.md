<h2>🔹 1. Left Anti Join</h2>
<blockquote>
📘 <strong>Definition:</strong> Returns all rows from the <strong>left table</strong> that have <u>no matching rows</u> in the right table.
</blockquote>

<ul>
  <li>✅ Only unmatched rows from <code>A</code> are returned</li>
  <li>❌ <code>B</code> is only used for filtering</li>
</ul>

<pre><code class="sql">
SELECT *
FROM table1 A
LEFT JOIN table2 B
ON A.Key = B.Key
WHERE B.Key IS NULL;
</code></pre>

<p>📝 <strong>Note:</strong> Table order matters. Left table is the focus.</p>

<hr>

<h2>🔹 2. Right Anti Join</h2>
<blockquote>
📘 <strong>Definition:</strong> Returns all rows from the <strong>right table</strong> that have <u>no matching rows</u> in the left table.
</blockquote>

<ul>
  <li>✅ Only unmatched rows from <code>B</code> are returned</li>
  <li>❌ <code>A</code> is only used for filtering</li>
</ul>

<pre><code class="sql">
SELECT *
FROM table1 A
RIGHT JOIN table2 B
ON A.Key = B.Key
WHERE A.Key IS NULL;
</code></pre>

<p>📝 <strong>Note:</strong> Table order matters. Right table is the focus.</p>

<hr>

<h2>🔹 3. Full Anti Join</h2>
<blockquote>
📘 <strong>Definition:</strong> Returns all rows from both tables that do <u>not match</u> each other.
</blockquote>

<pre><code class="sql">
SELECT *
FROM table1 A
FULL JOIN table2 B
ON A.Key = B.Key
WHERE A.Key IS NULL OR B.Key IS NULL;
</code></pre>

<p>📝 <strong>Note:</strong> Order doesn’t matter here — both tables are equally considered.</p>

<hr>

<h2>🔹 4. Cross Join</h2>
<blockquote>
📘 <strong>Definition:</strong> Returns the <strong>Cartesian product</strong> — all combinations of rows between two tables.
</blockquote>

<pre><code class="sql">
SELECT *
FROM table1
CROSS JOIN table2;
</code></pre>

<ul>
  <li>🧮 Every row from table1 is combined with every row from table2</li>
  <li>📝 No <code>ON</code> or <code>WHERE</code> needed since there's no matching condition</li>
</ul>

<hr>

<h2>🧠 Join Decision Tree</h2>

<pre>
<pre>
<pre>
           🔽 Do you need only matching rows?
               ┌────────────────────────────┐
               │           YES              │
               └────────────┬───────────────┘
                            ▼
                      ┌────────────┐
                      │ INNER JOIN │
                      └────────────┘

           🔽 Do you need all rows?
              ┌────────────────────────────┐
              │           YES              │
              └────────────┬───────────────┘
                           ▼

                  🔽 Are both tables equally important?
                    ┌───────────────────────────────┐
                    │             YES               │
                    └─────────────┬─────────────────┘
                                  ▼
                            ┌────────────┐
                            │ FULL JOIN  │
                            └────────────┘

                  🔽 Is one table the master table?
                    ┌───────────────────────────────┐
                    │             YES               │
                    └─────────────┬─────────────────┘
                                  ▼

                        🔽 Which table is the master?
                            ┌─────────────────────────────┐
                            │      Which table is it?     │
                            └────────────┬────────────────┘
                                         ▼
                                ┌────────────────────────────────────────┐
                                ▼                                        ▼
                            ┌────────────────────┐            ┌─────────────────────┐
                            │   Left table (A)   │            │   Right table (B)   │
                            └──────────┬─────────┘            └──────────┬──────────┘
                                       ▼                                 ▼
                                ┌────────────┐                     ┌─────────────┐
                                │  LEFT JOIN │                     │  RIGHT JOIN │
                                └────────────┘                     └─────────────┘

           🔽 Only want unmatched data from one side?
               ┌────────────────────────────────────────┐
               │                 YES                    │                  └──────────────────┬─────────────────────┘
                                  ▼
                ┌────────────────────────────────────────────────────┐
                │ LEFT ANTI JOIN / RIGHT ANTI JOIN (filtered NULLs)  │
                └────────────────────────────────────────────────────┘
</pre>

</pre>

</pre>

<p>✅ Use this decision tree to guide your JOIN type selection with confidence!</p>


<h2>🔗 Multi-Table Joins using LEFT JOIN</h2>

<blockquote>
📘 <strong>Definition:</strong> A <code>LEFT JOIN</code> can be chained to combine multiple tables, starting with one and progressively joining others on matching keys.
</blockquote>

<p>✅ This is useful when combining data from 3 or more related tables — even if some intermediate tables don’t have matching data.</p>

---

<h3>🛠️ Syntax:</h3>

<pre><code class="sql">
SELECT A.col1, B.col2, C.col3
FROM table_A A
LEFT JOIN table_B B ON A.key = B.key
LEFT JOIN table_C C ON B.key = C.key;
</code></pre>

---

<h3>📌 Example:</h3>

<pre><code class="sql">
SELECT customers.name, orders.order_id, payments.amount
FROM customers
LEFT JOIN orders ON customers.customer_id = orders.customer_id
LEFT JOIN payments ON orders.order_id = payments.order_id;
</code></pre>

<ul>
  <li>🔹 This retrieves <strong>all customers</strong> even if they haven’t placed orders.</li>
  <li>🔹 And it includes <strong>all orders</strong> even if no payment has been made yet.</li>
  <li>🟨 <code>NULL</code> will appear in columns where no match exists.</li>
</ul>

---

<h3>⚠️ Rules & Notes:</h3>
<ul>
  <li>Always start with the <strong>base (left-most) table</strong> you want all results from.</li>
  <li>Each subsequent <code>LEFT JOIN</code> filters based on the previous join’s result.</li>
  <li>Alias tables to keep SQL readable and avoid column name conflicts.</li>
</ul>

<p>🔁 You can continue chaining more <code>LEFT JOIN</code>s as needed, following the same pattern.</p>
