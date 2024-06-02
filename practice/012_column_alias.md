# Exercises: Column Alias

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

## Exercises

### Exercise 1: Assigning a Column Alias

**Objective**: Assign a column alias to a column.

**Task**: Use the `SELECT` statement to find the first names and assign an alias `surname` to the `last_name` column.

```sql
SELECT
    first_name,
    last_name AS surname
FROM test_customer;
```

### Exercise 2: Assigning an Alias to an Expression

**Objective**: Assign an alias to an expression.

**Task**: Use the `SELECT` statement to concatenate the first and last names and assign the alias `full_name`.

```sql
SELECT
    first_name || ' ' || last_name AS full_name
FROM test_customer;
```

### Exercise 3: Column Aliases with Spaces

**Objective**: Assign a column alias that contains spaces.

**Task**: Use the `SELECT` statement to concatenate the first and last names and assign the alias `"full name"`.

```sql
SELECT
    first_name || ' ' || last_name AS "full name"
FROM test_customer;
```

### Exercise 4: Using Aliases Without the `AS` Keyword

**Objective**: Use column aliases without the `AS` keyword.

**Task**: Use the `SELECT` statement to assign an alias to a column without using the `AS` keyword.

```sql
SELECT
    first_name,
    last_name surname
FROM test_customer;
```

## Cleaning Up

After completing the exercises, you may want to clean up by dropping the test database:

```sql
DROP DATABASE testdb;
```

## Summary

Using column aliases in PostgreSQL can make your query results more readable and meaningful.
By practicing with various examples and exercises, you can efficiently utilize column aliases to enhance your queries.
