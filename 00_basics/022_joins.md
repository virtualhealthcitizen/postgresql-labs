# PostgreSQL Joins

**Summary**: The sections discusses various kinds of PostgreSQL join operations including
- inner join
- left join
- right join
- full outer join

PostgreSQL join is used to combine columns from one (self-join) or more tables based on the values of the common columns between related tables.
The common columns are typically the primary key columns of the first table and the foreign key columns of the second table.
PostgreSQL supports the following join operations:
- inner join
- left join
- right join
- full outer join
- cross join
- natural join
- a special kind of join called self-join

## Setting up the sample tables

Suppose you have two tables called `basket_a` and `basket_b` that store fruits:

```sql
CREATE TABLE basket_a (
  a INT PRIMARY KEY,
  fruit_a VARCHAR (100) NOT NULL
);

CREATE TABLE basket_b (
  b INT PRIMARY KEY,
  fruit_b VARCHAR (100) NOT NULL
);

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

The tables have some common fruits such as `apple` and `orange`.

Confirm that the following statement returns the displayed data from the `basket_a` table:

```sql
SELECT * FROM basket_a;
```

<img src="img/69.png" width="200" />

Confirm that the following statement returns the displayed data from the `basket_a` table:

```sql
SELECT * FROM basket_b;
```

<img src="img/70.png" width="200" />

## PostgreSQL inner join

The following statement joins the first table (`basket_a`) with the second table (`basket_b`) by matching the values in the `fruit_a` and `fruit_b` columns.

```sql
SELECT
  a,
  fruit_a,
  b,
  fruit_b
FROM
  basket_a
INNER JOIN basket_b
  ON fruit_a = fruit_b;
```

<img src="img/71.png" width="200" />

The inner join examines each row in the first table (`basket_a`).
It compares the value in the `fruit_a` column of each row in the second table (`basket_b`).
If these values are equal, the inner join creates a new row that contains columns from both tables and adds this new row to the result set.
The following Venn diagram illustrates the inner join:

<img src="img/72.png" width="200" />

## PostgreSQL left join

The following statement uses the left join clause to join the `basket_a` table with the `basket_b` table.
In the left join context, the first table is called the **left table** and the second table is called the **right table**.

```sql
SELECT
  a,
  fruit_a,
  b,
  fruit_b
FROM
  basket_a
LEFT JOIN basket_b
  ON fruit_a = fruit_b;
```

<img src="img/73.png" width="200" />

The left join starts selecting data from the left table.
It compares values in the `fruit_a` column with the values in the `fruit_b` column in the `basket_b` table.

If these values are equal, the left join creates a new row that contains columns of both tables and adds this new row to the result set. (See row #1 and row #2 in the result set.

In case the values are not equal, the left join also creates a new row that contains columns from both tables and adds it to the result set. However, it fills the columns of the right table (`basket_b`) with `NULL`. (See row #3 and row #4 in the result set.)

The following Venn diagram illustrates the left join:

<img src="img/74.png" width="200" />

To select rows from the left table that do not have matching rows in the right table, you use the left join with a `WHERE` clause. For example:

```sql
SELECT
  a,
  fruit_a,
  b
  fruit_b
FROM
  basket_a
LEFT JOIN basket_b
  ON fruit_a = fruit_b
WHERE b IS NULL;
```

<img src="img/75.png" width="200" />

<blockquote>
Note that the <code>LEFT JOIN</code> is the same as the <code>LEFT OUTER JOIN</code> so you can use them interchangeably.
</blockquote>

The following Venn diagram illustrates the left join that returns rows from the left table which do now have matching rows from the right table:

<img src="img/76.png" width="200" />
