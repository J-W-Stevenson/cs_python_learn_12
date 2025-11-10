# Python-SQL Connection

## **1. Connecting to MySQL using `mysql.connector`**

First, install the library if you haven’t already:

```bash
pip install mysql-connector-python
```

### **Example code:**

```python
import mysql.connector

# Establish connection
conn = mysql.connector.connect(
    host="localhost",        # The hostname of the database server (usually 'localhost' if local)
    user="your_username",    # Your database username
    password="your_password",# Your database password
    database="your_db_name", # Name of the database you want to connect to
    port=3306                # Port number (default MySQL port is 3306)
)

# Create a cursor object to execute SQL queries
cursor = conn.cursor()

# Example query
cursor.execute("SELECT DATABASE();")
result = cursor.fetchone()
print("Connected to database:", result[0])

# Close cursor and connection
cursor.close()
conn.close()
```

### **Explanation of parameters in `connect()`**

| Parameter  | Purpose                                                                                           |
| ---------- | ------------------------------------------------------------------------------------------------- |
| `host`     | The server address of your MySQL database. `"localhost"` means it is running on the same machine. |
| `user`     | Username to log into the database.                                                                |
| `password` | Password for that user.                                                                           |
| `database` | Optional. The name of the database you want to use immediately after connecting.                  |
| `port`     | Optional. Port number MySQL is listening on. Default is `3306`.                                   |

---

## **2. Connecting to MySQL using `pymysql`**

Install PyMySQL first:

```bash
pip install pymysql
```

### **Example code:**

```python
import pymysql

# Establish connection
conn = pymysql.connect(
    host="localhost",        # Database server hostname
    user="your_username",    # Database username
    password="your_password",# Database password
    database="your_db_name", # Name of the database to connect to
    port=3306,               # Port number (default is 3306)
    charset="utf8mb4"        # Optional: character encoding
)

# Create a cursor
cursor = conn.cursor()

# Execute query
cursor.execute("SELECT DATABASE();")
result = cursor.fetchone()
print("Connected to database:", result[0])

# Close connection
cursor.close()
conn.close()
```

**Note:** `pymysql.connect()` uses mostly the same parameters as `mysql.connector.connect()`.
The extra parameter `charset` specifies the encoding, useful if you store Unicode characters.

---

## **3. Connecting to SQLite (no server required)**

SQLite is file-based, so there’s no host or port.

```python
import sqlite3

# Connect to database file (creates the file if it doesn't exist)
conn = sqlite3.connect("my_database.db")

# Create cursor
cursor = conn.cursor()

# Example query
cursor.execute("CREATE TABLE IF NOT EXISTS users (id INTEGER PRIMARY KEY, name TEXT);")

# Commit changes and close connection
conn.commit()
cursor.close()
conn.close()
```

---

✅ **Summary**

* Use `mysql.connector` or `pymysql` for MySQL databases.
* Use `sqlite3` for lightweight, file-based databases.
* Always close your cursor and connection to avoid leaks.
* Use `.commit()` for write operations (`INSERT`, `UPDATE`, `DELETE`) in MySQL or SQLite.

---

## **1. Using `mysql.connector`**

```python
import mysql.connector
from mysql.connector import Error

try:
    conn = mysql.connector.connect(
        host="localhost",
        user="wrong_user",       # Intentional wrong username
        password="wrong_pass",   # Intentional wrong password
        database="test_db",
        port=3306
    )

    if conn.is_connected():
        print("Connected to MySQL database")
        cursor = conn.cursor()
        cursor.execute("SELECT DATABASE();")
        print("Database:", cursor.fetchone()[0])

except mysql.connector.Error as e:
    # Catch different MySQL-specific errors
    if e.errno == 1045:
        print("Authentication error: Check username or password.")
    elif e.errno == 1049:
        print("Database does not exist.")
    elif e.errno == 2003:
        print("Cannot connect to MySQL server. Check host/port.")
    else:
        print(f"Connection error: {e}")

finally:
    if 'conn' in locals() and conn.is_connected():
        conn.close()
        print("Connection closed")
```

### Key points:

* `mysql.connector.Error` is the base class for MySQL connection errors.
* `errno` gives the specific MySQL error code:

  * `1045` → Access denied (wrong username/password)
  * `1049` → Unknown database
  * `2003` → Can't connect to MySQL server
* `finally` ensures the connection is closed even if an error occurs.

---

## **2. Using `pymysql`**

```python
import pymysql

try:
    conn = pymysql.connect(
        host="localhost",
        user="wrong_user",
        password="wrong_pass",
        database="test_db",
        port=3306,
        charset="utf8mb4"
    )
    print("Connected to MySQL database")
    cursor = conn.cursor()
    cursor.execute("SELECT DATABASE();")
    print("Database:", cursor.fetchone()[0])

except pymysql.MySQLError as e:
    # e.args[0] contains the error code
    error_code = e.args[0]
    if error_code == 1045:
        print("Authentication error: Check username/password")
    elif error_code == 1049:
        print("Database does not exist")
    elif error_code == 2003:
        print("Cannot connect to MySQL server")
    else:
        print(f"Connection error: {e}")

finally:
    if 'conn' in locals() and conn.open:
        conn.close()
        print("Connection closed")
```

---

## **3. Using SQLite**

SQLite is file-based, so errors are usually related to file permissions or invalid SQL:

```python
import sqlite3

try:
    conn = sqlite3.connect("nonexistent_folder/mydb.db")
    cursor = conn.cursor()
    print("Connected to SQLite database")

except sqlite3.Error as e:
    print("SQLite error:", e)

finally:
    if 'conn' in locals():
        conn.close()
        print("Connection closed")
```

---

✅ **Summary of best practices for handling connection errors:**

1. Always use `try-except-finally` to handle errors and close connections.
2. Catch **library-specific exceptions** (`mysql.connector.Error`, `pymysql.MySQLError`, `sqlite3.Error`).
3. Use **error codes** (like `1045`) to handle specific cases (wrong password, missing database).
4. Always close connections in the `finally` block.

---



```python
# First, make sure you have the MySQL connector installed:
# pip install mysql-connector-python

import mysql.connector

# 1. Connect to the MySQL database
connection = mysql.connector.connect(
    host="localhost",      # Your MySQL server address
    user="your_username",  # Your MySQL username
    password="your_password",  # Your MySQL password
    database="your_database"   # Database name to connect to
)

# 2. Create a cursor object
cursor = connection.cursor()

# Explanation:
# cursor() is used to create a cursor object.
# A cursor allows you to execute SQL statements and fetch results.

# -------------------
# INSERT operation
# -------------------
insert_query = "INSERT INTO employees (name, position, salary) VALUES (%s, %s, %s)"
data_to_insert = ("Alice", "Developer", 75000)

cursor.execute(insert_query, data_to_insert)

# Explanation:
# execute() runs the SQL query provided. You can also pass parameters
# to safely insert data without SQL injection risk.

connection.commit()  # Save the changes to the database
# Explanation:
# commit() is required to make the changes permanent in the database.

print(f"{cursor.rowcount} record inserted.")

# -------------------
# UPDATE operation
# -------------------
update_query = "UPDATE employees SET salary = %s WHERE name = %s"
data_to_update = (80000, "Alice")

cursor.execute(update_query, data_to_update)
connection.commit()

print(f"{cursor.rowcount} record updated.")

# -------------------
# DELETE operation
# -------------------
delete_query = "DELETE FROM employees WHERE name = %s"
data_to_delete = ("Alice",)

cursor.execute(delete_query, data_to_delete)
connection.commit()

print(f"{cursor.rowcount} record deleted.")

# 3. Close the cursor and connection
cursor.close()
connection.close()
```

### Key Explanations:

1. **`cursor()`**

   * Creates a cursor object which is used to interact with the database.
   * Think of it as a “controller” that allows Python to send SQL commands to MySQL.

2. **`execute()`**

   * Executes a SQL statement (query or command) through the cursor.
   * You can use placeholders (`%s`) to safely pass parameters and avoid SQL injection.

3. **`commit()`**

   * Persists changes (like `INSERT`, `UPDATE`, `DELETE`) to the database.
   * Without `commit()`, changes may not be saved permanently.


```python
import mysql.connector

# 1. Connect to the MySQL database
connection = mysql.connector.connect(
    host="localhost",
    user="your_username",
    password="your_password",
    database="your_database"
)

# 2. Create a cursor object
cursor = connection.cursor()

# -------------------
# INSERT operation with user input
# -------------------
name = input("Enter employee name: ")
position = input("Enter employee position: ")
salary = float(input("Enter employee salary: "))

insert_query = "INSERT INTO employees (name, position, salary) VALUES (%s, %s, %s)"
data_to_insert = (name, position, salary)

cursor.execute(insert_query, data_to_insert)
connection.commit()
print(f"{cursor.rowcount} record inserted.")

# -------------------
# UPDATE operation with user input
# -------------------
update_name = input("Enter the name of the employee to update salary: ")
new_salary = float(input("Enter the new salary: "))

update_query = "UPDATE employees SET salary = %s WHERE name = %s"
data_to_update = (new_salary, update_name)

cursor.execute(update_query, data_to_update)
connection.commit()
print(f"{cursor.rowcount} record updated.")

# -------------------
# DELETE operation with user input
# -------------------
delete_name = input("Enter the name of the employee to delete: ")

delete_query = "DELETE FROM employees WHERE name = %s"
data_to_delete = (delete_name,)

cursor.execute(delete_query, data_to_delete)
connection.commit()
print(f"{cursor.rowcount} record deleted.")

# 3. Close the cursor and connection
cursor.close()
connection.close()
```

### Key Points:

1. **Parameterized Queries**:

   * `%s` placeholders are used in SQL queries, and values are passed as a tuple.
   * This prevents SQL injection even when taking input from users.

2. **Input Conversion**:

   * Convert salary input to `float` to match the database column type.

3. **Commit Changes**:

   * Every `INSERT`, `UPDATE`, or `DELETE` must be followed by `connection.commit()` to save changes.

---


```python
import mysql.connector
from mysql.connector import Error

try:
    # 1. Establish a connection to the MySQL database
    connection = mysql.connector.connect(
        host='localhost',        # Database host
        user='your_username',    # Your MySQL username
        password='your_password',# Your MySQL password
        database='your_database' # The database to use
    )

    if connection.is_connected():
        print("Connected to MySQL database")

        # 2. Create a cursor object
        cursor = connection.cursor()

        # 3. Define the SELECT query
        query = "SELECT id, name, email FROM users"  # Example table 'users'

        # 4. Execute the query
        cursor.execute(query)

        # 5. Use rowcount to get the number of rows retrieved
        print(f"Number of records fetched (rowcount): {cursor.rowcount}")

        # 6. Fetch one record
        one_record = cursor.fetchone()
        print("First record using fetchone():", one_record)

        # 7. Fetch all remaining records
        all_records = cursor.fetchall()
        print("Remaining records using fetchall():")
        for record in all_records:
            print(record)

except Error as e:
    print("Error while connecting to MySQL:", e)

finally:
    # 8. Close cursor and connection
    if 'cursor' in locals() and cursor:
        cursor.close()
    if 'connection' in locals() and connection.is_connected():
        connection.close()
        print("MySQL connection is closed")
```

### ✅ Key Notes:

1. **`cursor.execute(query)`**: Executes the SQL query.
2. **`cursor.rowcount`**: Returns the number of rows that the last `.execute()` produced (for `SELECT`, some connectors may return `-1` until you fetch the results).
3. **`fetchone()`**: Fetches the next row of a query result set. Returns `None` if no more rows are available.
4. **`fetchall()`**: Fetches all remaining rows of a query result set as a list of tuples.
5. Always close the cursor and connection to free resources.

---


```python
import mysql.connector
from mysql.connector import Error

try:
    # 1. Connect to MySQL database
    connection = mysql.connector.connect(
        host='localhost',
        user='your_username',
        password='your_password',
        database='your_database'
    )

    if connection.is_connected():
        print("Connected to MySQL database")

        # 2. Create a cursor
        cursor = connection.cursor()

        # 3. Execute SELECT query
        query = "SELECT id, name, email FROM users"
        cursor.execute(query)

        # 4. Fetch all rows
        rows = cursor.fetchall()

        print(f"Total records fetched: {cursor.rowcount}\n")

        # 5. Iterate and print each record in formatted style
        print("{:<5} {:<20} {:<30}".format("ID", "Name", "Email"))
        print("-" * 60)
        for row in rows:
            id, name, email = row
            print("{:<5} {:<20} {:<30}".format(id, name, email))

except Error as e:
    print("Error:", e)

finally:
    if 'cursor' in locals() and cursor:
        cursor.close()
    if 'connection' in locals() and connection.is_connected():
        connection.close()
        print("\nMySQL connection closed")
```

### ✅ What this does:

* Uses `fetchall()` to retrieve all rows at once.
* Iterates over each row (`row` is a tuple).
* Uses `str.format()` to align columns neatly.
* Displays a header row for clarity.

---


### Python Code:

```python
import mysql.connector
from mysql.connector import Error

# Function to create a database connection
def create_connection():
    try:
        connection = mysql.connector.connect(
            host='localhost',        # Replace with your host
            user='root',             # Replace with your username
            password='password',     # Replace with your password
            database='testdb'        # Replace with your database name
        )
        if connection.is_connected():
            return connection
    except Error as e:
        print(f"Error: {e}")
        return None

# Function to insert a new record
def insert_record(connection):
    cursor = connection.cursor()
    name = input("Enter name: ")
    age = input("Enter age: ")
    sql = "INSERT INTO users (name, age) VALUES (%s, %s)"
    values = (name, age)
    try:
        cursor.execute(sql, values)
        connection.commit()
        print("Record inserted successfully.")
    except Error as e:
        print(f"Error: {e}")

# Function to update an existing record
def update_record(connection):
    cursor = connection.cursor()
    user_id = input("Enter ID of record to update: ")
    new_name = input("Enter new name: ")
    new_age = input("Enter new age: ")
    sql = "UPDATE users SET name=%s, age=%s WHERE id=%s"
    values = (new_name, new_age, user_id)
    try:
        cursor.execute(sql, values)
        connection.commit()
        if cursor.rowcount:
            print("Record updated successfully.")
        else:
            print("Record not found.")
    except Error as e:
        print(f"Error: {e}")

# Function to delete a record
def delete_record(connection):
    cursor = connection.cursor()
    user_id = input("Enter ID of record to delete: ")
    sql = "DELETE FROM users WHERE id=%s"
    try:
        cursor.execute(sql, (user_id,))
        connection.commit()
        if cursor.rowcount:
            print("Record deleted successfully.")
        else:
            print("Record not found.")
    except Error as e:
        print(f"Error: {e}")

# Function to display all records
def display_records(connection):
    cursor = connection.cursor()
    sql = "SELECT * FROM users"
    try:
        cursor.execute(sql)
        rows = cursor.fetchall()
        if rows:
            print("\nID | Name | Age")
            print("-" * 20)
            for row in rows:
                print(f"{row[0]} | {row[1]} | {row[2]}")
        else:
            print("No records found.")
    except Error as e:
        print(f"Error: {e}")

# Main menu function
def menu():
    connection = create_connection()
    if not connection:
        print("Failed to connect to database.")
        return
    
    while True:
        print("\n--- MENU ---")
        print("1. Insert Record")
        print("2. Update Record")
        print("3. Delete Record")
        print("4. Display All Records")
        print("5. Exit")

        choice = input("Enter your choice: ")
        if choice == '1':
            insert_record(connection)
        elif choice == '2':
            update_record(connection)
        elif choice == '3':
            delete_record(connection)
        elif choice == '4':
            display_records(connection)
        elif choice == '5':
            print("Exiting...")
            break
        else:
            print("Invalid choice. Try again.")

    connection.close()

# Run the menu
if __name__ == "__main__":
    menu()
```

---

### Requirements:

1. MySQL server running with a database named `testdb`.
2. A table called `users`:

```sql
CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(255) NOT NULL,
    age INT NOT NULL
);
```

3. Install MySQL connector:

```bash
pip install mysql-connector-python
```

---



---

### Enhanced Python Application:

```python
import mysql.connector
from mysql.connector import Error

# Function to create a database connection
def create_connection():
    try:
        connection = mysql.connector.connect(
            host='localhost',       # Update with your host
            user='root',            # Update with your username
            password='password',    # Update with your password
            database='testdb'       # Update with your database
        )
        if connection.is_connected():
            print("Connected to the database successfully.")
            return connection
    except Error as e:
        print(f"Error connecting to database: {e}")
        return None

# Function to insert a new record
def insert_record(connection):
    cursor = connection.cursor()
    try:
        name = input("Enter name: ").strip()
        age = input("Enter age: ").strip()
        if not name or not age.isdigit():
            print("Invalid input. Name cannot be empty and age must be a number.")
            return
        
        sql = "INSERT INTO users (name, age) VALUES (%s, %s)"
        cursor.execute(sql, (name, int(age)))
        connection.commit()
        print(f"Record inserted successfully with ID {cursor.lastrowid}.")
    except Error as e:
        print(f"Failed to insert record: {e}")

# Function to update an existing record
def update_record(connection):
    cursor = connection.cursor()
    try:
        user_id = input("Enter ID of record to update: ").strip()
        if not user_id.isdigit():
            print("Invalid ID.")
            return
        
        new_name = input("Enter new name: ").strip()
        new_age = input("Enter new age: ").strip()
        if not new_name or not new_age.isdigit():
            print("Invalid input. Name cannot be empty and age must be a number.")
            return
        
        sql = "UPDATE users SET name=%s, age=%s WHERE id=%s"
        cursor.execute(sql, (new_name, int(new_age), int(user_id)))
        connection.commit()
        if cursor.rowcount:
            print("Record updated successfully.")
        else:
            print("No record found with the given ID.")
    except Error as e:
        print(f"Failed to update record: {e}")

# Function to delete a record
def delete_record(connection):
    cursor = connection.cursor()
    try:
        user_id = input("Enter ID of record to delete: ").strip()
        if not user_id.isdigit():
            print("Invalid ID.")
            return
        
        confirm = input(f"Are you sure you want to delete record ID {user_id}? (y/n): ").strip().lower()
        if confirm != 'y':
            print("Delete operation cancelled.")
            return
        
        sql = "DELETE FROM users WHERE id=%s"
        cursor.execute(sql, (int(user_id),))
        connection.commit()
        if cursor.rowcount:
            print("Record deleted successfully.")
        else:
            print("No record found with the given ID.")
    except Error as e:
        print(f"Failed to delete record: {e}")

# Function to display all records
def display_records(connection):
    cursor = connection.cursor()
    try:
        cursor.execute("SELECT * FROM users")
        rows = cursor.fetchall()
        if rows:
            print("\nID | Name | Age")
            print("-" * 20)
            for row in rows:
                print(f"{row[0]} | {row[1]} | {row[2]}")
        else:
            print("No records found.")
    except Error as e:
        print(f"Failed to fetch records: {e}")

# Main menu function
def menu():
    connection = create_connection()
    if not connection:
        return

    while True:
        print("\n--- MENU ---")
        print("1. Insert Record")
        print("2. Update Record")
        print("3. Delete Record")
        print("4. Display All Records")
        print("5. Exit")

        choice = input("Enter your choice: ").strip()
        if choice == '1':
            insert_record(connection)
        elif choice == '2':
            update_record(connection)
        elif choice == '3':
            delete_record(connection)
        elif choice == '4':
            display_records(connection)
        elif choice == '5':
            print("Exiting... Goodbye!")
            break
        else:
            print("Invalid choice. Please enter a number between 1 and 5.")

    if connection.is_connected():
        connection.close()
        print("Database connection closed.")

# Run the menu
if __name__ == "__main__":
    menu()
```

---

### ✅ Enhancements Made:

1. Added **confirmation after insert, update, and delete** operations.
2. Added **input validation** to prevent invalid entries.
3. Wrapped all database operations in `try/except` blocks for **robust exception handling**.
4. Graceful **database connection messages**.
5. Added a **delete confirmation prompt** to prevent accidental deletions.

---
Absolutely! Let’s go step by step. We’ll cover:

1. **Using `%s` with SQL queries in Python (parameterized queries)**
2. **Using the `format()` method for query strings**
3. **Why parameterized queries are safer than string concatenation**

---

## 1️⃣ Using `%s` in SQL Queries (Parameterized Queries)

When using a library like `psycopg2` (PostgreSQL) or `mysql-connector-python` (MySQL), you can safely insert variables into your SQL using **parameterized queries**. This helps prevent **SQL injection**, which is a major security risk if you concatenate strings.

### Example with `%s`:

```python
import psycopg2

# Connect to your database
conn = psycopg2.connect(
    host="localhost",
    database="testdb",
    user="postgres",
    password="password"
)
cur = conn.cursor()

# User input
user_id = 5

# Safe query using %s
query = "SELECT * FROM users WHERE id = %s"
cur.execute(query, (user_id,))  # Note: values must be passed as a tuple
result = cur.fetchall()

print(result)

cur.close()
conn.close()
```

✅ Key points:

* `%s` is a **placeholder** for variables.
* Actual values are passed separately as a tuple.
* The database driver safely escapes the values.

---

## 2️⃣ Using `format()` Method

You can also use Python’s string `format()` to build queries:

```python
user_id = 5
query = "SELECT * FROM users WHERE id = {}".format(user_id)
print(query)
```

This outputs:

```
SELECT * FROM users WHERE id = 5
```

⚠️ **Danger:** This approach is **not safe** if `user_id` comes from user input because it can lead to **SQL injection**:

```python
user_input = "1; DROP TABLE users;"  # malicious input
query = "SELECT * FROM users WHERE id = {}".format(user_input)
print(query)
# Output: SELECT * FROM users WHERE id = 1; DROP TABLE users;
```

Executing this would delete your table!

---

## 3️⃣ Why `%s` Parameterized Queries are Safer

* **Automatic escaping:** The database library handles escaping quotes, special characters, etc.
* **Prevents injection attacks:** Even if the input is malicious, it will be treated as a value, not executable SQL.

### Dangerous string concatenation example:

```python
user_input = "1 OR 1=1"
query = "SELECT * FROM users WHERE id = " + user_input
print(query)
# Output: SELECT * FROM users WHERE id = 1 OR 1=1
```

* This could return all users instead of one specific user.

### Safe parameterized version:

```python
query = "SELECT * FROM users WHERE id = %s"
cur.execute(query, (user_input,))
```

* The library treats `"1 OR 1=1"` as a literal string, not SQL code.
* No accidental table-wide queries or deletions.

---

### ✅ Summary Table

| Method               | Safety               | Example                                                        |
| -------------------- | -------------------- | -------------------------------------------------------------- |
| `%s` (parameterized) | Safe                 | `cur.execute("SELECT * FROM users WHERE id = %s", (user_id,))` |
| `format()`           | Unsafe if user input | `"SELECT * FROM users WHERE id = {}".format(user_id)`          |
| String concatenation | Unsafe               | `"SELECT * FROM users WHERE id=" + user_input`                 |

---



```python
# Import the MySQL connector module
import mysql.connector
from mysql.connector import Error

try:
    # 1. Connect to the MySQL database
    connection = mysql.connector.connect(
        host='localhost',      # Replace with your host, e.g., 'localhost'
        user='root',           # Replace with your MySQL username
        password='password',   # Replace with your MySQL password
        database='test_db'     # Replace with your database name
    )

    if connection.is_connected():
        print("Connected to MySQL database")

    # 2. Create a cursor object to execute SQL queries
    cursor = connection.cursor()

    # 3. Create a table if it doesn't exist
    create_table_query = """
    CREATE TABLE IF NOT EXISTS employees (
        id INT AUTO_INCREMENT PRIMARY KEY,
        name VARCHAR(50) NOT NULL,
        position VARCHAR(50),
        salary DECIMAL(10,2)
    )
    """
    cursor.execute(create_table_query)
    print("Table 'employees' is ready.")

    # 4. Insert some records into the table
    insert_query = """
    INSERT INTO employees (name, position, salary)
    VALUES (%s, %s, %s)
    """
    employees_data = [
        ("Alice", "Developer", 70000),
        ("Bob", "Designer", 65000),
        ("Charlie", "Manager", 90000)
    ]

    cursor.executemany(insert_query, employees_data)  # Insert multiple records
    connection.commit()  # Commit the transaction
    print(f"{cursor.rowcount} records inserted.")

    # 5. Update one record
    update_query = """
    UPDATE employees
    SET salary = %s
    WHERE name = %s
    """
    cursor.execute(update_query, (75000, "Alice"))
    connection.commit()
    print(f"{cursor.rowcount} record(s) updated.")

    # 6. Delete one record
    delete_query = """
    DELETE FROM employees
    WHERE name = %s
    """
    cursor.execute(delete_query, ("Bob",))
    connection.commit()
    print(f"{cursor.rowcount} record(s) deleted.")

    # 7. Fetch and display all records
    select_query = "SELECT * FROM employees"
    cursor.execute(select_query)
    records = cursor.fetchall()  # Fetch all records

    print("Current records in 'employees':")
    for row in records:
        print(row)

except Error as e:
    print("Error while connecting to MySQL:", e)

finally:
    # 8. Close cursor and connection
    if 'cursor' in locals() and cursor:
        cursor.close()
    if 'connection' in locals() and connection.is_connected():
        connection.close()
        print("MySQL connection closed.")
```

---

✅ **What this script does:**

1. Connects to a MySQL database.
2. Creates a table `employees` if it doesn’t exist.
3. Inserts multiple employee records.
4. Updates Alice's salary.
5. Deletes Bob’s record.
6. Fetches and prints all remaining records.
7. Closes the connection properly.

---

<!-- ------------------------------------------------------------------------------------------- -->






