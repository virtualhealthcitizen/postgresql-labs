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
