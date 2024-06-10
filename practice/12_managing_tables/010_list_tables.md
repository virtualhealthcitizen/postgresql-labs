# Exercises: List Tables in a Database

## Using the DVD Rental Database

### Exercise 1: Basic Listing Using `psql`

**Objective**: List all tables in the test database using `psql`.

**Task**: Use the command to list tables.

```bash
\dt
```

**Expected Result**: A list of all tables in the current schema.

### Exercise 2: Extended Information Using `psql`

**Objective**: Retrieve detailed information about tables using `psql`.

**Task**: Use the extended command to list tables with additional details.

```bash
\dt+
```

**Expected Result**: A list of tables with size and description information.

### Exercise 3: List Tables Using SQL Query

**Objective**: List all user-defined tables using an SQL query.

**Task**: Execute the following query:

```sql
SELECT tablename
FROM pg_catalog.pg_tables
WHERE schemaname = 'public';
```

**Expected Result**: A list of user-defined tables in the `'public'` schema.

### Exercise 4: Including System Tables

**Objective**: List all tables, including system tables, using an SQL query.

**Task**: Execute the following query without filtering system tables:

```sql
SELECT *
FROM pg_catalog.pg_tables;
```

**Expected Result**: A comprehensive list of all tables, including system tables.

## Using a Temporary Test Database

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
CREATE TABLE test_table1 (
    id SERIAL PRIMARY KEY,
    name VARCHAR(100) NOT NULL
);

CREATE TABLE test_table2 (
    id SERIAL PRIMARY KEY,
    description TEXT
);
```

### Exercise 5: Listing Tables in the Test Database

**Objective**: List all tables in the test database.

**Task**: Use the `psql` command and SQL queries to list tables in the test database.

**Expected Result**:

```bash
\dt
```

```sql
SELECT tablename
FROM pg_catalog.pg_tables
WHERE schemaname = 'public';
```

## Cleaning Up

After completing the exercises you may want to clean up by dropping the test database:

```sql
DROP DATABASE testdb;
```

## Summary

Listing tables in PostgreSQL can be done using the `psql` command-line tool or through SQL queries.
By practicing these methods, you can efficiently manage and explore the tables in your database.
