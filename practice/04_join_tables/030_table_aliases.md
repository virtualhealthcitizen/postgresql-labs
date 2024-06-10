# Exercises: Table aliases

## Setting Up a Temporary Test Database

### 1. Creating a Temporary Test Database

```sql
CREATE DATABASE testdb;
```

### 2. Connecting to the Temporary Test Database

```bash
\c testdb
```

## Creating the `employees` and `payments` Tables and Inserting Data

### 3. Creating the Tables

```sql
CREATE TABLE employees (
    employee_id SERIAL PRIMARY KEY,
    first_name VARCHAR(50) NOT NULL,
    last_name VARCHAR(50) NOT NULL,
    manager_id INT
);

CREATE TABLE payments (
    payment_id SERIAL PRIMARY KEY,
    customer_id INT NOT NULL,
    amount NUMERIC(5,2) NOT NULL,
    payment_date DATE NOT NULL,
    FOREIGN KEY (customer_id) REFERENCES employees(employee_id)
);
```

### 4. Inserting Data

```sql
INSERT INTO employees (first_name, last_name, manager_id) VALUES
('John', 'Doe', NULL),
('Jane', 'Smith', 1),
('Bill', 'Jones', 1),
('Mary', 'Johnson', 2);

INSERT INTO payments (customer_id, amount, payment_date) VALUES
(1, 50.00, '2023-01-01'),
(2, 75.00, '2023-01-02'),
(3, 100.00, '2023-01-03'),
(4, 150.00, '2023-01-04');
```

## Exercises

### Exercise 1: Using Table Aliases for Readability

**Objective**: Use a table alias to simplify the query and make it more readable.

**Task**: Query the `employees` table using an alias.

```sql
SELECT e.first_name, e.last_name FROM employees e;
```

### Exercise 2: Using Table Aliases in Join Clauses

**Objective**: Use table aliases to join `employees` and `payments` tables.

**Task**: Perform an inner join between `employees` and `payments` tables using aliases.

```sql
SELECT e.first_name, e.last_name, p.amount, p.payment_date
FROM employees e
INNER JOIN payments p ON e.employee_id = p.customer_id;
```

### Exercise 3: Using Table Aliases in Self-Join

**Objective**: Use table aliases to perform a self-join on the `employees` table.

**Task**: Perform a self-join on the `employees` table to find each employee and their manager.

```sql
SELECT e.first_name AS employee, m.first_name AS manager
FROM employees e
INNER JOIN employees m ON e.manager_id = m.employee_id;
```

### Exercise 4: Using Table Aliases with Complex Queries

**Objective**: Combine multiple aliases in a single query.

**Task**: Use aliases to join `employees` and `payments` and filter the results.

```sql
SELECT e.first_name, e.last_name, p.amount, p.payment_date
FROM employees e
INNER JOIN payments p ON e.employee_id = p.customer_id
WHERE p.amount > 50.00;
```

## Cleaning Up

After completing the exercises, you may want to clean up by dropping the test database:

```sql
DROP DATABASE testdb;
```

## Summary

- Table aliases temporarily assign tables new names during execution of a query.
- Table aliases improve readability and simplify queries, especially when dealing with long table names.
- Table aliases are essential in join clauses and self-joins to avoid errors and make queries more concise.
