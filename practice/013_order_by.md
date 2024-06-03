# Exercises: `ORDER BY`

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

### Exercise 1: Sorting by One Column in Ascending Order

**Objective**: Sort the rows by the first name in ascending order.

**Task**: Use the `ORDER BY` clause to sort the rows by the `first_name` column in ascending order.

```sql
SELECT first_name, last_name FROM test_customer ORDER BY first_name ASC;
```

### Exercise 2: Sorting by One Column in Descending Order

**Objective**: Sort the rows by the last name in descending order.

**Task**: Use the `ORDER BY` clause the sort the rows by the `last_name` column in descending order.

```sql
SELECT first_name, last_name, FROM test_customer ORDER BY last_name DESC;
```

### Exercise 3: Sorting by Multiple Columns

**Objective**: Sort the rows by the first name in ascending order and the last name in descending order.

**Task**: Use the `ORDER BY` clause to sort the rows by multiple columns.

```sql
SELECT first_name, last_name FROM test_customer ORDER BY first_name ASC, last_name DESC;
```

### Exercise 4: Sorting by Expressions

**Objective**: Sort the rows by the length of the first name in descending order.

**Task**: Use the `ORDER BY` clause to sort the rows by the length of the first name.

```sql
SELECT first_name, LENGTH(first_name) AS len FROM test_customer ORDER BY len DESC;
```

### Exercise 5: Sorting with `NULL` Values

**Objective**: Sort rows with `NULL` values explicitly.

**Task**: Create a new table `sort_demo` and insert values including `NULL`.
Sort the rows placing `NULL` values first.

**Steps**:
- Create and populate the `sort_demo` table.

  ```sql
  CREATE TABLE sort_demo (
      num INT
  );
  
  INSERT INTO sort_demo (num) VALUES (1), (2), (3), (NULL);
  ```
  
- Sort the rows with `NULL` values first.

  ```sql
  SELECT num FROM sort_demo ORDER BY num NULLS FIRST; 
  ```

With these exercises, you can practice using the `ORDER BY` clause in various scenarios to better understand how it sorts result sets in PostgreSQL.
