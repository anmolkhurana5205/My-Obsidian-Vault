- The `GROUP BY` statement is used to **group rows that have the same values in one or more columns**.
- It is mostly used with **aggregate functions** like `COUNT()`, `SUM()`, `AVG()`, `MIN()`, `MAX()` to get summarized results.

### Syntax
``` mysql
SELECT column1, aggregate_function(column2)
FROM table_name
WHERE condition
GROUP BY column1;
```
- `column1` → Column you want to group by
- `aggregate_function(column2)` → Function that summarizes data for each group
![[Pasted image 20251022134631.png]]
### Common Aggregate Functions with GROUP BY
| Function  | Description                            |
| --------- | -------------------------------------- |
| `COUNT()` | Counts number of rows in each group    |
| `SUM()`   | Adds values in a column for each group |
| `AVG()`   | Calculates average value in each group |
| `MIN()`   | Finds the minimum value in each group  |
| `MAX()`   | Finds the maximum value in each group  |
### **Multiple Columns in GROUP BY**
You can group by **more than one column**:
``` mysql
SELECT department, job_title, COUNT(*) AS total_employees
FROM employees
GROUP BY department, job_title;
```
- Each combination of department + job title is treated as a separate group.

### **Using GROUP BY with [[HAVING]]**
- `HAVING` is like a `WHERE` clause but for **groups**.
- `WHERE` filters rows **before grouping**, `HAVING` filters groups **after grouping**.
``` mysql
SELECT department, COUNT(*) AS total_employees
FROM employees
GROUP BY department
HAVING COUNT(*) > 5;
```
- Only departments with **more than 5 employees** are included.

### **What’s happening internally?**
Step-by-step:
- SQL scans all rows in the table.
- It groups rows based on the `GROUP BY` column(s).
- For each group, it applies **aggregate functions**.
- Returns **one row per group**.

### **Important Rules**
1. All **non-aggregated columns in SELECT** must appear in the `GROUP BY` clause.
``` mysql
SELECT name, COUNT(*) FROM employees GROUP BY department; -- ❌ Error
```
- Correct would be:
``` mysql
SELECT department, COUNT(*) FROM employees GROUP BY department; -- ✅
```

2. Aggregate functions can be used **with or without GROUP BY**:
- Without GROUP BY → Computes aggregate for **entire table**.
- With GROUP BY → Computes aggregate **per group**.

### **Quick Summary**
- `GROUP BY` = summarize data by groups.
- Used with aggregate functions (`COUNT`, `SUM`, `AVG`, `MIN`, `MAX`).
- Can use **multiple columns**.
- Use `HAVING` to filter groups after aggregation.
- All non-aggregated columns in `SELECT` **must** be in `GROUP BY`.

