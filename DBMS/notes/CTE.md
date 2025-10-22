- A **CTE** is a temporary named result set in SQL that you can reference within a `SELECT`, `INSERT`, `UPDATE`, or `DELETE` statement. Think of it as a **temporary table** or **view** that exists only during the execution of that query.
- It makes queries **more readable**, **organized**, and **easier to debug**.

### **Syntax of a CTE**
``` mysql
WITH cte_name (column1, column2, ...)
AS (
    -- SQL query here
    SELECT column1, column2
    FROM table_name
    WHERE condition
)
-- Use the CTE in a query
SELECT *
FROM cte_name
WHERE some_condition;
```
- `WITH` keyword starts a CTE.
- `cte_name` is the name you give to the CTE.
- Optional `(column1, column2, ...)` allows you to rename columns.
- The SQL query inside the parentheses defines the data.
- After the CTE, you can reference it like a **regular table**.

### **Types of CTEs**

#### **a) Simple (Non-Recursive) CTE**
Used to organize queries or break complex queries into smaller pieces.
**Example:**
``` mysql
WITH dept_avg AS (
    SELECT dept_id, AVG(salary) AS avg_salary
    FROM employees
    GROUP BY dept_id
)
SELECT e.name, e.salary, d.avg_salary
FROM employees e
JOIN dept_avg d ON e.dept_id = d.dept_id
WHERE e.salary > d.avg_salary;
```

#### **b) Recursive CTE**
Used when you need to perform **hierarchical or iterative calculations**, like organization charts or tree structures.
**Syntax:**
``` mysql
WITH RECURSIVE cte_name (columns)
AS (
    -- Anchor member
    SELECT ...
    FROM ...
    WHERE ...

    UNION ALL

    -- Recursive member
    SELECT ...
    FROM table_name t
    JOIN cte_name c ON t.parent_id = c.id
)
SELECT *
FROM cte_name;
```

### **Key Features of CTE**
1. **Readable Queries** – Break down complex queries into smaller, reusable parts.
2. **Temporary Scope** – Exists only for the duration of the query.
3. **Recursive Capabilities** – Can be used for hierarchical data traversal.
4. **Can be Referenced Multiple Times** – Inside the same query, you can refer to the CTE multiple times.
5. **Supports INSERT, UPDATE, DELETE** – Not just SELECT.

### CTE vs Subquery
|Feature|CTE|Subquery|
|---|---|---|
|Readability|Easier, can name intermediate results|Harder for multiple layers|
|Reusability|Can reference multiple times|Cannot reuse easily|
|Recursion|Supports recursive queries|Cannot do recursion|
|Scope|Exists only for query execution|Exists only inside the query it is defined|
### Multiple CTEs
You can define **more than one CTE** in a query using commas:
``` mysql
WITH cte1 AS (
    SELECT ...
),
cte2 AS (
    SELECT ...
)
SELECT *
FROM cte1
JOIN cte2 ON cte1.id = cte2.id;
```

### **When to Use CTE**
- When queries are **complex** and need better readability.
- When working with **recursive data** (organization hierarchy, tree structures).
- When you want to **avoid repeating the same subquery** multiple times.
- When you need a **temporary result set** without creating a physical table.

