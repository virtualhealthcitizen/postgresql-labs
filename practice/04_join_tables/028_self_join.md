# Exercises: Self-Join

## Setting Up a Temporary Test Database

To practice using self-joins, we will create a temporary test database and tables called `employee` and `film`.

## Creating a Temporary Test Database

### 1. Creating a Temporary Test Database

```sql
CREATE DATABASE testdb;
```

### 2. Connecting to the Temporary Test Database

```bash
\c testdb
```

## Creating the `employee` and `film` Tables and Inserting Data

### 3. Creating the `employee` Table

```sql
CREATE TABLE employee (
    employee_id SERIAL PRIMARY KEY,
    first_name VARCHAR(255) NOT NULL,
    last_name VARCHAR(255) NOT NULL,
    manager_id INT,
    FOREIGN KEY (manager_id) REFERENCES employee (employee_id) ON DELETE CASCADE
);
```

### 4, Inserting Data into the `emplyoee` Table

```sql
INSERT INTO employee (employee_id, first_name, last_name, manager_id)
VALUES
    (1, 'Windy', 'Hays', NULL),
    (2, 'Ava', 'Christensen', 1),
    (3, 'Hassan', 'Conner', 1),
    (4, 'Anna', 'Reeves', 2),
    (5, 'Sau', 'Norman', 2),
    (6, 'Kelsie', 'Hays', 3),
    (7, 'Tory', 'Goff', 3),
    (8, 'Salley', 'Lester', 3);
```

### 5. Creating the `film` Table

```sql
CREATE TABLE film (
    film_id SERIAL PRIMARY KEY,
    title VARCHAR(255) NOT NULL,
    length INT
);
```

### 6, Inserting Data into the `film` Table

```sql
INSERT INTO film (title, length)
VALUES
    ('Chamber Italian', 117),
    ('Affair Prejudice', 117),
    ('Grosse Wonderful', 49),
    ('Doors President', 49),
    ('Bright Encounters', 73),
    ('Bedazzled Married', 73),
    ('Date Speed', 104),
    ('Crow Grease', 104),
    ('Annie Identity', 86),
    ('Academy Dinosaur', 86);
```

## Exercise 1: Querying Hierarchical Data

**Objective**: Use a self-join to find who reports to whom.

**Task**: Query the `employee` table to find each employee and their manager.

```sql
SELECT
    e.first_name || ' ' || e.last_name AS employee,
    m.first_name || ' ' || m.last_name AS manager
FROM
    employee e
    INNER JOIN employee m ON m.employee_id = e.manager_id
ORDER BY
    manager;
```

## Exercise 2: Including the Top Manager in the Result Set

**Objective**: Use a self-join with a `LEFT JOIN` to include the top manager in the result set.

**Task**: Query the `employee` table to find each employee and their manager, including the top manager.

```sql
SELECT
    e.first_name || ' ' || e.last_name AS employee,
    m.first_name || ' ' || m.last_name AS manager
FROM employee e
LEFT JOIN employee m ON m.employee_id = e.manager_id
ORDER BY
    manager;
```

## Exercise 3: Comparing Rows Within the Same Table

**Objective**: Use a self-join to find all pairs with the same length.

**Task**: Query the `film` table to find all pairs of films that have the same length.

```sql
SELECT
    f1.title,
    f2.title,
    f1.length
FROM film f1
INNER JOIN film f2 ON f1.film_id > f2.film_id
    AND f1.length = f2.length;
```

## Cleaning Up

After completing the exercises, you may want to clean up by dropping the test database:

```sql
DROP DATABASE testdb;
```

## Summary

- A PostgreSQL self-join is a regular join that joins a table to itself using the `INNER JOIN`, `LEFT JOIN`, or `RIGHT JOIN`.
- Self-joins are very useful for querying hierarchical data or comparing rows within the same table.
