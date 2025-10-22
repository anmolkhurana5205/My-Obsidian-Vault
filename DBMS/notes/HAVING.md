Note - It can only be used on aggregated data.

- `HAVING` is used to filter the results of a **GROUP BY** query based on an aggregate function.
- Think of it as a **WHERE** clause, but for **aggregated data**.
- You **cannot use HAVING** without aggregation (technically you can, but it usually doesn’t make sense).

**Key idea:**
- `WHERE` filters **rows before grouping**.
- `HAVING` filters **groups after aggregation**.

### Basic Syntax
``` mysql
SELECT column1, aggregate_function(column2)
FROM table_name
WHERE condition
GROUP BY column1
HAVING aggregate_function(column2) condition;
```

### **Simple Example**

|customer_id|order_amount|
|---|---|
|1|100|
|2|200|
|1|150|
|3|50|
|2|300|
**Table:** `orders`

Query: Customers with total order amount > 250:
``` mysql
SELECT customer_id, SUM(order_amount) AS total_amount
FROM orders
GROUP BY customer_id
HAVING SUM(order_amount) > 250;
```

| customer_id | total_amount |
| ----------- | ------------ |
| 1           | 250          |
| 2           | 500          |
Result Table

### **Difference Between WHERE and HAVING**
``` mysql
SELECT customer_id, SUM(order_amount)
FROM orders
WHERE order_amount > 100
GROUP BY customer_id
HAVING SUM(order_amount) > 300;
```
- `WHERE order_amount > 100` → filters **rows before grouping**.
- `HAVING SUM(order_amount) > 300` → filters **groups after aggregation**.

### **HAVING With Multiple Conditions**
You can use `AND`, `OR`, etc., just like in `WHERE`.
``` mysql
SELECT customer_id, COUNT(*) AS order_count, SUM(order_amount) AS total_amount
FROM orders
GROUP BY customer_id
HAVING COUNT(*) > 1 AND SUM(order_amount) > 200;
```
This filters customers who:
- Made **more than 1 order**
- Total orders sum **more than 200**

### **HAVING Without GROUP BY**
Technically possible but rare. Example:
``` mysql
SELECT SUM(order_amount) AS total
FROM orders
HAVING SUM(order_amount) > 500;
```
Here, the entire table is treated as a single group.

### **Using Aliases in HAVING**
Some databases allow using column aliases in HAVING:
``` mysql
SELECT customer_id, SUM(order_amount) AS total_amount
FROM orders
GROUP BY customer_id
HAVING total_amount > 250;
```
**Tip:** MySQL allows this, but SQL Server may require the full expression.

### **Common Mistakes**
#### 1. Using `HAVING` without an aggregate function:
``` mysql
HAVING customer_id = 1;  -- ❌ usually wrong
```
Should use `WHERE customer_id = 1` instead.

#### 2. Forgetting `GROUP BY`:
``` mysql
SELECT customer_id, SUM(order_amount)
FROM orders
HAVING SUM(order_amount) > 200;  -- ❌ unclear groups
```