# Exercises: PostgreSQL `WHERE`

## Setting Up a Temporary Test Database

To practice using the `WHERE` clause, we will create a temporary test database and a table called `test_customer`.

### 1. Creating a Temporary Test Database

```sql
CREATE DATABASE testdb;
```

### 2. Connecting to the Temporary Test Database

```bash
\c testdb
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
('Jamie', 'Rice', 'jamie.rice@example.com'),
('Jamie', 'Smith', 'jamie.smith@example.com'),
('Adam', 'Rodriguez', 'adam.rodriguez@example.com'),
('Ann', 'Green', 'ann.green@example.com'),
('Anne', 'Brown', 'anne.brown@example.com'),
('Annie', 'White', 'annie.white@example.com'),
('Brad', 'Motley', 'brad.motley@example.com'),
('Brad', 'Pitt', 'brad.pitt@example.com');
```

## Exercises

### Exercise 1: Using the `=` Operator

**Objective**: Retrieve rows for customers whose first names are `Jamie`.

**Task**: Use the `WHERE` clause with the `=` operator.

```sql
SELECT last_name, first_name FROM test_customer WHERE first_name = 'Jamie';
```

### Exercise 2: Using the `AND` Operator

**Objective**: Find customers whose first name is `Jamie` and last name is `Rice`.

**Task**: Use the `WHERE` clause with the `AND` operator.

```sql
SELECT last_name, first_name FROM test_customer WHERE first_name = 'Jamie' AND last_name = 'Rice';
```

### Exercise 3: Using the `OR` Operator

**Objective**: Find customers whose last name is `Rodriguez` or first name is `Adam`.

**Task**: Use the `WHERE` clause with the `OR` operator.

```sql
SELECT first_name, last_name FROM test_customer WHERE last_name = 'Rodriguez' OR first_name = 'Adam';
```

### Exercise 4: Using the `IN` Operator

**Objective**: Return customers whose first name is `Ann`, or `Anne`, or `Annie`.

**Task**: Use the `WHERE` clause with the `IN` operator.

```sql
SELECT first_name, last_name FROM test_customer WHERE first_name IN ('Ann', 'Anne', 'Annie');
```

### Exercise 5: Using the `LIKE` Operator

**Objective**: Return all customers whose first names start with `Ann`.

**Task**: Use the `WHERE` clause with the `LIKE` operator.

```sql
SELECT first_name, last_name FROM test_customer WHERE first_name LIKE 'Ann%';
```

### Exercise 6: Using the `BETWEEN` Operator

**Objective**: Find customers whose first names start with the letter `A` and contain 3 to 5 characters.

**Task**: Use the `WHERE` clause with the `BETWEEN` operator.

```sql
SELECT first_name, LENGTH(first_name) AS name_length
FROM test_customer
WHERE first_name LIKE 'A%' AND LENGTH(first_name) BETWEEN 3 AND 5
ORDER BY name_length;
```

### Exercise 7: Using the Not Equal (`<>`) Operator

**Objective**: Find customers whose first names start with `Bra` and last names are not `Motley`.

**Task**: Use the `WHERE` clause with the _not equal_ operator.

```sql
SELECT first_name, last_name
FROM test_customer
WHERE first_name LIKE 'Bra%' AND last_name <> 'Motley';
```
