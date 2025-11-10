# Comma-separated values (CSV)
Comma-separated values (CSV) is a plain text data format for storing tabular data where the fields (values) 
of a record are separated by a comma and each record is a line (i.e. newline separated). 
CSV is commonly-used in software that generally deals with tabular data such as a database and a spreadsheet.
Benefits cited for using CSV include simplicity of use and human readability. 
CSV is a form of delimiter-separated values. 
A CSV file is a file that contains CSV-formatted data.

***The image of spreadsheet***
<img width="836" height="269" alt="image" src="https://github.com/user-attachments/assets/58ad0e05-42c1-4faf-a608-e8059f59d596" />
***Above image is the spreadsheet version of csv file whose data looks like:***
```
Username; Identifier;First name;Last name
booker12;9012;Rachel;Booker
grey07;2070;Laura;Grey
johnson81;4081;Craig;Johnson
jenkins46;9346;Mary;Jenkins
smith79;5079;Jamie;Smith

```
***Another example***
```
Name,Age,City
Alice,25,New York
Bob,30,London
Charlie,28,Paris
```

---

### ✅ **1. Import the `csv` module**

```python
import csv
```

---

### ✅ **2. Write into a CSV file**

You can use:

* `writer()` → to create a writer object
* `writerow()` → to write a single row
* `writerows()` → to write multiple rows

#### Example:

```python
import csv

# Data to write
header = ['Name', 'Age', 'City']
data = [
    ['Alice', 25, 'New York'],
    ['Bob', 30, 'London'],
    ['Charlie', 28, 'Paris']
]

# Open the CSV file for writing
with open('people.csv', 'w', newline='') as file:
    writer = csv.writer(file)

    # Write header
    writer.writerow(header)

    # Write multiple rows
    writer.writerows(data)

print("CSV file written successfully!")
```

**Explanation:**

* `'w'` → opens the file for writing (overwrites existing content).
* `newline=''` → prevents extra blank lines on Windows.
* `writerow()` → writes one list as one row.
* `writerows()` → writes multiple lists at once.

---

### ✅ **3. Read from a CSV file**

You can use:

* `reader()` → to create a reader object that iterates over rows.

#### Example:

```python
import csv

# Open the CSV file for reading
with open('people.csv', 'r') as file:
    reader = csv.reader(file)

    # Iterate through the rows
    for row in reader:
        print(row)
```

**Output:**

```
['Name', 'Age', 'City']
['Alice', '25', 'New York']
['Bob', '30', 'London']
['Charlie', '28', 'Paris']
```

---

### ✅ **4. Summary**

| Function                          | Purpose                 |
| --------------------------------- | ----------------------- |
| `csv.writer(file)`                | Creates a writer object |
| `writer.writerow(list)`           | Writes a single row     |
| `writer.writerows(list_of_lists)` | Writes multiple rows    |
| `csv.reader(file)`                | Reads data row-by-row   |

---






