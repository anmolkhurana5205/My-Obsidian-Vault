- The **`UPDATE`** command in SQL is used to **modify existing records** in a table.  
- It does **not add** a new row — it only **changes data** already present.

### Basic Syntax
``` mysql
UPDATE table_name
SET column1 = value1, column2 = value2, ...
WHERE condition;
```
- `UPDATE table_name` → The table you want to change
- `SET` → The columns you want to update
- `WHERE` → Specifies which rows should be updated

⚠️ If you **omit the WHERE clause**, all rows in the table will be updated — which can be dangerous!

### Example – Updating One Column

Suppose you have a table `employees`:
``` mysql
UPDATE employees
SET salary = 50000
WHERE name = 'Riya';
```

### Updating Multiple Columns

You can update multiple columns in one go:
``` mysql
UPDATE employees
SET salary = 60000, name = 'Riya Sharma'
WHERE id = 1;
```

### Update Without [[WHERE]] Clause ⚠️

If you **omit the WHERE clause**, all rows in the table will be updated.
``` mysql
UPDATE employees
SET salary = 10000;
```
- This will change the salary of **every employee** to 10000.  
- That’s why using a `WHERE` clause is crucial unless you really mean to update all rows.

### Using Expressions in UPDATE

You can use arithmetic or functions inside `SET`:
``` mysql
UPDATE employees
SET salary = salary + 5000
WHERE id = 2;
```

### UPDATE Using a [[Subqueries]]

You can use a **subquery** to set values based on another table.
``` mysql
UPDATE employees e
SET salary = (
  SELECT AVG(salary)
  FROM employees
  WHERE department_id = e.department_id
)
WHERE e.department_id = 2;
```

### UPDATE with [[JOINS]] (Updating from Another Table)

Let’s say you have two tables:
``` mysql
UPDATE employees e
JOIN departments d
ON e.dept_id = d.dept_id
SET e.salary = e.salary + d.bonus;
```

### UPDATE with [[CASE]] Statement (Conditional Update)

You can apply different updates based on conditions:
``` mysql
UPDATE employees
SET salary = CASE
               WHEN salary < 50000 THEN salary + 10000
               WHEN salary BETWEEN 50000 AND 70000 THEN salary + 5000
               ELSE salary + 2000
             END;
```

## UPDATE Using [[IF()]] Function (MySQL Specific)

MySQL allows `IF()` function for simple conditions:
``` mysql
UPDATE employees
SET salary = IF(salary < 50000, salary + 10000, salary + 2000);
```

### Common Mistakes & Warnings ⚠️
| Mistake                        | Description                                            |
| ------------------------------ | ------------------------------------------------------ |
| Missing `WHERE`                | Updates all rows unintentionally                       |
| Wrong table alias              | `UPDATE e SET ... FROM employees e` → invalid in MySQL |
| Subquery returns multiple rows | Causes an error unless handled properly                |
| Using string without quotes    | Always use `'value'` for strings                       |

