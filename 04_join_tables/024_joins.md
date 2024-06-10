# PostgreSQL Joins

**Summary**: The sections discusses various kinds of PostgreSQL join operations including:

- inner join
- left join
- right join
- full outer join
- cross join
- natural join
- self-join

PostgreSQL join is used to combine columns from one (self-join) or more tables based on the values of the common columns between related tables.
The common columns are typically the primary key columns of the first table and the foreign key columns of the second table.
PostgreSQL supports the following join operations:

- inner join
- left join
- right join
- full outer join
- cross join
- natural join
- self-join

## Setting Up the Sample Tables

To practice using joins, we will create a temporary test database and tables called `basket_a` and `basket_b` that store fruits.

### Creating a Temporary Test Database

```sql
CREATE DATABASE testdb;
```

```bash
\c testdb
```

### Creating the `basket_a` and `basket_b` Tables and Inserting Data

Suppose you have two tables called `basket_a` and `basket_b` that store fruits:

### Creating the Tables

```sql
CREATE TABLE basket_a (
  a INT PRIMARY KEY,
  fruit_a VARCHAR (100) NOT NULL
);

CREATE TABLE basket_b (
  b INT PRIMARY KEY,
  fruit_b VARCHAR (100) NOT NULL
);
```

### Inserting Data

```sql
INSERT INTO basket_a (a, fruit_a)
VALUES
  (1, 'Apple'),
  (2, 'Orange'),
  (3, 'Banana'),
  (4, 'Cucumber');
  
INSERT INTO basket_b (b, fruit_b)
VALUES
  (1, 'Orange'),
  (2, 'Apple'),
  (3, 'Watermelon'),
  (4, 'Pear');
```

Notice that the tables have some common fruits such as `apple` and `orange`.

### Confirming the Data

Confirm that the following statement returns the expected data from the `basket_a` table:

```sql
SELECT * FROM basket_a;
```

<img src="img/69.png" width="200" />

Confirm that the following statement returns the expected data from the `basket_b` table:

```sql
SELECT * FROM basket_b;
```

<img src="img/70.png" width="200" />
