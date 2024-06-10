# Exercises: PostgreSQL Right Join

### Exercise 1: Right Join

**Objective**: Perform a right join between `basket_a` and `basket_b` tables by matching the `fruit_a` and `fruit_b` columns.

**Task**: Use the `RIGHT JOIN` to match the columns.

```sql
SELECT a, fruit_a, b, fruit_b
FROM basket_a
RIGHT JOIN basket_b ON fruit_a = fruit_b;
```

### Exercise 2: Right Join with `WHERE` Clause

**Objective**: Select rows from `basket_b` that do not have matching rows in `basket_a`.

**Task**: Use the `RIGHT JOIN` with a `WHERE` clause.

```sql
SELECT a, fruit_a, b, fruit_b
FROM basket_b
RIGHT JOIN basket_a ON fruit_a = fruit_b
WHERE a IS NULL;
```
