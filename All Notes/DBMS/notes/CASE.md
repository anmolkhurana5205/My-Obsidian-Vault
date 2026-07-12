The **CASE statement** in SQL works just like **if-else** or **switch** conditions in programming languages. 
It allows you to **check conditions** and **return specific values** depending on which condition is true.

### Basic Syntax
There are **two types** of CASE statements in SQL:
#### **a. Simple CASE**
Used when you are comparing one column or expression to multiple possible values.
``` mysql
SELECT name,
       CASE department
         WHEN 'HR' THEN 'Human Resources'
         WHEN 'IT' THEN 'Information Technology'
         WHEN 'FIN' THEN 'Finance'
         ELSE 'Other Department'
       END AS department_name
FROM employees;
```

#### **b. Searched CASE**
Used when you want to test **different conditions**, not just equality.
``` mysql
SELECT name,
       CASE
         WHEN salary > 100000 THEN 'High'
         WHEN salary BETWEEN 50000 AND 100000 THEN 'Medium'
         ELSE 'Low'
       END AS salary_level
FROM employees;
```

