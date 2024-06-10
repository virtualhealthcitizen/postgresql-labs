# Exercises: `DROP TABLE`

## Set up a temporary database with temporary tables for this exercise

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
CREATE TABLE test_category (
  category_id SERIAL PRIMARY KEY,
  name VARCHAR(100) NOT NULL
);

CREATE TABLE test_film (
  film_id SERIAL PRIMARY KEY,
  title VARCHAR(255) NOT NULL,
  description TEXT
);

CREATE TABLE test_film_category (
  film_id INT NOT NULL,
  category_id INT NOT NULL,
  PRIMARY KEY (film_id, category_id),
  FOREIGN KEY (film_id) REFERENCES test_film (film_id),
  FOREIGN KEY (category_id) REFERENCES test_category (category_id)
);
```

## Exercises

### Exercise 1: Dropping a simple table

**Objective**: Drop a simple t able from the test database.

**Task**: Drop the `test_category` table from the test database.

**Expected Result**:

```sql
DROP TABLE test_category;
```
   
### Exercise 2: Dropping a Case-Sensitive Table

**Objective**: Drop a table with a case-sensitive name.

**Task**: Create a table named `"SensitiveTable"` in the test database and then drop it.

**Expected Result**:

```sql
CREATE TABLE "SensitiveTable" (
  id SERIAL PRIMARY KEY,
  data VARCHAR(100)
);

DROP TABLE "SensitiveTable";
```

### Exercise 3: Dropping a Table with Dependencies

**Objective**: Drop a table that is referenced by other tables.

**Task**: Attempt to drop the `test_film` table without using `CASCADE` and observe the error.
Then, drop the table using `CASCADE`.

**Expected Result**:

```sql
DROP TABLE test_film; -- This should produce an error

DROP TABLE test_film CASCADE; -- This should succeed
```

### Exercise 4: Checking Dependencies

**Objective**: Check the dependencies of a table before dropping it.

**Task**: Use pgAdmin or the `pg_depend` catalog to check the dependencies of the `test_film` table.

**Steps**:
- Open pgAdmin and connect to your `testdb` database.
- Navigate to the `test_film` table and view its dependencies.

**Expected Result**: Identify the tables and constraints that depend on the `test_flim` table.

## Cleaning Up

After completing the exercises, you may want to clean up by dropping the test database.

```sql
DROP DATABASE testdb;
```

## Summary

The `DROP TABLE` command is a powerful tool for removing tables from a PostgreSQL database.
It is essential to use it cautiously, especially with tables that have dependencies.
The `CASCADE` option can simplify dropping complex tables with multiple dependencies, but it should be used with care to avoid unintended data loss.
