# Exercises: Joins

## Setting Up the Sample Tables

To practice using joins, we will create a temporary test database and tables called `basket_a` and `basket_b` that store fruits.

### Creating a Temporary Test Database

```sql
CREATE DATABASE testdb;
```

```bash
\c testdb
```

### Creating the `basket_a` and `basket_b` Tables and Inserting Data

Suppose you have two tables called `basket_a` and `basket_b` that store fruits:

### Creating the Tables

```sql
CREATE TABLE basket_a (
  a INT PRIMARY KEY,
  fruit_a VARCHAR (100) NOT NULL
);

CREATE TABLE basket_b (
  b INT PRIMARY KEY,
  fruit_b VARCHAR (100) NOT NULL
);
```

### Inserting Data

```sql
INSERT INTO basket_a (a, fruit_a)
VALUES
  (1, 'Apple'),
  (2, 'Orange'),
  (3, 'Banana'),
  (4, 'Cucumber');
  
INSERT INTO basket_b (b, fruit_b)
VALUES
  (1, 'Orange'),
  (2, 'Apple'),
  (3, 'Watermelon'),
  (4, 'Pear');
```

Notice that the tables have some common fruits such as `apple` and `orange`.

## Exercises

### Exercise 1: Inner Join

**Objective**: Join `basket_a` and `basket_b` tables by matching the `fruit_a` and `fruit_b` columns.

**Task**: Use the `INNER JOIN` to match the columns.

```sql
SELECT a, fruit_a, b, fruit_b
FROM basket_a
INNER JOIN basket_b ON fruit_a = fruit_b;
```

### Exercise 2: Left Join

**Objective**: Perform a left join between `basket_a` and `basket_b` tables by matching the `fruit_a` and `fruit_b` columns.

**Task**: Use the `LEFT JOIN` to match the columns.

```sql
SELECT a, fruit_a, b, fruit_b
FROM basket_a
LEFT JOIN basket_b ON fruit_a = fruit_b;
```

### Exercise 3: Right Join

**Objective**: Perform a right join between `basket_a` and `basket_b` tables by matching the `fruit_a` and `fruit_b` columns.

**Task**: Use the `RIGHT JOIN` to match the columns.

```sql
SELECT a, fruit_a, b, fruit_b
FROM basket_a
RIGHT JOIN basket_b ON fruit_a = fruit_b;
```

### Exercise 4: Full Outer Join

**Objective**: Perform a full outer join between `basket_a` and `basket_b` tables by matching the `fruit_a` and `fruit_b` columns.

**Task**: Use the `FULL OUTER JOIN` to match the columns.

```sql
SELECT a, fruit_a, b, fruit_b
FROM basket_a
FULL OUTER JOIN basket_b ON fruit_a = fruit_b;
```

### Exercise 5: Left Join with `WHERE` Clause

**Objective**: Select rows from `basket_a` that do not have matching rows in `basket_b`.

**Task**: Use the `LEFT JOIN` with a `WHERE` clause.

```sql
SELECT a, fruit_a, b, fruit_b
FROM basket_a
LEFT JOIN basket_b ON fruit_a = fruit_b
WHERE b IS NULL;
```

### Exercise 6: Right Join with `WHERE` Clause

**Objective**: Select rows from `basket_b` that do not have matching rows in `basket_a`.

**Task**: Use the `RIGHT JOIN` with a `WHERE` clause.

```sql
SELECT a, fruit_a, b, fruit_b
FROM basket_b
RIGHT JOIN basket_a ON fruit_a = fruit_b
WHERE a IS NULL;
```

## Cleaning Up

After completing the exercises, you may want to clean up by dropping the test database:

```sql
DROP DATABASE testdb;
```

## Summary

- Inner join returns rows when there is a match in both tables.
- Left join returns all rows from the left table and matching rows from the right table.
- Right join returns all rows from the right table and matching rows from the left table.
- Full outer join returns rows when there is a match in one of the tables.
- Use the `WHERE` clause with joins to filter the result set based on the join conditions.
