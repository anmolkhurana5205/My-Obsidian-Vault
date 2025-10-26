A **window function** performs a calculation across a set of table rows that are **related to the current row**, called a “window,” without collapsing the result into a single output like aggregate functions do. Instead, the result is added as a **new column** alongside each row.

### Syntax

Basic syntax:
``` mysql
<window_function>() OVER (
    [PARTITION BY partition_column]
    [ORDER BY order_column]
    [ROWS BETWEEN frame_start AND frame_end]
)
```
- **`<window_function>`** → The function you want, e.g., `SUM()`, `AVG()`, `RANK()`.
- **`PARTITION BY`** → Divides rows into groups (like `GROUP BY`, but keeps original rows).
- **`ORDER BY`** → Orders rows inside each partition.
- **`ROWS BETWEEN`** → Optional; defines exactly which rows are part of the window frame (e.g., running total).

### Types of Window Functions
#### a) Ranking Functions
These assign a rank or number to each row based on some order:
1. **`ROW_NUMBER()`**
    - Assigns a unique sequential number to rows.
    - Ties are not allowed; each row gets a different number.
```
SELECT name, salary,
       ROW_NUMBER() OVER (ORDER BY salary DESC) AS row_num
FROM employees;
```
**No ties — every row gets its own number.**
2. **`RANK()`**
    - Assigns the same rank to ties but **skips subsequent ranks**.
    - Example: salaries 120, 100, 100 → ranks 1, 2, 2, next is 4.
```
SELECT name, salary,
       RANK() OVER (ORDER BY salary DESC) AS rank_no
FROM employees;
```
ties are allowed
2. **`DENSE_RANK()`**
    - Like `RANK()`, but **no gaps** in ranks.
    - Example: salaries 120, 100, 100 → ranks 1, 2, 2, next is 3.
```
SELECT name, salary,
       DENSE_RANK() OVER (ORDER BY salary DESC) AS dense_rank_no
FROM employees;
```
no ties
2. **`NTILE(n)`**
    - Divides rows into `n` roughly equal groups (percentiles/quartiles).
```
SELECT name, salary,
       NTILE(3) OVER (ORDER BY salary DESC) AS bucket
FROM employees;
```


#### b) Aggregate Functions as Window Functions
Normal aggregate functions can also act as window functions:
- `SUM()`, `AVG()`, `COUNT()`, `MAX()`, `MIN()`
- Example:
``` mysql
SELECT name, dept_id, salary,
       SUM(salary) OVER(PARTITION BY dept_id) AS dept_total,
       AVG(salary) OVER(PARTITION BY dept_id) AS dept_avg
FROM employees;
```
Each employee sees the **department total and average**, but all rows remain.

#### c) Value Functions (`LEAD()` / `LAG()`)
These let you **look at previous or next rows**:
- `LAG(column, offset)` → value of a column in a previous row.
- `LEAD(column, offset)` → value of a column in a next row.
``` mysql
SELECT name, salary,
       LAG(salary, 1) OVER (ORDER BY salary DESC) AS prev_salary,
       LEAD(salary, 1) OVER (ORDER BY salary DESC) AS next_salary
FROM employees;
```
This is very useful for trends, differences, or comparisons.

#### d) Row-Based Window Frames
- **`ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW`** → running total up to current row.
- **`ROWS BETWEEN 1 PRECEDING AND 1 FOLLOWING`** → includes one row before and after current row.
- This gives **fine-grained control** over which rows to include in calculations.
```
SELECT day, sales,
       SUM(sales) OVER (
           ORDER BY day
           ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW
       ) AS running_total
FROM sales;
```

```
SELECT day, sales,
       AVG(sales) OVER (
           ORDER BY day
           ROWS BETWEEN 1 PRECEDING AND 1 FOLLOWING
       ) AS moving_avg
FROM sales;
```

### Key Concepts
1. **Partitioning**: `PARTITION BY` defines groups. Window function calculations restart for each partition.
2. **Ordering**: `ORDER BY` defines the row order inside the window. Important for ranking, running totals, LAG/LEAD.
3. **Frames**: `ROWS BETWEEN ...` defines exactly which rows are visible to the function. Defaults depend on the function.

