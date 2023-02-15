### **Connect to a database**

In the psql console, just issue

```shell
\c db_name
```

e.g.,

```shell
\c test_db
```

In the below screenshot:
- the databases are listed using the `\l` psql command
- the user connects to the `test_db` database using the `\c` psql command

![04.png](img/04.png)

Note that you can log in to the PostgreSQL server and connect to a specific database using one command:

```shell
psql -U postgres -d db_name
```

The above command connects to the database `db_name` as the `postgresql` user.

The `-d` flag means **d**atabase.