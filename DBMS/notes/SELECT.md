## 1. Selecting Data

### a. All Columns
``` mysql
SELECT * FROM employees;
```

### b. Specific Columns
``` mysql
SELECT id, name, salary FROM employees;
```

### c. Column Aliases (Renaming Output)
``` mysql
SELECT name AS employee_name, salary AS income FROM employees;
```
You can also skip `AS`:
``` mysql
SELECT name employee_name, salary income FROM employees;
```

## 2. Expressions and Calculations

You can perform calculations directly inside `SELECT`.
``` mysql
SELECT name, salary * 12 AS yearly_salary
FROM employees;
```

You can even combine text:
``` mysql
SELECT CONCAT(first_name, ' ', last_name) AS full_name
FROM employees;
```

Or add conditions using [[CASE]]:
``` mysql
SELECT name,
       CASE
         WHEN salary > 100000 THEN 'High'
         WHEN salary BETWEEN 50000 AND 100000 THEN 'Medium'
         ELSE 'Low'
       END AS salary_level
FROM employees;
```

## 3. DISTINCT — Remove Duplicate Values

`DISTINCT` eliminates duplicates from the output.
``` mysql
SELECT DISTINCT department FROM employees;
```

If you select multiple columns:
``` mysql
SELECT DISTINCT department, job_title FROM employees;
```
→ Returns unique combinations of both.

## 4. [[WHERE]] — Filtering Rows

Used to filter which rows appear in the result.
``` mysql
SELECT * FROM employees WHERE salary > 50000;
```

#### Common Operators
|Operator|Meaning|Example|
|---|---|---|
|`=`|Equal|`WHERE dept_id = 3`|
|`!=` or `<>`|Not equal|`WHERE dept_id != 3`|
|`>` `<` `>=` `<=`|Comparison|`WHERE age >= 25`|
|`BETWEEN`|Range|`WHERE age BETWEEN 25 AND 35`|
|`IN`|List of values|`WHERE dept_id IN (1, 2, 3)`|
|`LIKE`|Pattern match|`WHERE name LIKE 'A%'`|
|`IS NULL`|Checks null|`WHERE manager_id IS NULL`|
Example:
``` mysql
SELECT * FROM employees WHERE name LIKE '%son'; // ends with son
SELECT * FROM employees WHERE age BETWEEN 30 AND 40;
```

## 5. ORDER BY — Sorting Results

Used to sort the output.
``` mysql
SELECT * FROM employees ORDER BY salary DESC;
```
#### Notes:
- Default: `ASC` (ascending order)
- You can sort by **multiple columns**:
``` mysql
SELECT * FROM employees ORDER BY dept_id ASC, salary DESC;
```
- `ORDER BY dept_id ASC` → sorts the rows by `dept_id` in **ascending order** (lowest to highest).
- `, salary DESC` → within each department (`dept_id`), it further sorts employees by `salary` in **descending order** (highest to lowest).

## 6. Aggregate Functions with SELECT

Used for calculations on groups of rows.

| Function  | Description   |
| --------- | ------------- |
| `COUNT()` | Count of rows |
| `SUM()`   | Sum of values |
| `AVG()`   | Average value |
| `MIN()`   | Minimum       |
| `MAX()`   | Maximum       |
``` mysql
SELECT COUNT(*) FROM employees;
SELECT AVG(salary) FROM employees;
```

## 7. [[GROUP BY]] — Grouping Results

Groups rows that have the same values in specified columns.
``` mysql
SELECT dept_id, AVG(salary)
FROM employees
GROUP BY dept_id;
```

## 8. [[HAVING]] — Filtering Groups

`HAVING` filters **after grouping**, while `WHERE` filters **before** grouping.
``` mysql
SELECT dept_id, AVG(salary)
FROM employees
GROUP BY dept_id
HAVING AVG(salary) > 60000;
```

## 9. [[LIMIT and OFFSET]] — Restrict Output

Used to get a fixed number of rows (common in LeetCode).
``` mysql
SELECT * FROM employees LIMIT 5;           -- First 5 rows
SELECT * FROM employees LIMIT 5 OFFSET 10; -- Skip first 10 rows
```

## 10. SELECT with [[JOINS]] (Combining Tables)

The `SELECT` command can query multiple tables using **JOIN**.

#### INNER JOIN
``` mysql
SELECT e.name, d.department_name
FROM employees e
JOIN departments d ON e.dept_id = d.id;
```
#### LEFT JOIN
``` mysql
SELECT e.name, d.department_name
FROM employees e
LEFT JOIN departments d ON e.dept_id = d.id;
```

#### SELF JOIN
``` mysql
SELECT a.name AS employee, b.name AS manager
FROM employees a
JOIN employees b ON a.manager_id = b.id;
```

## 11. SELECT with [[Subqueries]]

A `SELECT` can contain another `SELECT` inside it.
#### In WHERE Clause
``` mysql
SELECT name
FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);
```

#### As Derived Table (FROM Clause)
``` mysql
SELECT dept_id, COUNT(*) AS emp_count
FROM (
  SELECT * FROM employees WHERE salary > 50000
) AS high_earners
GROUP BY dept_id;
```

## 12. SELECT with [[Window Functions]] (Advanced but Vital for LeetCode)

Window functions allow you to calculate things **across rows without grouping them**.
``` mysql
SELECT name, salary,
       RANK() OVER (ORDER BY salary DESC) AS rank_in_company,
       SUM(salary) OVER (PARTITION BY dept_id) AS dept_total
FROM employees;
```

Functions include:
- `ROW_NUMBER()`
- `RANK()`
- `DENSE_RANK()`
- `SUM()`, `AVG()`, `COUNT()` with `OVER(...)`

## 13. SELECT with [[CASE]] (Conditional Logic)
Use `CASE` to add conditional columns.
``` mysql
SELECT name, salary,
       CASE
         WHEN salary > 100000 THEN 'High'
         WHEN salary BETWEEN 50000 AND 100000 THEN 'Medium'
         ELSE 'Low'
       END AS salary_level
FROM employees;
```

## 14. SELECT with UNION
Combine results from multiple SELECTs.
``` mysql
SELECT name FROM employees
UNION
SELECT name FROM interns;
```
- `UNION` → removes duplicates
- `UNION ALL` → keeps duplicates

## 15. SELECT with [[CTE]] (Common Table Expression)

Improves readability for complex queries.
``` mysql
WITH avg_sal AS (
  SELECT dept_id, AVG(salary) AS avg_salary
  FROM employees
  GROUP BY dept_id
)
SELECT e.name, e.dept_id
FROM employees e
JOIN avg_sal a ON e.dept_id = a.dept_id
WHERE e.salary > a.avg_salary;
```

### Step 1: The CTE (Common Table Expression)
``` mysql
WITH avg_sal AS (
  SELECT dept_id, AVG(salary) AS avg_salary
  FROM employees
  GROUP BY dept_id
)
```
Here:
- `avg_sal` is the name of the CTE (you can think of it like a **temporary table**).
- Inside it, we calculate the **average salary per department**.
- `GROUP BY dept_id` ensures each department’s average salary is calculated separately.
- The result of this part might look like this:

| dept_id | avg_salary |
| ------- | ---------- |
| 1       | 50000      |
| 2       | 62000      |
| 3       | 48000      |
### Step 2: The Main Query
``` mysql
SELECT e.name, e.dept_id
FROM employees e
JOIN avg_sal a ON e.dept_id = a.dept_id
WHERE e.salary > a.avg_salary;
```
Here’s what happens:
- We **join** the `employees` table (`e`) with the CTE `avg_sal` (`a`) **on the department ID**.
- This means each employee is paired with the **average salary** of their own department.
- Then we use the `WHERE` clause to **filter** only those employees whose `salary` is **greater than** their department’s average (`a.avg_salary`).
## 16. Execution Order (VERY IMPORTANT)

When SQL executes, the actual order is **different** from how you write it.

| Logical Order | Clause   |
| ------------- | -------- |
| 1             | FROM     |
| 2             | JOIN     |
| 3             | WHERE    |
| 4             | GROUP BY |
| 5             | HAVING   |
| 6             | SELECT   |
| 7             | ORDER BY |
| 8             | LIMIT    |
| 9             | OFFSET   |
