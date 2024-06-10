# Exercises: Full Outer Join

### Exercise 1: Full Outer Join

**Objective**: Perform a full outer join between `basket_a` and `basket_b` tables by matching the `fruit_a` and `fruit_b` columns.

**Task**: Use the `FULL OUTER JOIN` to match the columns.

```sql
SELECT a, fruit_a, b, fruit_b
FROM basket_a
FULL OUTER JOIN basket_b ON fruit_a = fruit_b;
```
