### **Create a database from psql**

While there are many ways to create a database in *PostgreSQL*, the below example has been generated in *pgAdmin 4*, and is a fairly standard way to create a database.

It includes all the parameters one would specify when creating a database using *pgAdmin 4*.

```sql
CREATE DATABASE db_name
    WITH
    OWNER = user_name
    TEMPLATE = postgres
    ENCODING = 'UTF-8'
    LC_COLLATE = 'C'
    LC_CTYPE = 'C'
    TABLESPACE = pg_default
    CONNECTION LIMIT = -1
    IS_TEMPLATE = False;
```

### Example

```sql
CREATE DATABASE session_db
    WITH
    OWNER = postgres
    TEMPLATE = postgres
    ENCODING = 'UTF-8'
    LC_COLLATE = 'C'
    LC_CTYPE = 'C'
    TABLESPACE = pg_default
    CONNECTION LIMIT = -1
    IS_TEMPLATE = False;
```
