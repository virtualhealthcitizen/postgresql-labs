# **List tables in a database**

Listing tables in a PostgreSQL database can be done using the `psql` command-line interface or through SQL queries.
Below, we explore both methods in detail.

## Using `psql`

### 1. Basic Command

To list all tables in the current database, use the following command from the `psql` command prompt:

```bash
\dt
```

This command shows a list of all tables in the current schema.

### 2. Extended Information

To get more detailed information about the tables, including size and description, use:

```bash
\dt+
```

This command provides additional columns such as `size` and `description`.

## Using SQL Query

### 1. Querying the `pg_tables` System Catalog

You can use a `SELECT` statement to retrieve information about tables.
The `pg_tables` system catalog contains metadata about all tables in the database.

```sql
SELECT *
FROM pg_catalog.pg_tables
WHERE schemaname != 'pg_catalog' AND
      schemaname != 'information_schema';
```

This query filters out the system tables and lists only user-defined tables.

If you omit the `WHERE` clause, you will get many tables including the system tables.

### 2. Listing All Tables Including System Tables

If you want to include system tables, you can omit the `WHERE` clause:

```sql
SELECT *
FROM pg_catalog.pg_tables;
```

This will return a comprehensive list of all tables, including system tables.

## Using the DVD Rental Database

For practical examples, let's use the DVD Rental database.

### 1. List All Tables

```bash
\dt
```

This command will display all tables in the DVD Rental database.

### 2. List Tables with Extended Information

```bash
\dt+
```

This will provide additional details about each table, such as size and description.

### 3. SQL Query to List User-Defined Tables

```sql
SELECT tablename
FROM pg_catalog.pg_tables
WHERE schemaname = 'public';
```

This query lists all user-defined tables in the `public` schema of the DVD Rental database.
