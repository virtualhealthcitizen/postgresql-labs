# Exercises: `LIMIT`

## Setting Up a Temporary Test Database

To practice using the `LIMIT` clause, we will create a temporary test database and a table called `test_film`.

### 1. Creating a Temporary Test Database

```sql
CREATE DATABASE testdb;
```

### 2. Connecting to the Temporary Test Database

```bash
\c testdb
```

### 3. Creating the `test_film` Table and Inserting Data

```sql
CREATE TABLE test_film (
    film_id SERIAL PRIMARY KEY,
    title VARCHAR(255) NOT NULL,
    release_year INT,
    rental_rate NUMERIC(4,2)
);

INSERT INTO test_film (title, release_year, rental_rate)
VALUES
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

### Exercise 1: Using `LIMIT` Clause

**Objective**: Retrieve the first 5 films sorted by `film_id`.

**Task**: Use the `LIMIT` clause to get the first 5 films.

```sql
SELECT film_id, title, release_year FROM test_film ORDER BY film_id LIMIT 5;
```

### Exercise 2: Using `LIMIT` with `OFFSET`

**Objective**: Retrieve 4 films starting from the fourth one ordered by `film_id`.

**Task**: Use the `LIMIT` and `OFFSET` clauses to get the films.

```sql
SELECT film_id, title, release_year FROM test_film ORDER BY film_id LIMIT 4 OFFSET 3;
```

### Exercise 3: Using `LIMIT` to Get Top 10 Rows

**Objective**: Retrieve the top 5 most expensive films in terms of rental state.

**Task**: Use the `LIMIT` clause with `ORDER BY` to get the top 5 films by rental rate.

```sql
SELECT film_id, title, rental_rate FROM test_film ORDER BY rental_rate DESC LIMIT 5;
```

### Exercise 4: Combining `LIMIT` with `WHERE`

**Objective**: Retrieve the first 3 films released after the year 2005, sorted by `release_year`.

**Task**: Use the `LIMIT` clause with a `WHERE` clause and `ORDER BY` to get the films.

```sql
SELECT film_id, title, release_year FROM test_film WHERE release_year > 2005 ORDER BY release_year LIMIT 3;
```

## Cleaning Up

After completing the exercises, you may want to clean up by dropping the test database:

```sql
DROP DATABASE test_film;
```

## Summary

- The `LIMIT` clause constrains the number of rows returned by a query.
- The `OFFSET` clause skips a specified number of rows before returning the result set.
- Always use the `ORDER BY` clause with the `LIMIT` clause to ensure the rows are returned in a specified order.
