### **List tables in a database**

<br />

#### Using `psql`

From the psql command prompt, use the command:

```shell
\dt
```

To get more information on tables, you can use the command:

```shell
\dt+
```

Doing so will add the `size` and `description` columns.

---

#### Using a `SELECT` statement (`pg_catalog` schema)

```sql
SELECT *
FROM pg_catalog.pg_tables
WHERE schemaname != 'pg_catalog' AND
      schemaname != 'information_schema';
```

In this query, a condition is used in the `WHERE` clause to filter system tables. If you omit the `WHERE` clause, you will get many tables including the system tables.