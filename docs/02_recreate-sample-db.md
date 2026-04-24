# Re-create sample `dvdrental` database

### Create `dvdrental_dup` database

```sql
CREATE DATABASE dvdrental_dup
    WITH
    OWNER = postgres
    ENCODING = 'UTF-8'
    TABLESPACE = pg_default
    CONNECTION LIMIT = -1
    IS_TEMPLATE = False;
```

### Connect to the `dvdrental_dup` database

```bash
\c dvdrental_dup
```

![Connect to `dvdrental_dup` database](img/02_connect-to-dvdrental_dup-db.png)

## DDL execution order

Create **parent tables before child tables** (i.e., tables that are referenced by foreign keys must exist first).
Here's the correct order:

---

### Phase 1 – No dependencies (base tables)

1. `country`
2. `language`
3. `category`
4. `actor`

---

### Phase 2 – Depends on Phase 1

1. `city` `->` requires `country`
2. `film` `->` requires `language`

---

### Phase 3 – Depends on Phase 2

1. `address` `->` requires `city`
2. `film_actor` `->` requires `film`, `actor`
3. `film_category` `->` requires `film`, `category`

---

### Phase 4 – Depends on Phase 3

1. `customer` `->` requires `address`
2. `inventory` `->` requires `film`
3. `staff` `->` requires `address`

---

### Phase 5 – Depends on Phase 4

1. `store` `->` requires `staff`, `address`
2. `rental` `->` requires `inventory`, `customer` `staff`

---

### Phase 6 – Depends on Phase 5

1. `payment` `->` requires `customer`, `staff`, `rental`

---

> **Note**: `staff` and `store` have a **circular reference** risk – `staff.store_id` and `store.manager_staff_id` reference each other.
> The safest way to handle this is to create `staff` first (without the foreign key constraint on `store_id`), then create `store`, then add the constraint via `ALTER TABLE` afterward if needed.
