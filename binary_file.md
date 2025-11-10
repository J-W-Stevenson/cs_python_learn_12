
## 🧠 What is a Binary File?

A **binary file** stores data in **binary format (0s and 1s)**, unlike text files that store human-readable text.
Examples: images, videos, compiled programs, and even serialized Python objects.

---

## 🔹 1. Opening a Binary File

| Mode  | Description                                           |
| ----- | ----------------------------------------------------- |
| `rb`  | Read binary mode                                      |
| `rb+` | Read and write binary mode                            |
| `wb`  | Write binary mode (overwrites existing file)          |
| `wb+` | Read and write binary mode (overwrites existing file) |
| `ab`  | Append binary mode (adds data at end)                 |
| `ab+` | Read and append binary mode                           |

**Syntax:**

```python
file = open("data.bin", "wb")  # Open for writing in binary mode
# ... do operations ...
file.close()
```

---

## 🔹 2. Importing the `pickle` Module

`pickle` allows you to **serialize (dump)** and **deserialize (load)** Python objects to and from binary files.

```python
import pickle
```

---

## 🔹 3. Writing / Creating a Binary File

Use `pickle.dump(object, file)` to write data.

```python
import pickle

data = {"name": "Alice", "age": 25, "city": "Paris"}

with open("data.bin", "wb") as f:
    pickle.dump(data, f)

print("Data written successfully!")
```

This saves the dictionary `data` to a binary file `data.bin`.

---

## 🔹 4. Reading from a Binary File

Use `pickle.load(file)` to read data.

```python
import pickle

with open("data.bin", "rb") as f:
    data = pickle.load(f)

print("Data read from file:", data)
```

---

## 🔹 5. Appending to a Binary File

Appending requires care — because `pickle.dump()` doesn’t automatically separate objects.
To append multiple records, write them sequentially in `ab` mode:

```python
import pickle

student = {"name": "Bob", "age": 22}

with open("students.bin", "ab") as f:
    pickle.dump(student, f)
```

To read all appended objects:

```python
import pickle

students = []
with open("students.bin", "rb") as f:
    while True:
        try:
            students.append(pickle.load(f))
        except EOFError:
            break

print(students)
```

---

## 🔹 6. Searching in a Binary File

Example: search for a student by name.

```python
import pickle

name_to_search = "Bob"
found = False

with open("students.bin", "rb") as f:
    while True:
        try:
            student = pickle.load(f)
            if student["name"] == name_to_search:
                print("Record found:", student)
                found = True
                break
        except EOFError:
            break

if not found:
    print("Record not found.")
```

---

## 🔹 7. Updating a Record in a Binary File

We typically read all records, modify the required one, then rewrite the file.

```python
import pickle

students = []

# Step 1: Read all records
with open("students.bin", "rb") as f:
    while True:
        try:
            students.append(pickle.load(f))
        except EOFError:
            break

# Step 2: Update record
for student in students:
    if student["name"] == "Bob":
        student["age"] = 23

# Step 3: Rewrite the file
with open("students.bin", "wb") as f:
    for student in students:
        pickle.dump(student, f)

print("Record updated successfully!")
```

---

## 🔹 8. Closing a Binary File

If you use `with open(...)`, the file closes automatically.
Otherwise, use:

```python
file.close()
```

---

## ✅ Summary Table

| Operation      | Function / Method           | File Mode              |
| -------------- | --------------------------- | ---------------------- |
| Open file      | `open(filename, mode)`      | `rb`, `wb`, `ab`, etc. |
| Write / Create | `pickle.dump(obj, file)`    | `wb`, `ab`             |
| Read           | `pickle.load(file)`         | `rb`                   |
| Append         | `pickle.dump(obj, file)`    | `ab`                   |
| Search         | Loop + `pickle.load(file)`  | `rb`                   |
| Update         | Read all → modify → rewrite | `rb` + `wb`            |

---

Here’s a menu-driven example:

```python
import pickle
import os

FILENAME = "students.bin"

# Function to create/overwrite file with initial data
def create_file():
    students = []
    n = int(input("How many student records do you want to enter? "))
    for i in range(n):
        name = input(f"Enter name of student {i+1}: ")
        age = int(input(f"Enter age of student {i+1}: "))
        city = input(f"Enter city of student {i+1}: ")
        students.append({"name": name, "age": age, "city": city})
    
    with open(FILENAME, "wb") as f:
        for student in students:
            pickle.dump(student, f)
    print(f"{n} records saved successfully!\n")

# Function to read all records
def read_file():
    if not os.path.exists(FILENAME):
        print("File does not exist.\n")
        return
    print("Student Records:")
    with open(FILENAME, "rb") as f:
        while True:
            try:
                student = pickle.load(f)
                print(student)
            except EOFError:
                break
    print()

# Function to append a new record
def append_record():
    name = input("Enter name: ")
    age = int(input("Enter age: "))
    city = input("Enter city: ")
    student = {"name": name, "age": age, "city": city}
    
    with open(FILENAME, "ab") as f:
        pickle.dump(student, f)
    print("Record appended successfully!\n")

# Function to search for a record by name
def search_record():
    name_to_search = input("Enter name to search: ")
    found = False
    if not os.path.exists(FILENAME):
        print("File does not exist.\n")
        return

    with open(FILENAME, "rb") as f:
        while True:
            try:
                student = pickle.load(f)
                if student["name"].lower() == name_to_search.lower():
                    print("Record found:", student)
                    found = True
                    break
            except EOFError:
                break
    if not found:
        print("Record not found.\n")
    else:
        print()

# Function to update a record by name
def update_record():
    name_to_update = input("Enter name to update: ")
    updated = False
    students = []

    if not os.path.exists(FILENAME):
        print("File does not exist.\n")
        return

    # Read all records
    with open(FILENAME, "rb") as f:
        while True:
            try:
                students.append(pickle.load(f))
            except EOFError:
                break

    # Update record
    for student in students:
        if student["name"].lower() == name_to_update.lower():
            student["age"] = int(input("Enter new age: "))
            student["city"] = input("Enter new city: ")
            updated = True
            break

    # Rewrite file
    with open(FILENAME, "wb") as f:
        for student in students:
            pickle.dump(student, f)

    if updated:
        print("Record updated successfully!\n")
    else:
        print("Record not found.\n")

# Menu-driven program
def menu():
    while True:
        print("===== Student Binary File Menu =====")
        print("1. Create/Overwrite File")
        print("2. Read All Records")
        print("3. Append Record")
        print("4. Search Record")
        print("5. Update Record")
        print("6. Exit")
        choice = input("Enter your choice: ")

        if choice == "1":
            create_file()
        elif choice == "2":
            read_file()
        elif choice == "3":
            append_record()
        elif choice == "4":
            search_record()
        elif choice == "5":
            update_record()
        elif choice == "6":
            print("Exiting program. Goodbye!")
            break
        else:
            print("Invalid choice! Try again.\n")

if __name__ == "__main__":
    menu()
```

---

### ✅ Features of this Program:

1. **Create/overwrite** the binary file with multiple records.
2. **Read** all records from the binary file.
3. **Append** a new record at the end.
4. **Search** a record by name.
5. **Update** a record by name.
6. Uses **`pickle`** to serialize Python dictionaries.
7. Handles **file-not-found** situations gracefully.

---


