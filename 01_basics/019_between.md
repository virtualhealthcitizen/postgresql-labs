# PostgreSQL `BETWEEN` operator

**Summary**: This section discusses how to use the PostgreSQL `BETWEEN` operator to match a value against a range of values.

## Introduction to the PostgreSQL `BETWEEN` operator

You use the `BETWEEN` operator to match a value against a range of values.
The following illustrates the syntax of the `BETWEEN` operator:

### Syntax of the `BETWEEN` Operator

```sql
value BETWEEN low AND high
```

If the `value` is greater than or equal to the `low` value and less than or equal to the `high` value, the expression returns true; otherwise, it returns false.

You can rewrite the `BETWEEN` operator by using the greater than or equal (`>=`) or less than or equal (`<=`) operators like this:

```sql
value >= low and value <= high
```

If you want to check if a value is out of range, you combine the `NOT` operator with the `BETWEEN` operator as follows:

```sql
value NOT BETWEEN low AND high
```

The following is equivalent to the expression that uses the `NOT` and `NETWEEN` operators:

```sql
value < low OR value > high
```

You often use the `BETWEEN` operator in the `WHERE` clause of a `SELECT`, `INSERT`, `UPDATE`, or `DELETE` statement.

## PostgreSQL `BETWEEN` operator examples

Let's take a look at the `payment` table in the sample database.

<img src="img/58.png" width="180" />

### Example 1: Using the `BETWEEB` Operator

The following query uses the `BETWEEN` operator to select payments whose amount is between **8** and **9** (USD):

```sql
SELECT
  customer_id,
  payment_id,
  amount
FROM
  payment
WHERE
  amount BETWEEN 8 AND 9;
```

<img src="img/59.png" width="250" />

### Example 2: Using the `NOT BETWEEN` Operator

To get payments whose amount is not in the range of **8** and **9**, you use the following query:

```sql
SELECT
  customer_id,
  payment_id,
  amount
FROM
  payment
WHERE
  amount NOT BETWEEN 8 AND 9;
```

<img src="img/60.png" width="275" />

### Example 3: Using the `BETWEEN` Operator with Dates

If you want to check a value against date ranges, you should use the literal date in ISO 8601 format, i.e., `YYYY-MM-DD`.
For example, to get the payment whose payment date is between `2007-02-07` and `2007-02-15`, you use the following query:

```sql
SELECT
  customer_id,
  payment_id,
  amount,
  payment_date
FROM
  payment
WHERE
  payment_date BETWEEN '2007-02-07' AND '2007-02-15';
```

<img src="img/61.png" width="400" />
