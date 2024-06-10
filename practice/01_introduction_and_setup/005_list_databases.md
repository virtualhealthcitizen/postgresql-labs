# Exercises: List Databases

### **List Databases Exercises**

#### **Exercise 1: Basic Listing**

1. **Objective:**
   List all the databases in your PostgreSQL instance.

   **Task:**
   In the `psql` console, execute the command to list all databases.
   ```shell
   \l
   ```
   **Expected Output:**
   You should see a list of all databases along with details such as database name, owner, encoding, collation, character type, and access privileges.

#### **Exercise 2: Extended Listing Command**

2. **Objective:**
   Use an alternative command to list all databases.

   **Task:**
   In the `psql` console, execute the command:
   ```shell
   \list
   ```
   **Expected Output:**
   The output should be the same as the previous exercise.

#### **Exercise 3: Using SQL Query to List Databases**

3. **Objective:**
   List all databases using an SQL query.

   **Task:**
   In the `psql` console or any PostgreSQL client, execute the following query:
   ```sql
   SELECT datname FROM pg_database;
   ```
   **Expected Output:**
   A list of database names.

#### **Exercise 4: Detailed Information Using SQL Query**

4. **Objective:**
   Retrieve detailed information about each database.

   **Task:**
   Execute the following SQL query:
   ```sql
   SELECT datname, datdba, encoding, datcollate, datctype, datistemplate, datallowconn, datconnlimit, datlastsysoid, datfrozenxid, datminmxid, dattablespace, datacl 
   FROM pg_database;
   ```
   **Expected Output:**
   Detailed information about each database, similar to what `\l` provides.

#### **Exercise 5: Filtering Databases**

5. **Objective:**
   Filter the list of databases based on specific criteria.

   **Task:**
   List all databases owned by the default PostgreSQL user (`postgres`):
   ```sql
   SELECT datname 
   FROM pg_database 
   WHERE datdba = (SELECT usesysid FROM pg_user WHERE usename = 'postgres');
   ```
   **Expected Output:**
   A list of databases owned by the user `postgres`.

#### **Exercise 6: Using pgAdmin to List Databases**

6. **Objective:**
   List databases using the pgAdmin graphical interface.

   **Task:**
    - Open pgAdmin and connect to your PostgreSQL server.
    - In the Browser pane, expand the server node to see the list of databases.

   **Expected Output:**
   A list of all databases displayed in the pgAdmin interface.

#### **Exercise 7: Practical Use Case - Verifying Database Creation**

7. **Objective:**
   Verify the creation of a new database.

   **Task:**
   Create a new database named `testdb`:
   ```sql
   CREATE DATABASE testdb;
   ```
   Then, list all databases to verify `testdb` has been created:
   ```shell
   \l
   ```

   **Expected Output:**
   `testdb` should appear in the list of databases.

#### **Exercise 8: Practical Use Case - Checking Access Privileges**

8. **Objective:**
   Review access privileges of the databases.

   **Task:**
   Execute the following command to list databases and review access privileges:
   ```shell
   \l+
   ```
   **Expected Output:**
   A detailed list of databases including access privileges.

---

These exercises cover listing databases using various methods and commands, filtering results, and practical scenarios for database management. Feel free to move on to the next module or let me know if you need further assistance with these exercises.
