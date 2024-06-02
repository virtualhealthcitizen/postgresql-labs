# PostgreSQL `SERIAL`

In PostgreSQL, the `serial` keyword is a pseudo-type which allows us to define **auto-increment columns** in tables.

This particular kind of database object generator is used to **create a sequence of integers** that are frequently used as a **primary key** in a table.

```sql
CREATE TABLE table_name(
  ID SERIAL
);
```

PostgreSQL does the following if we provide the `SERIAL` pseudo-type to the `ID` column.
1. PostgreSQL will create a sequence object and then establish the next value created by the sequence as the particular column's pre-defined value.
2. PostgreSQL will enhance a `NOT NULL` constraint to the `ID` column since a sequence always produces an integer that is a **non-null value**.
3. PostgreSQL will make the `ID` column the owner of the sequence.
   The sequence object will be removed when the table or `ID` column is dropped.

Either of the below commands can be used to specify the `serial` pseudo-type:

```sql
CREATE TABLE table_name(
 ID SERIAL
);
```

```sql
CREATE SEQUENCE table_name_ID_seq;
CREATE TABLE table_name(
 ID integer NOT NULL DEFAULT nextval('table_name_ID_seq')
);

ALTER SEQUENCE table_name_ID_seq
OWNED BY table_name.ID;
```

## `SERIAL` pseudo-type classifications

The PostgreSQL `SERIAL` pseudo-type has been classified into three types:
- `SMALLSERIAL`
- `SERIAL`
- `BIGSERIAL`

The following table contains each `SERIAL` pseudo-type specification that is supported by PostgreSQL:

| Name          | Storage Size | Range                    |
|---------------|--------------|--------------------------|
| `SMALLSERIAL` | 2 bytes      | 1 to 32767               |
| `SERIAL`      | 4 bytes      | 1 to 2147483647          |
| `SMALLSERIAL` | 8 bytes      | 1 to 9223372036854775807 |

## Syntax of the `SERIAL` type

Let's see different examples to understand how the PostgreSQL `SERIAL` pseudo-type works.

In the following PostgreSQL snippets, we are creating one new table with the `CREATE` command and inserting some values using the `INSERT` command.

> **Note**: The `PRIMARY KEY` constraint can, and often should, be defined for the `SERIAL` column because the `SERIAL` pseudo-type does not indirectly create an index on the column or make the column the primary key of a table.

## Example 1: `cars` table

### `CREATE`

In the below example, we are using the `CREATE` command to generate a `cars` table in the `organization` database.

```sql
CREATE TABLE cars(
  car_id SERIAL PRIMARY KEY,
  car_name VARCHAR NOT NULL,
  car_model VARCHAR NOT NULL
);
```

**Output**

The `cars` table has been successfully created after executing the above commands, as shown in the below screenshot.

(_insert screenshot after completing lab_)

### `INSERT`

Once the `cars` table has been generated, we can insert some values into it using the `INSERT` command.

We can use the `DEFAULT` keyword in the `INSERT` command or omit the column name (`car_id`).

#### Omitting the column name

```sql
INSERT INTO cars(car_name, car_model)
VALUES('Porsche', '911 Carrera');
```

**Output**

The values have been inserted into the `cars` table successfully.

(_insert screenshot after completing the lab_)

#### Using the `DEFAULT` keyword with the column name

```sql
INSERT INTO cars(car_id, car_name, car_model)
VALUES(DEFAULT, 'Audi', 'A8');
```

**Output**

The values have been inserted into the `cars` table successfully.

(_insert screenshot after completing the lab_)

### `SELECT`

After creating and inserting values into the `cars` table, we'll use the `SELECT` command to return all rows of the `cars` table.

```sql
SELECT * FROM cars;
```

**Output**

(_insert screenshot after completing the lab_)

### `pg_get_serial_sequence()`

We can use the `pg_get_serial_sequence()` function to get the sequence name of a `SERIAL` column in a specified table:

```sql
pg_get_serial_sequence('table_name', 'column_name')
```

#### Using `currval()` with `pg_get_serial_sequence()`

To get the **current value** created by the sequence, we can pass a sequence name to the `currval()` function.

In the following example, we use the `currval()` function to return the current value produced by the `cars` table's `car_id_seq` object:

```sql
SELECT currval(pg_get_serial_sequence('cars', 'car_id'));
```

**Output**

(_insert screenshot after completing the lab_)

### Using a `RETURNING` clause with an `INSERT` clause

We can use a `RETURNING car_id` clause with an `INSERT` clause if we want to get those values created by the sequence when we insert a new row into the table.

The below command is used to insert a new row in the `cars` table, and returns those records generated for the `car_id` column.

```sql
INSERT INTO cars(car_name, car_model)
VALUES('Jaguar', 'XK')
RETURNING car_id;
```

**Output**

`car_id` is returned as **3**.

(_insert screenshot after completing the lab_)

<blockquote>
Note: As we understood above, the <strong>sequence generator</strong> operation is not transaction-safe, which implies that each user will get a different value <strong>if two parallel database</strong> connections try to get the next value from the sequence.
The sequence number of that user will be idle, which will create a gap in the sequence if <strong>one user can roll back the transaction</strong>.
</blockquote>

## Example 2: `vegetables` table

### `CREATE`

Create a new table named `vegetables` using the `CREATE` command, in a database called `organization`, with the `veg_id` column as the `SERIAL` pseudo-type.

```sql
CREATE TABLE vegetables(
  veggie_id SERIAL PRIMARY KEY,
  veggie_name VARCHAR NOT NULL,
  veggie_seasons VARCHAR NOT NULL
);
```

**Output**

The `vegetables` table has been successfully created.

(_insert screenshot after completing the lab_)

### `INSERT`

Once the `vegetables` table has been generated, insert some values into it using the `INSERT` command, and omit the `veggies_id` column as shown in the below command:

#### Omitting the column name

```sql
INSERT INTO vegetables(veggie_name, veggie_seasons)
VALUES('Broccoli', 'Spring');
```

**Output**

The values have been inserted into the `vegetables` table successfully.

(_insert screenshot after completing the lab_)

#### Using the `DEFAULT` keyword with the column name

We can also use the `DEFAULT` keyword with the `veggie_id` column as shown in the following command:

```sql
INSERT INTO vegetables(veggie_id, veggie_name, veggie_seasons)
VALUES(DEFAULT, 'Sweet Potatoes', 'Winter');
```

**Output**

The values have been inserted into the `vegetables` table successfully.

(_insert screenshot after completing the lab_)

Add some more values to the `vegetables` table:

```sql
INSERT INTO vegetables
  (veggie_name, veggie_seasons)
VALUES
  ('Jalapeno Peppers', 'Fall'),
  ('Cucumbers', 'Summer'),
  ('Winter Squash', 'Winter'),
  ('Snow Peas', 'Spring'),
  ('Black Radish', 'All seasons'),
  ('Pumpkin', 'Fall');
```

**Output**

The values have been inserted into the `vegetables` table successfully.

(_insert screenshot after completing the lab_)

### `SELECT`

After creating and inserting the `vegetables` table's values, we will use the `SELECT` command to return all rows of the `vegetables` table:

```sql
SELECT *
FROM vegetables;
```

**Output**

After successfully implementing the above command, we will get the below output:

(_insert screenshot after completing the lab_)

## Overview

The PostgreSQL `SERIAL` pseudo-type is mostly used to create **automatic increases** of a column value for a particular table.
