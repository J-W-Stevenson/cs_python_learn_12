
---

# ✅ Step 1 — Make sure MySQL is installed

If you haven't installed MySQL, download it here:

👉 *Search for “MySQL Community Server download”*
(Installer includes MySQL Server + Workbench)

Install it normally and remember your **root** password.

---

# ✅ Step 2 — If MySQL is installed, locate the `bin` folder

On Windows, MySQL is usually installed in:

```
C:\Program Files\MySQL\MySQL Server 8.0\bin
```

or sometimes:

```
C:\Program Files (x86)\MySQL\MySQL Server 8.0\bin
```

Inside this folder, you should see files like:

* mysql.exe
* mysqld.exe
* mysqladmin.exe

If you see `mysql.exe`, you're in the right place.

---

# ✅ Step 3 — Add MySQL to your PATH

### 1. Open **Environment Variables**

* Press **Windows Key**
* Search **"Environment Variables"**
* Open: **Edit the system environment variables**
* Click **Environment Variables**

### 2. Edit the PATH

* Under **System variables**, find **Path**
* Select **Edit**
* Click **New**
* Paste the MySQL `bin` directory path, for example:

```
C:\Program Files\MySQL\MySQL Server 8.0\bin
```

### 3. Save everything and restart your terminal/VS Code.

---

# ✅ Step 4 — Test the command

Open a new command prompt and run:

```bash
mysql --version
```

If it works, you can now run:

```bash
mysql -u root -p
```

---

# 📌 QUICK FIX (without PATH)

If you don’t want to modify PATH, you can still run MySQL from CMD using the full path:

```bash
"C:\Program Files\MySQL\MySQL Server 8.0\bin\mysql.exe" -u root -p
```

---
## **Check if the MySQL Server is NOT running** on your computer



---

# ✅ Step 1 — Check if MySQL Server is installed

MySQL Server and MySQL Workbench are *different things*.
Make sure **MySQL Server** is installed (not just Workbench).

---

# ✅ Step 2 — Start MySQL Server (Windows)

### Option A — Start using Services

1. Press **Win + R**
2. Type: `services.msc`
3. Look for:

* **MySQL80**
* or **MySQL57**
* or **MySQL** (depends on version)

4. Right-click → **Start**

If it is already running, restart it.

---

### Option B — Start using Command Prompt (as Administrator)

Run:

```bash
net start MySQL80
```

If your service has a different name:

```bash
net start MySQL57
```

If you don’t know the service name, list all services:

```bash
sc query type= service state= all | find "MYSQL"
```

---

# ❗ If you get “service not found”

Then MySQL Server is **not installed**, or it failed to install.

Install (or reinstall) MySQL Server:

Search for → **MySQL Community Server download**

Install using the MySQL Installer and make sure:

✔ MySQL Server
✔ MySQL Workbench

are both selected.

---

# ✅ Step 3 — Validate server is listening on port 3306

Run:

```bash
netstat -ano | find "3306"
```

* If nothing appears → MySQL isn’t running.
* If you see a row → MySQL is running.

---

# 📌 Common Causes of Error 10061

| Cause                              | Meaning               |
| ---------------------------------- | --------------------- |
| MySQL Server is not running        | **Most common**       |
| Wrong port                         | Default is 3306       |
| Service failed to install          | MySQL installer issue |
| Another program is using port 3306 | Need to change port   |

---

# 🎯 Summary Fix

1. Open **services.msc**
2. Start **MySQL80** service
3. Run again:

```bash
mysql -u root -p
```

---

## **if MySQL Server *is* installed**.
Now we just need to make sure it’s running properly.

---

# ✅ Step 1 — Check the MySQL80 service status

In **services.msc**, look at **MySQL80**:

### ✔️ If the status is **Running**

Then MySQL is running, and you should be able to connect:

```bash
mysql -u root -p
```

If you still get the error, tell me.

---

### ❌ If the status is **Stopped**

Right-click **MySQL80** → **Start**.

👉 If it starts successfully, try connecting again:

```bash
mysql -u root -p
```

---

### ⚠️ If it **fails to start**

This is very common when MySQL’s config is corrupted or the data directory is wrong.

If it fails, you should see an error popup OR the service starts and immediately stops.

Please tell me what happens when you click **Start**:

* Does it **start successfully?**
* Does it **stop immediately?**
* Do you get an **error message?**

---

# ✅ Step 2 — Try starting it from Command Prompt

Run CMD **as Administrator** and type:

```bash
net start MySQL80
```

Tell me what message you get:

* **The MySQL80 service was started successfully.**
* **The service is not responding.**
* **The service could not be started due to...**

---

# 📌 If MySQL starts successfully

Then try connecting again:

```bash
mysql -u root -p
```

---

# 📌 If MySQL fails to start

We may need to check the error log located at:

```
C:\ProgramData\MySQL\MySQL Server 8.0\Data\DESKTOP-xxxx.err
```

## If it shows something like 
```
Your MySQL connection id is 10
Server version: 8.0.44 MySQL Community Server - GPL
Copyright (c) 2000, 2025, Oracle and/or its affiliates.
Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.                                                                                                                                                                                                                                         Type 'help;' or '\h' for help. Type '\c' to clear the current input statement. 
```



## To create another MySQL user (besides **root**) and give them access to a database, follow these steps.

---

# ✅ Step 1: Log into MySQL as root

Open your terminal or command prompt:

```bash
mysql -u root -p
```

Enter your root password.

---

# ✅ Step 2: Create a new database (if you don't already have one)

```sql
CREATE DATABASE mydatabase;
```

---

# ✅ Step 3: Create a new user

Replace `newuser` and `newpassword` with your desired username and password.

```sql
CREATE USER 'newuser'@'localhost' IDENTIFIED BY 'newpassword';
```

---

# ✅ Step 4: Give the user permission to the database

```sql
GRANT ALL PRIVILEGES ON mydatabase.* TO 'newuser'@'localhost';
```

If you want the user to access **all** databases (not recommended):

```sql
GRANT ALL PRIVILEGES ON *.* TO 'newuser'@'localhost' WITH GRANT OPTION;
```

---

# ✅ Step 5: Save changes

```sql
FLUSH PRIVILEGES;
```

---

# 🎉 Done!

Your new user is now created and can connect from your Python script:

```python
conn = mysql.connector.connect(
    host="localhost",
    user="newuser",
    password="newpassword",
    database="mydatabase",
    port=3306
)
```

---
## Try this in python 
```

import mysql.connector

# Connect using root (no database selected yet)
conn = mysql.connector.connect(
    host="localhost",
    user="newuser",
    password="newpassword",
    database="mydatabase",
    port=3306
)

cursor = conn.cursor()

# 1. Create a new database
# cursor.execute("CREATE DATABASE IF NOT EXISTS mydatabase;")
# print("Database created or already exists.")

# 2. Select the database
cursor.execute("USE mydatabase;")

# 3. Create a table
cursor.execute("""
CREATE TABLE IF NOT EXISTS users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100),
    email VARCHAR(100)
);
""")
print("Table created or already exists.")

# 4. Insert data
cursor.execute("""
INSERT INTO users (name, email)
VALUES ('Alice', 'alice@example.com'),
       ('Bob', 'bob@example.com');
""")
conn.commit()
print("Data inserted.")

# 5. Read the data back
cursor.execute("SELECT * FROM users;")
rows = cursor.fetchall()

print("Data in table:")
for row in rows:
    print(row)

# Close connections
cursor.close()
conn.close()
```

