- specifically in **MySQL**

### Syntax:
```
IF(condition, value_if_true, value_if_false)
```
- **condition** → Logical test (returns TRUE or FALSE)
- **value_if_true** → Returned if the condition is true
- **value_if_false** → Returned if the condition is false

### Basic IF
```
SELECT IF(10 > 5, 'YES', 'NO');
```
Output → `YES`

### With a Table
```
SELECT name,
       salary,
       IF(salary > 50000, 'High', 'Low') AS salary_level
FROM employees;
```

### Using `IF` in `UPDATE`
```
UPDATE employees
SET bonus = IF(salary > 70000, 10000, 5000);
```

### Nested `IF()`
```
SELECT name,
       IF(salary > 80000, 'Very High',
          IF(salary > 50000, 'Medium', 'Low')) AS level
FROM employees;
```

### Using `IF()` in WHERE
```
SELECT *
FROM employees
WHERE salary > IF(department = 'HR', 40000, 50000);
```

### Notes for `IF()` Function
- Only available in **MySQL** and **MariaDB**.  
    (In SQL Server, Oracle, PostgreSQL → use `CASE` instead.)
- Always return **a single scalar value** (not a table).
- You **cannot** use `IF()` to control query flow — it only works for returning values.

