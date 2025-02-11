# SQL

## 1. Key Concepts

### Primary Key
- A unique identifier for each record in a table.
- Ensures data integrity and prevents duplicate records.

### Foreign Key
- A field (or set of fields) in one table that refers to the primary key in another table.
- Helps maintain referential integrity.

### Indexes
- Data structures that improve query performance.
- **Clustered Index**: Defines the physical order of data in a table (one per table).
- **Non-Clustered Index**: Separate structure for fast lookups (multiple per table).

### SQL vs. NoSQL
- **SQL (Relational Databases)**: Structured, table-based, uses SQL, enforces schemas.
- **NoSQL (Non-Relational Databases)**: Flexible schema, supports document, key-value, columnar, and graph storage.

## 2. Essential SQL Commands

### Data Definition Language (DDL)
- **`CREATE TABLE`** – Creates a new table.
- **`ALTER TABLE`** – Modifies an existing table.
- **`DROP TABLE`** – Deletes a table.
- **`TRUNCATE TABLE`** – Removes all records from a table but keeps the structure.

Example:
```sql
CREATE TABLE employees (
    id INT PRIMARY KEY,
    name VARCHAR(100),
    department VARCHAR(50),
    salary DECIMAL(10,2)
);
```

### Data Manipulation Language (DML)
- **`INSERT INTO`** – Adds new records.
- **`UPDATE`** – Modifies existing records.
- **`DELETE FROM`** – Removes records.
- **`SELECT`** – Retrieves data.

Example:
```sql
INSERT INTO employees (id, name, department, salary)
VALUES (1, 'John Doe', 'HR', 55000);
```

### Filtering Data
- **`WHERE`**: Filters records based on conditions.
- **`LIKE`**: Searches for a pattern.
- **`IN`**: Matches any value in a given list.
- **`BETWEEN`**: Filters within a range.
- **`IS NULL`**: Checks for NULL values.

Example:
```sql
SELECT * FROM employees WHERE salary > 50000;
```

### Aggregation and Grouping
- **`GROUP BY`**: Groups records by one or more columns.
- **`HAVING`**: Filters results after aggregation.
- **`ORDER BY`**: Sorts query results.

Example:
```sql
SELECT department, AVG(salary)
FROM employees
GROUP BY department
HAVING AVG(salary) > 50000;
```

### Joins
- **`INNER JOIN`**: Returns only matching rows from both tables.
- **`LEFT JOIN`**: Returns all rows from the left table and matching rows from the right table.
- **`RIGHT JOIN`**: Returns all rows from the right table and matching rows from the left table.
- **`FULL JOIN`**: Returns all records when there is a match in either table.

Example:
```sql
SELECT employees.name, departments.department_name
FROM employees
INNER JOIN departments ON employees.department_id = departments.id;
```

### Subqueries
- A query inside another query.
- Used in `SELECT`, `FROM`, and `WHERE` clauses.

Example:
```sql
SELECT name FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);
```

### Transactions
- **`BEGIN TRANSACTION`**: Starts a transaction.
- **`COMMIT`**: Saves changes.
- **`ROLLBACK`**: Undoes changes.

Example:
```sql
BEGIN TRANSACTION;
UPDATE employees SET salary = salary * 1.1 WHERE department = 'IT';
COMMIT;
```

## 3. Common Interview Questions
1. **What is the difference between `WHERE` and `HAVING`?**
   - `WHERE` filters rows before grouping, `HAVING` filters after grouping.
2. **How do you optimize SQL queries?**
   - Use indexes, avoid `SELECT *`, use proper joins, limit data retrieval.
3. **What is normalization?**
   - Process of organizing data to reduce redundancy and improve consistency.
4. **How do you handle duplicates in SQL?**
   - Use `DISTINCT`, `GROUP BY`, or `ROW_NUMBER()`.
5. **What is the difference between `DELETE`, `TRUNCATE`, and `DROP`?**
   - `DELETE`: Removes rows with `WHERE`, can be rolled back.
   - `TRUNCATE`: Removes all rows, cannot be rolled back.
   - `DROP`: Removes table structure and data.

This guide covers core SQL concepts and essential commands for interviews. Let me know if you need more details!

