- The `WHERE` clause is used to **filter records** that meet a specified condition.

### Basic Syntax:
``` mysql
SELECT column1, column2, ...
FROM table_name
WHERE condition;
```

### Operators Used with WHERE

#### 1. **Comparison Operators**
| Operator     | Description              | Example           |
| ------------ | ------------------------ | ----------------- |
| `=`          | Equal to                 | `salary = 50000`  |
| `!=` or `<>` | Not equal to             | `salary <> 50000` |
| `>`          | Greater than             | `salary > 40000`  |
| `<`          | Less than                | `salary < 40000`  |
| `>=`         | Greater than or equal to | `salary >= 40000` |
| `<=`         | Less than or equal to    | `salary <= 40000` |

#### 2. **Logical Operators**
|Operator|Meaning|Example|
|---|---|---|
|`AND`|All conditions must be true|`salary > 50000 AND dept = 'IT'`|
|`OR`|Any condition can be true|`dept = 'IT' OR dept = 'HR'`|
|`NOT`|Negates the condition|`NOT dept = 'IT'`|
Example:
``` mysql
SELECT * FROM employees
WHERE salary > 60000 AND department = 'Finance';
```

#### 3. **BETWEEN**
- Used to check if a value lies **between** a range (inclusive).
``` mysql
SELECT * FROM employees
WHERE salary BETWEEN 40000 AND 80000;
```
Equivalent to:
``` mysql
salary >= 40000 AND salary <= 80000
```


#### 4. **IN**
- Used to match a column against **multiple values**.
``` mysql
SELECT * FROM employees
WHERE department IN ('IT', 'Finance', 'Marketing');
```
It’s a cleaner alternative to multiple OR conditions.


#### 5. **LIKE**
Used for **pattern matching** in strings.  
MySQL uses two wildcards:
- `%` → any sequence of characters
- `_` → a single character
``` mysql
WHERE name LIKE 'A%'       -- Starts with A
WHERE name LIKE '%n'       -- Ends with n
WHERE name LIKE '%an%'     -- Contains 'an'
WHERE name LIKE '_a%'      -- Second letter is 'a'
```


#### 6. **IS NULL / IS NOT NULL**
- Checks for **missing values**.
``` mysql
WHERE manager_id IS NULL;
WHERE manager_id IS NOT NULL;
```


#### 7. **EXISTS**
- Checks whether a **subquery** returns any result.
``` mysql
SELECT name FROM employees e
WHERE EXISTS (SELECT 1 FROM departments d WHERE e.dept_id = d.id);
```


### WHERE Clause with Multiple Conditions
- You can combine multiple conditions using parentheses for clarity:
``` mysql
SELECT * FROM employees
WHERE (department = 'IT' OR department = 'Finance')
  AND salary > 50000;
```
This ensures `salary > 50000` applies to both IT and Finance departments.


### WHERE with UPDATE / DELETE

#### Update:
``` mysql
UPDATE employees
SET bonus = 10000
WHERE department = 'Sales';
```

#### Delete:
``` mysql
DELETE FROM employees
WHERE last_login < '2024-01-01';
```


### WHERE vs HAVING
| Feature            | WHERE                        | HAVING                                    |
| ------------------ | ---------------------------- | ----------------------------------------- |
| Used on            | Rows                         | Groups                                    |
| Works with         | Non-aggregated columns       | Aggregated columns (`SUM`, `COUNT`, etc.) |
| Order of Execution | Before grouping (`GROUP BY`) | After grouping                            |