# Exercises: `SELECT DISTINCT`

## Setting Up a Temporary Test Database

To practice using the `DISTINCT` clause, we will create a temporary test database and a table called `distinct_demo`.

### 1. Creating a Temporary Test Database

```sql
CREATE DATABASE distinct_demo;
```

### 2. Connecting to the Temporary Test Database

```bash
\c testdb
```

### 3. Creating the `distinct_demo` Table and Inserting Data

```sql
CREATE TABLE distinct_demo (
  id serial NOT NULL PRIMARY KEY,
  bcolor VARCHAR,
  fcolor VARCHAR
);

INSERT INTO distinct_demo (bcolor, fcolor)
VALUES
  ('red', 'red'),
  ('red', 'red'),
  ('red', NULL),
  (NULL, 'red'),
  ('red', 'green'),
  ('red', 'blue'),
  ('green', 'red'),
  ('green', 'blue'),
  ('green', 'green'),
  ('blue', 'red'),
  ('blue', 'green'),
  ('blue', 'blue');
```

### Exercise 1: Using `DISTINCT` on One Column

**Objective**: Select unique values in the `bcolor` column.

**Task**: Use the `DISTINCT` clause to select unique values in the `bcolor` column and sort them in alphabetical order.

```sql
SELECT DISTINCT bcolor FROM distinct_demo ORDER BY bcolor;
```

### Exercise 2: Using `DISTINCT` on Multiple Columns

**Objective**: Select unique combinations of `bcolor` and `fcolor`.

**Task**: Use the `DISTINCT` clause to select unique combinations of `bcolor` and `fcolor` and sort them by `bcolor` and `fcolor`.

```sql
SELECT DISTINCT bcolor, fcolor FROM distinct_demo ORDER BY bcolor, fcolor;
```

### Exercise 3: Using `DISTINCT ON`

**Objective**: Select the first row of each group of duplicates based on the `bcolor` column.

**Task**: Use the `DISTINCT ON` clause to select the first row of each group of duplicates based on the `bcolor` column and sort them by `bcolor` and `fcolor`.

```sql
SELECT DISTINCT ON (bcolor) bcolor, fcolor FROM distinct_demo ORDER BY bcolor, fcolor;
```

## Cleaning Up

After completing the exercises, you may want to clean up by dropping the test database:

```sql
DROP DATABASE distinct_demo;
```

## Summary

- The `DISTINCT` clause removes duplicate rows from a result set.
- Use the `DISTINCT` clause to select unique values based on one or more columns.
- The `DISTINCT ON` clause allows you to keep the first row of each group of duplicates.
- Always use the `ORDER BY` clause with the `DISTINCT ON` expression to make the result set predictable.
