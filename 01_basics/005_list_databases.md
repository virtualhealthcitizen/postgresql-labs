# **List databases**

PostgreSQL provides several ways to list databases.
This can be done using the `psql` command-line interface or through SQL queries.
Below, we explore both methods in detail.

## Using `psql` console

1. **Basic Command**:
   
   To list all databases in your PostgreSQL instance, you can use the following command in the `psql` console:

   ```bash
   \l
   ```

   ![03.png](img/03.png)

   This command displays a list of all databases along with information such as the database name, owner, encoding, collation, character type, and access provileges.

2. **Extended Command**:

   Another variant to list databases is:

   ```bash
   \list
   ```
   
   This is simply an alternative to `\l` and provides the same output.

## Using SQL query

You can also list databases using an SQL query within the `psql` console or any PostgreSQL client application:

### 1. **Querying the `pg_database` System Catalog**:

```sql
SELECT datname FROM pg_database;
```

This command will return a list of database names.
The `pg_database` catalog contains information about all the databases in the PostgreSQL cluster.

### 2. **Detailed Information**:

If you want more detailed information about each database, you can use:

```sql
SELECT
    datname,
    datdba,
    encoding,
    datcollate,
    datctype,
    datistemplate,
    datallowconn,
    datconnlimit,
    datlastssysoid,
    datfrozenxid,
    datminxid,
    dattablespace,
    datacl
FROM pg_database;
```

This query will provide comprehensive details about each database, similar to the `\l` command.

## Filtering Results

To filter the list of databases based on specific criteria, you can add a `WHERE` clause to your SQL query.
For example, to list databases owned by a specific user:

```sql
SELECT datname
FROM pg_database
WHERE datdba = (SELECT usesysid FROM pg_user WHERE usename = 'username');
```

## Using pgAdmin

If you prefer a graphical interface, pgAdmin is a popular choice for managing PostgreSQL databases.
To list databases in pgAdmin:

1. Open pgAdmin and connect to your PostgreSQL server.
2. In the Browser pane, expand the server node to see the list of databases.

## Practical Use Cases

### 1. Verifying Database Creation

After creating a new database, use the `\l` or equivalent SQL query to ensure the database has been created successfully.

### 2. Database Management

Periodically listing databases can help in monitoring and managing the databases on your server, including checking for unauthorized or unnecessary databases.

### 3. Access Privileges

By listing databases, you can also review the access privileges to ensure that the correct users have appropriate permissions.

## Summary

Listing databases is a fundamental task in PostgreSQL administration.
Whether using command-line tools like `psql`, executing SQL queries, or leveraging graphical tools like pgAdmin, knowing how to list databases effectively is crucial for managing and organizing your PostgreSQL environment.
