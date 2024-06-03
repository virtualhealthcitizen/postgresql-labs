# Exercises: `BETWEEN`

Let's use a temporary test table similar to the `payment` table in the `dvdrental` sample database for the demonstration.

## Setting Up the Temporary Test Database

To practice using the `BETWEEN` operator, we will create a temporary test database and a table called `test_payment`.

### 1. Creating a Temporary Test Database

```sql
CREATE DATABASE test_payment;
```

### 2. Connecting to the Temporary Test Database

```bash
\c test_payment
```

### 3. Creating the `test_payment` Table and Inserting Data

```sql
CREATE TABLE test_payment (
    payment_id SERIAL PRIMARY KEY,
    customer_id INT NOT NULL,
    amount NUMERIC(5,2) NOT NULL,
    payment_date DATE NOT NULL
);

INSERT INTO test_payment (customer_id, amount, payment_date)
VALUES
(1, 8.50, '2023-01-01'),
(2, 9.00, '2023-01-02'),
(3, 7.50, '2023-01-03'),
(1, 8.00, '2023-01-04'),
(2, 6.50, '2023-01-05'),
(3, 10.00, '2023-01-06');
```

## Exercises

### Exercise 1: Using the `BETWEEN` Operator

**Objective**: Retrieve payments whose amount is between **8** and **10** (USD).

**Task**: Use the `BETWEEN` operator in the `WHERE` clause.

```sql
SELECT customer_id, payment_id, amount
FROM test_payment
WHERE amount BETWEEN 8 AND 10;
```

### Exercise 2: Using the `NOT_BETWEEN` Operator

**Objective**: Retrieve payments whose amount is not between **8** and **10** (USD).

**Task**: Use the `NOT BETWEEN` operator in the `WHERE` clause.

```sql
SELECT customer_id, payment_id, amount
FROM test_payment
WHERE amount NOT BETWEEN 8 AND 10;
```

### Exercise 3: Using the `BETWEEN` Operator with Dates

**Objective**: Retrieve payments whose payment date is between `2023-01-01` and `2023-01-03`.

**Task**: Use the `BETWEEN` operator with dates in the `WHERE` clause.

```sql
SELECT customer_id, payment_id, amount, payment_date
FROM test_payment
WHERE payment_date BETWEEN '2023-01-01' AND '2023-01-03';
```

### Exercise 4: Using the `BETWEEN` Operator with Numbers

**Objective**: Retrieve payments for customer ID **1** whose amount is between **8** and **9** (USD).

**Task**: Use the `BETWEEN` operator with numbers in the `WHERE` clause.

```sql
SELECT customer_id, payment_id, amount
FROM test_payment
WHERE customer_id = 1 AND amount BETWEEN 8 AND 9;
```

## Cleaning Up

After completing the exercises, you may want to clean up by dropping the test database:

```sql
DROP DATABASE test_payment;
```

## Summary

- The `BETWEEN` operator matches a value against a range of values.
- The `NOT BETWEEN` operator checks if a value is out of a specified range.
- The `BETWEEN` operator can be used with dates, numbers, and other types.
- The `BETWEEN` operator is often used in the `WHERE` clause of a `SELECT`, `INSERT`, `UPDATE`, or `DELETE` statement.
