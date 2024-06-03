# Exercises: `LIKE`

## Setting Up a Temporary Test Database

To practice using the `LIKE` and `ILIKE` operators, we will create a temporary test database and a table called `test_customer`.

### 1. Creating a Temporary Test Database

```sql
CREATE DATABASE test_customer;
```

### 2. Connecting to the Temporary Test Database

```bash
\c test_customer
```

### 3. Creating the `test_customer` Table and Inserting Data

```sql
CREATE TABLE test_customer (
    customer_id SERIAL PRIMARY KEY,
    first_name VARCHAR(45) NOT NULL,
    last_name VARCHAR(45) NOT NULL,
    email VARCHAR(255) UNIQUE NOT NULL,
    created_on TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

INSERT INTO test_customer (first_name, last_name, email) VALUES
('Jennifer', 'Smith', 'jennifer.smith@example.com'),
('Jenifer', 'Brown', 'jenifer.brown@example.com'),
('Jenna', 'Johnson', 'jenna.johnson@example.com'),
('Jessica', 'Williams', 'jessica.williams@example.com'),
('Kimberly', 'Jones', 'kimberly.jones@example.com'),
('Theresa', 'Taylor', 'theresa.taylor@example.com');
```

## Exercises

### Exercise 1: Using the `LIKE` Operator

**Objective**: Find customers whose first names start with `Jen`.

**Task**: Use the `LIKE` operator in the `WHERE` clause.

```sql
SELECT first_name, last_name
FROM test_customer
WHERE first_name LIKE 'Jen%';
```

### Exercise 2: Using Wildcards in Patterns

**Objective**: Find customers whose first names contain `er`.

**Task**: Use the `LIKE` operator with wildcards in the `WHERE` clause.

```sql
SELECT first_name, last_name
FROM test_customer
WHERE first_name LIKE '%er%';
```

### Exercise 3: Using the `NOT LIKE` Operator

**Objective**: Find customers whose first names do not start with `Jen`.

**Task**: Use the `NOT LIKE` operator in the `WHERE` clause.

```sql
SELECT first_name, last_name
FROM test_customer
WHERE first_name NOT LIKE 'Jen';
```

### Exercise 4: Using the `ILIKE` Operator

**Objective**: Find customers whose first names start with `JEN` case-insensitively.

**Task**: Use the `ILIKE` operator in the `WHERE` clause.

```sql
SELECT first_name, last_name
FROM test_customer
WHERE first_name ILIKE 'JEN%';
```

## Cleaning Up

After completing the exercises, you may want to clean up by dropping the test database:

```sql
DROP DATABASE test_customer;
```

## Summary

- The `LIKE` operator is used for pattern matching in PostgreSQL.
- The `ILIKE` operator is a case-insensitive version of the `LIKE` operator.
- Use the percent sign (`%`) and underscore (`_`) as wildcards in patterns.
- Combine `LIKE` or `ILIKE` with `NOT` to exclude patterns from the result set.
