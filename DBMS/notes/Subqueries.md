A **subquery** (also called an **inner query** or **nested query**) is a query placed inside another SQL query. Subqueries allow you to perform intermediate calculations or filtering that you can then use in the **outer query**.
- **Inner query** → executes first and returns a result.
- **Outer query** → uses the result of the inner query.

Syntax example:
``` mysql
SELECT column1
FROM table1
WHERE column2 = (SELECT column2 FROM table2 WHERE condition);
```

#### **A. Based on the result returned**

1. **Single-row subquery**  
    Returns **one row and one column**. Often used with operators like `=`, `<`, `>`.
``` mysql
SELECT name, salary
FROM employees
WHERE salary = (SELECT MAX(salary) FROM employees);
```

2. **Multiple-row subquery** 
	Returns **one column but multiple rows**. Used with operators like `IN`, `ANY`, `ALL`.
``` mysql
SELECT name
FROM employees
WHERE dept_id IN (SELECT id FROM departments WHERE location = 'Delhi');
```

3. **Multiple-column subquery**  
	 Returns **multiple columns**. Must use tuple comparison `(col1, col2)`.
``` mysql
SELECT name
FROM employees
WHERE (dept_id, salary) = (SELECT dept_id, MAX(salary) FROM employees GROUP BY dept_id);
```

#### **B. Based on placement**

1. **Subquery in `WHERE` clause**  
    Used to filter data.
``` mysql
SELECT name
FROM employees
WHERE dept_id = (SELECT id FROM departments WHERE dept_name = 'HR');
```

2. **Subquery in `FROM` clause (Derived Tables)**  
	Treats the subquery as a temporary table.
``` mysql
SELECT dept_id, avg_salary
FROM (SELECT dept_id, AVG(salary) AS avg_salary FROM employees GROUP BY dept_id) AS dept_avg
WHERE avg_salary > 50000;
```

3. **Subquery in `SELECT` clause**  
	Calculates a value for each row.
``` mysql
SELECT name,
       (SELECT dept_name FROM departments WHERE departments.id = employees.dept_id) AS dept_name
FROM employees;
```

4. **Subquery in `HAVING` clause**  
	Useful with aggregation.
``` mysql
SELECT dept_id, COUNT(*) AS emp_count
FROM employees
GROUP BY dept_id
HAVING COUNT(*) > (SELECT AVG(emp_count) FROM (SELECT dept_id, COUNT(*) AS emp_count FROM employees GROUP BY dept_id) AS temp);
```

### **3. Correlated vs Non-Correlated Subqueries**

#### **A. Non-Correlated Subquery**
- Independent; executes **once**.
- Outer query doesn’t affect it.
``` mysql
SELECT name
FROM employees
WHERE dept_id IN (SELECT id FROM departments WHERE location = 'Delhi');
```

#### **B. Correlated Subquery**
- Dependent; executes **row by row**.
- Outer query values are used in the inner query.
``` mysql
SELECT e1.name, e1.salary
FROM employees e1
WHERE e1.salary > (SELECT AVG(e2.salary) FROM employees e2 WHERE e1.dept_id = e2.dept_id);
```

### **4. Important Operators with Subqueries**
1. **`IN`** → matches a list of values.
2. **`NOT IN`** → excludes values from a list.
3. **`ANY` / `SOME`** → compares a value to **any value** returned by a subquery.
4. **`ALL`** → compares a value to **all values** returned by a subquery.
5. **`EXISTS`** → returns TRUE if the subquery returns any row.
6. **`NOT EXISTS`** → TRUE if the subquery returns **no rows**.

