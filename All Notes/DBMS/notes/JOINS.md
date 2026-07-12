A **JOIN** in SQL is used to **combine rows from two or more tables** based on a **related column** between them — typically a **foreign key** and a **primary key**.

### SYNTAX
``` mysql
SELECT columns
FROM table1
JOIN table2
ON table1.common_column = table2.common_column;
```

### Types of Joins in MySQL
MySQL mainly supports these joins:
1. **INNER JOIN**
2. **LEFT JOIN (LEFT OUTER JOIN)**
3. **RIGHT JOIN (RIGHT OUTER JOIN)**
4. **FULL JOIN (FULL OUTER JOIN)**
5. **CROSS JOIN**
6. **SELF JOIN**

### **1. INNER JOIN**
- Returns **only the rows that have matching values** in both tables.
- Rows without matches in either table are **excluded**.

| emp_id | name  | dept_id |
| ------ | ----- | ------- |
| 1      | Rahul | 101     |
| 2      | Priya | 102     |
| 3      | Aman  | 103     |
| 4      | Neha  | NULL    |
Table 1: `employees`

| dept_id | dept_name |
| ------- | --------- |
| 101     | HR        |
| 102     | IT        |
| 104     | Marketing |
Table 2: `departments`

#### INNER JOIN Query
``` mysql
SELECT 
  employees.name, 
  departments.dept_name
FROM employees
INNER JOIN departments
ON employees.dept_id = departments.dept_id;
```

| name  | dept_name |
| ----- | --------- |
| Rahul | HR        |
| Priya | IT        |
Result Table

### **2. LEFT JOIN (LEFT OUTER JOIN)**
- Returns **all rows from the left table**, and **matched rows from the right table**.
- If there’s no match, the right table’s columns return **NULL**.

|emp_id|name|dept_id|
|---|---|---|
|1|Rahul|101|
|2|Priya|102|
|3|Aman|103|
|4|Neha|NULL|
Table 1: `employees`

| dept_id | dept_name |
| ------- | --------- |
| 101     | HR        |
| 102     | IT        |
| 104     | Marketing |
Table 2: `departments`

#### LEFT JOIN (LEFT OUTER JOIN) Query
``` mysql
SELECT 
  employees.name, 
  departments.dept_name
FROM employees
LEFT JOIN departments
ON employees.dept_id = departments.dept_id;
```

| name  | dept_name |
| ----- | --------- |
| Rahul | HR        |
| Priya | IT        |
| Aman  | NULL      |
| Neha  | NULL      |
Result Table

### **3. RIGHT JOIN (RIGHT OUTER JOIN)**
- Returns **all rows from the right table**, and **matched rows from the left table**.
- If there’s no match, the left table’s columns return **NULL**.

|emp_id|name|dept_id|
|---|---|---|
|1|Rahul|101|
|2|Priya|102|
|3|Aman|103|
|4|Neha|NULL|
Table 1: `employees`

| dept_id | dept_name |
| ------- | --------- |
| 101     | HR        |
| 102     | IT        |
| 104     | Marketing |
Table 2: `departments`

#### RIGHT JOIN (RIGHT OUTER JOIN) Query
``` mysql
SELECT 
  employees.name, 
  departments.dept_name
FROM employees
RIGHT JOIN departments
ON employees.dept_id = departments.dept_id;
```

|name|dept_name|
|---|---|
|Rahul|HR|
|Priya|IT|
|NULL|Marketing|
Result Table

### **4. FULL JOIN (FULL OUTER JOIN)**
- ⚠️ **MySQL doesn’t directly support FULL JOIN**, but you can **simulate it** using `UNION`.
- This gives all records that appear in **either** the left or right table, filling NULLs where data is missing.
``` mysql
SELECT employees.name, departments.dept_name
FROM employees
LEFT JOIN departments
ON employees.dept_id = departments.id
UNION
SELECT employees.name, departments.dept_name
FROM employees
RIGHT JOIN departments
ON employees.dept_id = departments.id;
```


### 5. **CROSS JOIN**
- Produces a **Cartesian Product** — every row from the first table is paired with **every row from the second table**.
- Usually used **rarely**, as it can explode data size.

If 10 employees and 5 departments exist, the result = 10 × 5 = 50 rows.

| emp_id | name  |
| ------ | ----- |
| 1      | Rahul |
| 2      | Priya |
| 3      | Aman  |
Table 1: `employees`

| dept_id | dept_name |
| ------- | --------- |
| 101     | HR        |
| 102     | IT        |
Table 2: `departments`
#### CROSS JOIN Query
``` mysql
SELECT employees.name, departments.dept_name
FROM employees
CROSS JOIN departments;
```

|name|dept_name|
|---|---|
|Rahul|HR|
|Rahul|IT|
|Priya|HR|
|Priya|IT|
|Aman|HR|
|Aman|IT|
Result Table

### **6. SELF JOIN**
- A table joined **with itself**.
- Useful for comparing rows within the same table — e.g., finding employees with the same manager.

|emp_id|name|manager_id|
|---|---|---|
|1|Rahul|NULL|
|2|Priya|1|
|3|Aman|1|
|4|Neha|2|
Table: `employees`

#### SELF JOIN Query
``` mysql
SELECT 
  e1.name AS employee, 
  e2.name AS manager
FROM employees e1
LEFT JOIN employees e2
ON e1.manager_id = e2.emp_id;
```

### Step-by-Step Explanation

#### 1. `FROM employees e1`
- Here, we are taking the **`employees` table** and giving it a **nickname (alias)** — `e1`.
- Think of `e1` as **the main employee table**.
- Each row in `e1` represents one employee.

#### 2. `LEFT JOIN employees e2`
- Now, we are joining the **same table** again — `employees`.
- But we give it a **different alias** — `e2`.
- This second copy (`e2`) will act as the **manager table**.

So, `e1` = employees, `e2` = managers.

#### 3. `ON e1.manager_id = e2.emp_id`
- This line tells MySQL **how** to match rows between these two copies.
- In our table, each employee has a `manager_id` column which refers to another employee’s `emp_id`.

#### 4. `SELECT e1.name AS employee, e2.name AS manager`
- Now we **pick the columns** we want to show.
- `e1.name` = employee’s name.
- `e2.name` = that employee’s manager’s name.
- `AS employee` and `AS manager` are just **labels (aliases)** for output column names.

| employee | manager |
| -------- | ------- |
| Rahul    | NULL    |
| Priya    | Rahul   |
| Aman     | Rahul   |
| Neha     | Priya   |
Result Table

| Type            | Description                           | Includes Nulls?    |
| --------------- | ------------------------------------- | ------------------ |
| INNER SELF JOIN | Only employees who have a manager     | ❌ No               |
| LEFT SELF JOIN  | All employees, even without a manager | ✅ Yes              |
| RIGHT SELF JOIN | All managers, even without employees  | ✅ Yes              |
| CROSS SELF JOIN | Every employee–manager combination    | ✅ All combinations |
