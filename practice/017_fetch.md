# Exercises: `FETCH`

## Setting Up a Temporary Test Database

To practice using the `FETCH` clause, we will create a temporary test database and a table called `test_film`.

### 1. Creating a Temporary Test Database

```sql
CREATE DATABASE test_film;
```

### 2. Connecting to the Temporary Test Database

```bash
\c test_film
```

### 3. Creating the `test_film` Table and Inserting Data

```sql
CREATE TABLE test_film (
  film_id SERIAL PRIMARY KEY,
  title VARCHAR(255) NOT NULL,
  release_year INT,
  rental_rate NUMERIC(4,2)
);

INSERT INTO test_film (title, release_year, rental_rate) VALUES
('Film A', 2001, 4.99),
('Film B', 2002, 3.99),
('Film C', 2003, 5.99),
('Film D', 2004, 2.99),
('Film E', 2005, 6.99),
('Film F', 2006, 4.49),
('Film G', 2007, 5.49),
('Film H', 2008, 3.49),
('Film I', 2009, 6.49),
('Film J', 2010, 2.49);
```

## Exercises

### Exercise 1: Using `FETCH` Clause

**Objective**: Retrieve the first row sorted by `title`.

**Task**: Use the `FETCH` clause to get the first row.

```sql
SELECT film_id, title
FROM test_film
ORDER BY title
FETCH FIRST ROW ONLY;
```

### Exercise 2: Using `FETCH` to Select Multiple Rows

**Objective**: Retrieve the first 5 rows sorted by `title`.

**Task**: Use the `FETCH` caluse to get the first 5 rows.

```sql
SELECT film_id, title
FROM test_film
ORDER BY title
FETCH FIRST 5 ROWS ONLY;
```

### Exercise 3: Using `FETCH` with `OFFSET`

**Objective**: Retrieve the next 5 rows after skipping the first 5 rows, sorted by `title`.

**Task**: Use the `FETCH` clause with `OFFSET` to get the rows.

```sql
SELECT film_id, title
FROM test_film
ORDER BY title
OFFSET 5 ROWS
FETCH NEXT 5 ROWS ONLY;
```

### Exercise 4: Combining `FETCH` with `WHERE`

**Objective**: Retrieve the first 3 films released after the year 2005, sorted by `release_year`.

**Task**: Use the `FETCH` clause with a `WHERE` clause and `ORDER BY` to get the films.

```sql
SELECT film_id, title, release_year
FROM test_film
WHERE release_year > 2005
ORDER BY release_year
FETCH FIRST 3 ROWS ONLY;
```

## Cleaning Up

After completing the exercises, you may want to clean up by dropping the test database:

```sql
DROP DATABASE test_film;
```

## Summary

- The `FETCH` clause retrieves a specific number of rows returned by a query.
- The `OFFSET` clause skips a specified number of rows before returning the result set.
- Always use the `ORDER BY` clause with the `FETCH` clause to ensure the rows are returned in a specified order.
- The `FETCH` clause is SQL-standard and is functionally equivalent to the `LIMIT` clause.
