# Exercises: `SELECT`

## Setting Up a Temporary Test Database

### 1. Creating a Temporary Test Database

```sql
CREATE DATABASE testdb;
```

### 2. Connecting to the Temporary Test Database

```bash
\c testdb
```

### 3. Creating Temporary Test Tables

```sql
CREATE TABLE test_customer (
    customer_id SERIAL PRIMARY KEY,
    first_name VARCHAR(45) NOT NULL,
    last_name VARCHAR(45) NOT NULL,
    email VARCHAR(255) UNIQUE NOT NULL,
    created_on TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

INSERT INTO test_customer (first_name, last_name, email)
VALUES
    ('John', 'Doe', 'john.doe@example.com'),
    ('Jane', 'Smith', 'jane.smith@example.com'),
    ('Alice', 'Johnson', 'alice.johnson@example.com');
```

### Exercise 1: Query Data from One Column

**Objective**: Query the first names of all customers from the `test_customer` table.

**Task**: Use the `SELECT` statement to find the first names.

```sql
SELECT first_name FROM test_customer;
```

### Exercise 2: Query Data from Multiple Columns

**Objective**: Query the first name, last name, and email of customers from the `test_customer` table.

**Task**: Use the `SELECT` statement to find the specified columns.

```sql
SELECT first_name, last_name, email FROM test_customers;
```

### Exercise 3: Query Data from All Columns

**Objective**: Query data from all columns of the `test_customer` table.

**Task**: Use the `SELECT` statement to find all columns.

```sql
SELECT * FROM test_customer;
```

### Exercise $: Using Expressions in `SELECT`

**Objective**: Return the full names and emails of all customers using concatenation.

**Task**: Use the `SELECT` statement with the concatenation operator.

```sql
SELECT first_name || ' ' || last_name AS full_name FROM test_customer;
```

### Exercise 5: `SELECT` with Expressions and No `FROM` Clause

**Objective**: Use the `SELECT` statement with an arithmetic expression.

**Task**: Use the `SELECT` statement without a `FROM` clause.

```sql
SELECT 5 * 3;
```

## Cleaning Up

After completing the exercises, you may want to clean up by dropping the test database:

```sql
DROP DATABASE testdb;
```

## Summary

The `SELECT` statement is fundamental to querying data in PostgreSQL.
By practicing with various clauses and expressions, you can efficiently retrieve and manipulate data from your database.
