# Exercises: Create a Table

### **Create a Table**

Creating tables in PostgreSQL involves defining the table structure with columns, data types, and constraints. Below is a detailed guide on creating tables.

#### **General Syntax**

The general syntax to create a table is as follows:

```sql
CREATE TABLE [IF NOT EXISTS] table_name (
  column1 datatype(length) column_constraint,
  column2 datatype(length) column_constraint,
  column3 datatype(length) column_constraint,
  table_constraints
);
```

#### **Example: Basic Table Creation**

Here’s an example of creating tables for a user accounts system:

```sql
CREATE TABLE accounts (
  user_id serial PRIMARY KEY,
  username VARCHAR (50) UNIQUE NOT NULL,
  password VARCHAR (50) NOT NULL,
  email VARCHAR (255) UNIQUE NOT NULL,
  created_on TIMESTAMP NOT NULL,
  last_login TIMESTAMP
);

CREATE TABLE roles (
  role_id serial PRIMARY KEY,
  role_name VARCHAR (255) UNIQUE NOT NULL
);

CREATE TABLE account_roles (
  user_id INT NOT NULL,
  role_id INT NOT NULL,
  grant_date TIMESTAMP,
  PRIMARY KEY (user_id, role_id),
  FOREIGN KEY (role_id)
  REFERENCES roles (role_id),
  FOREIGN KEY (user_id)
  REFERENCES accounts (user_id)
);
```

#### **DVD Rental Database Example**

To apply this to the DVD Rental database, let's create tables similar to those in the sample database.

1. **Creating the `actor` table:**
   ```sql
   CREATE TABLE IF NOT EXISTS actor (
     actor_id SERIAL PRIMARY KEY,
     first_name VARCHAR(45) NOT NULL,
     last_name VARCHAR(45) NOT NULL,
     last_update TIMESTAMP DEFAULT CURRENT_TIMESTAMP
   );
   ```

2. **Creating the `film` table:**
   ```sql
   CREATE TABLE IF NOT EXISTS film (
     film_id SERIAL PRIMARY KEY,
     title VARCHAR(255) NOT NULL,
     description TEXT,
     release_year YEAR,
     language_id SMALLINT NOT NULL,
     rental_duration SMALLINT NOT NULL DEFAULT 3,
     rental_rate NUMERIC(4,2) NOT NULL DEFAULT 4.99,
     length SMALLINT,
     replacement_cost NUMERIC(5,2) NOT NULL DEFAULT 19.99,
     rating VARCHAR(10) DEFAULT 'G',
     last_update TIMESTAMP DEFAULT CURRENT_TIMESTAMP
   );
   ```

3. **Creating the `film_actor` table:**
   ```sql
   CREATE TABLE IF NOT EXISTS film_actor (
     actor_id INT NOT NULL,
     film_id INT NOT NULL,
     last_update TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
     PRIMARY KEY (actor_id, film_id),
     FOREIGN KEY (actor_id) REFERENCES actor (actor_id),
     FOREIGN KEY (film_id) REFERENCES film (film_id)
   );
   ```

### **Column Constraints**

Column constraints are rules applied to the columns of a table to enforce data integrity.

- **NOT NULL**: Ensures that values in a column cannot be `NULL`.
- **UNIQUE**: Ensures the values in a column are unique across the rows within the same table.
- **PRIMARY KEY**: A primary key column uniquely identifies rows in a table. A table can have only one primary key. The primary key constraint allows you to define the primary key of a table.
- **CHECK**: A `CHECK` constraint ensures the data must satisfy a boolean expression.
- **FOREIGN KEY**: Ensures values in a column or a group of columns from a table exist in a column or group of columns in another table. Unlike the primary key, a table can have many foreign keys.

### **Exercises**

#### **Exercise 1: Basic Table Creation**

1. **Objective:**
   Create a simple table for storing customer data.

   **Task:**
   Create a table named `customers` with the following columns:
    - `customer_id` (serial, primary key)
    - `first_name` (VARCHAR(45), not null)
    - `last_name` (VARCHAR(45), not null)
    - `email` (VARCHAR(255), unique, not null)
    - `created_on` (TIMESTAMP, not null, default current timestamp)

   **Expected Result:**
   ```sql
   CREATE TABLE customers (
     customer_id SERIAL PRIMARY KEY,
     first_name VARCHAR(45) NOT NULL,
     last_name VARCHAR(45) NOT NULL,
     email VARCHAR(255) UNIQUE NOT NULL,
     created_on TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP
   );
   ```

#### **Exercise 2: Creating a Table with Foreign Key**

2. **Objective:**
   Create a table with a foreign key constraint.

   **Task:**
   Create a table named `orders` with the following columns:
    - `order_id` (serial, primary key)
    - `customer_id` (int, not null)
    - `order_date` (TIMESTAMP, not null, default current timestamp)
    - `status` (VARCHAR(20), not null)

   Ensure `customer_id` references `customer_id` in the `customers` table.

   **Expected Result:**
   ```sql
   CREATE TABLE orders (
     order_id SERIAL PRIMARY KEY,
     customer_id INT NOT NULL,
     order_date TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
     status VARCHAR(20) NOT NULL,
     FOREIGN KEY (customer_id) REFERENCES customers (customer_id)
   );
   ```

#### **Exercise 3: Using Column Constraints**

3. **Objective:**
   Create a table with various column constraints.

   **Task:**
   Create a table named `products` with the following columns:
    - `product_id` (serial, primary key)
    - `product_name` (VARCHAR(255), unique, not null)
    - `price` (NUMERIC(10,2), check(price > 0))
    - `created_on` (TIMESTAMP, not null, default current timestamp)

   **Expected Result:**
   ```sql
   CREATE TABLE products (
     product_id SERIAL PRIMARY KEY,
     product_name VARCHAR(255) UNIQUE NOT NULL,
     price NUMERIC(10,2) CHECK (price > 0),
     created_on TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP
   );
   ```

#### **Exercise 4: Creating a Join Table**

4. **Objective:**
   Create a join table to establish a many-to-many relationship.

   **Task:**
   Create a join table named `order_products` with the following columns:
    - `order_id` (int, not null)
    - `product_id` (int, not null)
    - `quantity` (int, not null)
    - `PRIMARY KEY (order_id, product_id)`

   Ensure `order_id` references `order_id` in the `orders` table and `product_id` references `product_id` in the `products` table.

   **Expected Result:**
   ```sql
   CREATE TABLE order_products (
     order_id INT NOT NULL,
     product_id INT NOT NULL,
     quantity INT NOT NULL,
     PRIMARY KEY (order_id, product_id),
     FOREIGN KEY (order_id) REFERENCES orders (order_id),
     FOREIGN KEY (product_id) REFERENCES products (product_id)
   );
   ```

### **Summary**

Creating tables in PostgreSQL involves specifying the table structure with appropriate data types and constraints to ensure data integrity. By practicing creating tables with different constraints and relationships, you can gain a deeper understanding of database design and management.
