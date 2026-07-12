**MySQL** is an **open-source Relational Database Management System (RDBMS)** that uses **SQL (Structured Query Language)** to manage and manipulate data.

-  **Cross-platform** (works on Windows, Linux, macOS)
- **Compatible** with many programming languages (like PHP, Java, Python, Node.js, etc.)
- **Secure** (supports user authentication and privileges)

### Key Features of MySQL

1. **Relational** – Data is stored in **tables** (rows and columns) with relationships between them.
2. **Structured Query Language (SQL)** – Used to perform operations like `SELECT`, `INSERT`, `UPDATE`, and `DELETE`.
3. **Scalable** – Can handle small and large databases efficiently.
4. **Data Security** – Provides secure connections and encryption options.
5. **ACID Compliance** – Ensures reliable transactions (Atomicity, Consistency, Isolation, Durability).
6. **Replication & Clustering** – Allows data redundancy and high availability.
7. **Indexes** – Improve query performance.
8. **Stored Procedures, Views, and Triggers** – Help in advanced database management.

### MySQL Architecture Overview
MySQL architecture consists of:
1. **Client Layer** – Handles client connections and requests.
2. **SQL Layer** – Parses and executes SQL queries.
3. **Storage Engine Layer** – Manages how data is stored on disk (InnoDB, MyISAM, etc.).

### Basic Structure
``` mysql
SELECT columns
FROM table_name
WHERE condition
GROUP BY columns
HAVING condition
ORDER BY columns
LIMIT n;
```

### Execution Order (VERY IMPORTANT)

When SQL executes, the actual order is **different** from how you write it.

| Logical Order | Clause   |
| ------------- | -------- |
| 1             | FROM     |
| 2             | JOIN     |
| 3             | WHERE    |
| 4             | GROUP BY |
| 5             | HAVING   |
| 6             | SELECT   |
| 7             | ORDER BY |
| 8             | LIMIT    |
| 9             | OFFSET   |
### Aliases
- After aliasing, you **must use the aliases**
