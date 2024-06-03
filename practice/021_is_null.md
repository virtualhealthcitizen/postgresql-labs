# Exercises: `IS NULL`

## Setting Up a Temporary Test Database

To practice using the `IS NULL` and `IS NOT NULL` operators, we will create a temporary test database and a table called `test_contacts`.

### 1. Creating a Temporary Test Database

```sql
CREATE DATABASE test_contacts;
```

### 2. Connecting to the Temporary Test Database

```bash
\c test_contacts
```

### 3. Creating the `test_contacts` Table and Inserting Data

```sql
CREATE TABLE test_contacts (
    id SERIAL PRIMARY KEY,
    first_name VARCHAr(50) NOT NULL,
    last_name VARCHAR(50) NOT NULL,
    email VARCHAR(255) NOT NULL,
    phone VARCHAR(15)
);

INSERT INTO test_contacts (first_name, last_name, email, phone)
VALUES
('John', 'Doe', 'john.doe@example.com', NULL),
('Lily', 'Bush', 'lily.bush@example.com', '(408-234-2764)'),
('Peter', 'Parker', 'peter.parker@example.com', NULL),
('Tony', 'Stark', 'tony.stark@example.com', '(123-456-7890)');
```

### Exercise 1: Using the `IS NULL` Operator

**Objective**: Find contacts who do not have a phone number.

**Task**: Use the `IS NULL` operator in the `WHERE` clause.

```sql
SELECT id, first_name, last_name, email, phone
FROM test_contacts
WHERE phone IS NULL;
```

### Exercise 2: Using the `IS NOT NULL` Operator

**Objective**: Find contacts who have a phone number.

**Task**: Use the `IS NOT NULL` operator in the `WHERE` clause.

```sql
SELECT id, first_name, last_name, email, phone
FROM test_contacts
WHERE phone IS NOT NULL;
```

### Exercise 3: Combining `IS NULL` with Other Conditions

**Objective**: Find contacts with a specific email domain who do not have a phone number.

**Task**: Use the `IS NULL` operator with additional conditions in the `WHERE` clause.

```sql
SELECT id, first_name, last_name, email, phone FROM test_contacts WHERE phone IS NULL AND email LIKE '%example.com';
```

### Exercise 4: Checking for `NULL` Values in Other Columns

**Objective**: Find contacts whose email is `NULL`.

**Task**: Use the `IS NULL` operator in the `WHERE` clause to check for `NULL` in the email column.

```sql
SELECT id, first_name, last_name, email, phone
FROM test_contacts
WHERE email IS NULL;
```

## Cleaning Up

After completing the exercises, you may want to clean up by dropping the test database:

```sql
DROP DATABASE test_contacts;
```

## Summary

- The `IS NULL` operator checks if a value is `NULL`.
- The `IS NOT NULL` operator checks if a value is not `NULL`.
- `NULL` is not equal to any value, including itself.
- Use `IS NULL` and `IS NOT NULL` operators to filter `NULL` values in your queries.
