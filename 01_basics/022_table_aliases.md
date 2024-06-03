# PostgreSQL Table Aliases

**Summary**: This section discusses the PostgreSQL table aliases and their practical applications.

## Introduction to the PostgreSQL table aliases

Table aliases temporarily assign tables new names during the execution of a query.
The following illustrates the syntax of a table alias.

### Syntax of Table Aliases

```
table_name AS alias_name
```

In this syntax, the `table_name` is assigned an alias as `alias_name`.
Similar to column aliases, the `AS` keyword is optional.
You can omit the `AS` keyword as follows:

```
table_name alias_name
```

## Practical Applications of Table Aliases

Table aliases have several practical applications.

### 1. Using table aliases for the long table name to make queries more readable

If you must qualify a column name with a long table name, you can use a table alias to save some typing and make your query more readable.

For example, instead of using the following expression in a query:

```
a_very_long_table_name.column_name
```

you can assign the table `a_very_long_table_name` an alias like this:

```
a_very_long_table_name AS alias
```

and reference the `column_name` in the table `a_very_long_table_name` using the table alias:

```
alias.column_name
```

### 2. Using Table Aliases in Join Clauses

Typically, you often use a join clause to query data from multiple tables that have the same column name.
If you use the same column name that comes from multiple tables without fully qualifying them, you will get an error.

To avoid this error, you need to qualify these columns using the following syntax:

```
table_name.column_name
```

To make the query shorter, you can use the table aliases for the table names listed in the `FROM` clause and `INNER JOIN` clauses. For example:

```sql
SELECT
  c.customer_id,
  first_name,
  amount,
  payment_date
FROM
  customer c
INNER JOIN payment p
  ON p.customer_id = c.customer_id
ORDER BY
  payment_date DESC;
```

### 3. Using Table Aliases in Self-Join

When you join a table to itself (self-join), you need to use table aliases.
This is because referencing the same table multiple times within a query results in an error.

The following example shows how to reference the `employee` table twice in the same query using table aliases.

```sql
SELECT
  e.first_name AS employee
  m.first_name AS manager
FROM
  employee e
INNER JOIN employee m
  ON m.employee_id = e.manager_id
ORDER BY manager;
```
