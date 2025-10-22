- The **`LIMIT`** and **`OFFSET`** clauses are used to control how many rows are returned by a query and from which point to start returning them. 
- These are especially useful when dealing with large tables or when you want to implement pagination (like showing 10 results per page on a website).

### **1. LIMIT Clause**

**`LIMIT`** specifies the **maximum number of rows** you want to retrieve.
``` mysql
SELECT * FROM employees
LIMIT 5;
```
This will return **only the first 5 rows** from the `employees` table.

### **2. OFFSET Clause**

**`OFFSET`** tells SQL **how many rows to skip** before starting to return rows.
``` mysql
SELECT * FROM employees
LIMIT 5 OFFSET 10;
```
This means:
- Skip the **first 10 rows**
- Then return **the next 5 rows**
So, you’ll get rows **11 to 15**.

### Shortcut Syntax (MySQL only)

In **MySQL**, you can write both in one line using a comma:
``` mysql
SELECT * FROM employees
LIMIT 10, 5;
```
This is equivalent to:
``` mysql
SELECT * FROM employees
LIMIT 5 OFFSET 10;
```

