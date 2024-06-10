# Exercises: PostgreSQL Left Join

### Exercise 1: Left Join

**Objective**: Perform a left join between `basket_a` and `basket_b` tables by matching the `fruit_a` and `fruit_b` columns.

**Task**: Use the `LEFT JOIN` to match the columns.

```sql
SELECT a, fruit_a, b, fruit_b
FROM basket_a
LEFT JOIN basket_b ON fruit_a = fruit_b;
```

### Exercise 2: Left Join with `WHERE` Clause

**Objective**: Select rows from `basket_a` that do not have matching rows in `basket_b`.

**Task**: Use the `LEFT JOIN` with a `WHERE` clause.

```sql
SELECT a, fruit_a, b, fruit_b
FROM basket_a
LEFT JOIN basket_b ON fruit_a = fruit_b
WHERE b IS NULL;
```
