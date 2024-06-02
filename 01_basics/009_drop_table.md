# `DROP TABLE`

The `DROP TABLE` command is used to remove an existing table from the database.
This action is irreversible, meaning once a table is dropped, all the data stored in that table is permanently deleted.

## General Syntax

The basic syntax for dropping a table is:

```sql
DROP TABLE table_name;
```

## Case-Sensitive Table Names

If the table name is case-sensitive, it must be enclosed in double-quotes (`"`), e.g.:

```sql
DROP TABLE "Case_Sensitive";
```

## Cascading Drops

To drop a table and all its dependent objects (such as foreign keys in other tables), you can use the `CASCADE` option:

```sql
DROP TABLE table_name CASCADE;
```

This command will drop the `film` table and automatically drop any foreign key constraints that depend on it, such as those in the `film_actor` table.

## Checking Dependencies

Before dropping a table, it's often useful to check which objects depend on it.
This helps avoid accidental data loss or integrity issues.
You can use the `pg_depend` system catalog to investigate dependencies, though tools like **_pgAdmin_** provide easier interfaces for this purpose.
