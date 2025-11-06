# Structured Query Language (SQL)
There are many
***RDBMS*** such as `MySQL`, `Microsoft SQL Server`,
`PostgreSQL`, `Oracle`, etc. that allow us to create
a database consisting of relations. These RDBMS
also allow us to store, retrieve and manipulate
data on that database through queries. In this
chapter, we will learn how to create, populate and
query databases using `MySQL`.

## Structured Query Language (SQL)

The Structured Query Language (SQL) is the most
popular query language used by major relational
database management systems such as `MySQL`,
`ORACLE`, `SQL Server`, etc.
## Data Types And Constraints In MySQL
Each attribute(column) has a data type
### Data type of Attribute
Data type of an attribute indicates the type of data value
that an attribute can have.<br> It also decides the operations
that can be performed on the data of that attribute.<br>
For example, arithmetic operations can be performed
on numeric data but not on character data.<br> Commonly
used data types in MySQL are numeric types, date and
time types, and string types.<br>

***Commonly used data types in MySQL***
| **Data Type**  | **Description**                                                                                                                                                                                                              |
| -------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **CHAR(n)**    | Specifies character type data of fixed length *n* (0–255). Declaring `CHAR(10)` reserves space for 10 characters. If the data is shorter (e.g., `'city'` has 4 characters), MySQL pads the remaining 6 spaces on the right.  |
| **VARCHAR(n)** | Specifies variable-length character data of length *n* (0–65535). Declaring `VARCHAR(30)` allows up to 30 characters, but storage depends on the actual string length (e.g., `'city'` occupies space for only 4 characters). |
| **INT**        | Specifies an integer value, occupying 4 bytes. The range for **unsigned** INT is 0 to 4,294,967,295. For larger values, `BIGINT` (8 bytes) should be used.                                                                   |
| **FLOAT**      | Holds numbers with decimal points. Each FLOAT value occupies 4 bytes of storage.                                                                                                                                             |
| **DATE**       | Used to store dates in `'YYYY-MM-DD'` format. The valid range is `'1000-01-01'` to `'9999-12-31'`.                                                                                                                           |

### Constraints
Constraints are the certain types of restrictions on the
data values that an attribute can have.<br>They
are used to ensure correctness of data.<br> However, it is
not mandatory to define constraints for each attribute
of a table.<br>


***Commonly used SQL Constraints***

| **Constraint**  | **Description**                                                                                                              |
| --------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| **NOT NULL**    | Ensures that a column cannot have `NULL` values, where `NULL` means missing, unknown, or not applicable data.                |
| **UNIQUE**      | Ensures that all the values in a column are distinct (no duplicates).                                                        |
| **DEFAULT**     | Specifies a default value for the column if no value is provided during data insertion.                                      |
| **PRIMARY KEY** | Identifies the column (or set of columns) that uniquely identifies each row/record in a table.                               |
| **FOREIGN KEY** | Refers to a column whose value matches the primary key in another table, establishing a relationship between the two tables. |

## SQL For Data Definition
In order to be able to store data we need to first define
the relation schema.<br> Defining a schema includes creating
a relation and giving name to a relation, identifying the
attributes in a relation, deciding upon the datatype for
each attribute and also specify the constraints as per
the requirements.<br> Sometimes, we may require to make
changes to the relation schema also.<br> SQL allows us to
write statements for defining, modifying and deleting
relation schemas.<br> These are part of Data Definition
Language (DDL).<br>

• The Create statement is used to create a database and its tables (relations). <br>
• Before creating a database, we should be
clear about the number of tables the database will have,
the columns (attributes) in each table along with the
data type of each column, and its constraint, if any.<br>


### CREATE Database
To create a database, we use the `CREATE DATABASE`
statement as shown in the following syntax:<br>
```
CREATE DATABASE databasename;
```
A DBMS can manage multiple databases on one
computer. Therefore, we need to select the database
that we want to use. To know the names of existing
databases, we use the statement `SHOW DATABASES`.<br>
```
USE databasename;
```
From the listed databases, we can select the database to
be used. Once the database is selected, we can proceed
with creating tables or querying data.<br>
In order to use the `databasename` database, the
following SQL statement is required.
```
USE databasename;
```
Initially, the created database is empty. It can be
checked by using the show tables statement that lists
names of all the tables within a database.
```
SHOW TABLES;
```
### CREATE Table
After creating a database `databasename`, we need to
define relations in this database and specify attributes
for each relation along with data type and constraint (if
any) for each attribute. This is done using the `CREATE TABLE` statement.
```
CREATE TABLE tablename(
attributename1 datatype constraint,
attributename2 datatype constraint,
:
:
:
attributenameN datatype constraint);
```
It is important to observe the following points with
respect to the **CREATE TABLE** statement:<br><br>
• The number of columns in a table defines the degree
of that relation, which is denoted by N.<br>
• Attribute name specifies the name of the column in
the table.<br>
• Datatype specifies the type of data that an attribute
can hold.<br>
• Constraint indicates the restrictions imposed on the
values of an attribute. By default, each attribute can
take NULL values except for the primary key.<br>


<!-- ---------------------------------------- Constrainst images go here ----------------------------------------- -->
![Attendance_constraints](https://github.com/user-attachments/assets/cd4e4278-641f-485d-829b-1d30306b43f9)
<p align="center"><b>Attendance_constraints</b></p>



![Gaurdian_constraint](https://github.com/user-attachments/assets/15df8c6e-3a4c-4d9e-b2ab-6dd3f8182dde)
<p align="center"><b>Gaurdian_constraint</b></p>



![Student_contraint](https://github.com/user-attachments/assets/936d130e-721d-4e0d-9631-02ead278e60e)
<p align="center"><b>Student_contraint</b></p>


***Example***
```
CREATE TABLE STUDENT(
RollNumber INT,
SName VARCHAR(20),
SDateofBirth DATE,
GUID CHAR (12),
PRIMARY KEY (RollNumber));
```

### Describe Table
We can view the structure of an already created table
using the `DESCRIBE` statement or `DESC` statement.

```
DESCRIBE tablename;
```
***NOTE: We can use the SHOW TABLES statement to see the tables in the particular database***

### ALTER Table
To change or alter the structure
(schema) of the table by using the alter statement.

#### (A) Add primary key to a relation
```
ALTER TABLE tablename ADD PRIMARY KEY (column_name);
```
#### (B) Add foreign key to a relation
Once primary keys are added, the next step is to add
foreign keys to the relation (if any). Following points need
to be observed while adding foreign key to a relation:<br>
• The referenced relation must be already created.<br>
• The referenced attribute(s) must be part of the
primary key of the referenced relation.<br>
• Data types and size of referenced and referencing
attributes must be the same.<br>
```
ALTER TABLE table_name ADD FOREIGN KEY(attribute
name) REFERENCES referenced_table_name
(attribute name);
```
Example:
```
ALTER TABLE STUDENT
ADD FOREIGN KEY(GUID) REFERENCES
GUARDIAN(GUID);
```
#### (C) Add constraint UNIQUE to an existing attribute
UNIQUE constraint means no two values in that
column should be the same.
```
ALTER TABLE table_name ADD UNIQUE (attribute
name);
```
#### (D) Add an attribute to an existing table
```
ALTER TABLE table_name ADD attribute
name DATATYPE;
```
#### (E) Modify datatype of an attribute
We can change data types of the existing attributes of a
table using the following ALTER statement.
```
ALTER TABLE table_name MODIFY attribute DATATYPE;
```
#### (F) Modify constraint of an attribute
When we create a table, by default each attribute takes
NULL value except for the attribute defined as primary
key. We can change an attribute’s constraint from NULL
to NOT NULL using an alter statement.
```
ALTER TABLE table_name MODIFY attribute DATATYPE
NOT NULL;
```
***Note:*** *We have to specify the data type of the attribute along with constraint NOT NULL while using **MODIFY**.*

#### (G) Add default value to an attribute
If we want to specify default value for an attribute, then
use the following syntax:
```
ALTER TABLE table_name MODIFY attribute DATATYPE
DEFAULT default_value;
```
***Note:*** *We have to specify the data type of the attribute along with **DEFAULT** while using **MODIFY**.*
#### (H) Remove an attribute
Using ALTER, we can remove attributes from a table, as
shown in the following syntax:
```
ALTER TABLE table_name DROP attribute;
```
#### (I) Remove primary key from the table
Sometime there may be a requirement to remove primary
key constraint from the table. In that case, Alter table
command can be used in the following way:
```
ALTER TABLE table_name DROP PRIMARY KEY;
```
***Note:*** We have dropped the primary key from the GUARDIAN table,
but each table should have a primary key to maintain uniqueness.
Hence, we have to use the **ADD** statement with the Alter Table
command to specify the primary key for the GUARDIAN table as
shown in earlier examples.
### DROP Statement
Sometimes a table in a database or the database itself
needs to be removed. We can use a DROP statement
to remove a database or a table permanently from the
system. However, one should be very cautious while
using this statement as it cannot be undone.
Syntax to drop a table:
```DROP TABLE table_name;```
Syntax to drop a database:
```DROP DATABASE database_name;```

Note: Using the DROP statement to remove a database will
ultimately remove all the tables within it.

### SQL for Data Manipulation
When we create a table,
only its structure is created but the table has no data.
To populate records in the table, `INSERT` statement is
used. Also, table records can be deleted or updated using
`DELETE` and `UPDATE` statements. These SQL statements
are part of ***Data Manipulation Language (DML)***.<br>

Data Manipulation using a database means either
insertion of new data, removal of existing data or
modification of existing data in the database.<br>
### INSERTION of Records
`INSERT INTO` statement is used to insert new records in
a table. Its syntax is:
```
INSERT INTO tablename
VALUES(value 1, value 2,....);
```

**Caution**: While populating records in a table with foreign
key, ensure that records in referenced tables are already
populated.<br>

If we want to insert values only for some of the
attributes in a table (supposing other attributes having
NULL or any other default value), then we shall specify
the attribute names in which the values are to be inserted
using the following syntax of INSERT INTO statement.
Syntax:
```
INSERT INTO tablename (column1, column2, ...)
VALUES (value1, value2, ...);
```
The values must be given in the same order in which
attributes are written in **INSERT** statement.
**Note**: Text and date values must be enclosed in ‘ ’ (single quotes).

### SQL for Data Query
SQL provides efficient mechanisms to retrieve data
stored in multiple tables in MySQL database (or any
other RDBMS). The SQL statement SELECT is used to
retrieve data from the tables in a database and is also
called a query statement.

#### SELECT Statement
The SQL statement SELECT is used to retrieve data
from the tables in a database and the output is also
displayed in tabular form.
```
SELECT attribute1, attribute2, ...
FROM table_name
WHERE condition;
```
##### (A) Retrieve selected columns
```
SELECT Column_name FROM Table_name;
```
##### (B) Renaming of columns
In case we want to rename any column while displaying
the output, it can be done by using the alias `AS`.
````
SELECT Column_name as c_n FROM Table_name;
````
```
SELECT Ename AS Name, Salary*12 AS 'Annual Income’ from Employee;
```
**Note: **Annual Income will not be added as a new column in the
database table. It is just for displaying the output of the query.
**If an aliased column name has space as in the case of Annual Income, it should be enclosed in quotes as 'Annual Income'.**
##### (C) Distinct Clause
The SELECT statement when combined with DISTINCT
clause, returns records without repetition (distinct
records).
```
SELECT DISTINCT Column_name FROM Table_name;
```
 ##### (D) WHERE Clause
The `WHERE` clause is used to retrieve data that meet
some specified conditions.

```
SELECT DISTINCT Column_Name1
FROM Table_name
WHERE Column_name2=value;
```
In the above example, = operator is used in the
WHERE clause. Other relational operators (`<`, `<=`, `>`, `>=`,
`!=`) can be used to specify such conditions. The logical
operators `AND`, `OR`, and `NOT` are used to combine
multiple conditions.

##### (E) Membership operator IN
The `IN` operator compares a value with a set of values
and returns true if the value belongs to that set. The
above query can be rewritten using `IN` operator as
shown below:
```
SELECT * FROM Table_name
WHERE Column_name1 IN (value1, value2 , value3);
```
```
SELECT * FROM Table_name
WHERE Column_name1 NOT IN (value1, value2 , value3);
```
##### (F) ORDER BY Clause
`ORDER BY` clause is used to display data in an ordered
form with respect to a specified column. By default,
`ORDER BY` displays records in ascending order of
the specified column’s values. To display the records
in descending order, the `DESC` (means descending)
keyword needs to be written with that column.

##### (G) Handling NULL Values
SQL supports a special value called `NULL` to represent
a missing or unknown value. NULL is used to represent
such unknown values. It is important to note that NULL
is different from 0 (zero). Also, any arithmetic operation
performed with NULL value gives NULL.
##### (H) Substring pattern matching
We cannot match such patterns using =
operator as we are not looking for an exact match.
SQL provides a `LIKE` operator that can be used with
the WHERE clause to search for a specified pattern in
a column.
The LIKE operator makes use of the following two
wild card characters:
• `%` (per cent)- used to represent zero, one, or multiple
characters.<br>
• `_` (underscore)- used to represent exactly a single
character.

```
SELECT * FROM EMPLOYEE
WHERE Ename like 'K%';
```
```
SELECT * FROM EMPLOYEE
WHERE Ename like '%a'
AND Salary > 45000;
```
```
SELECT * FROM EMPLOYEE
WHERE Ename like '_ANYA';
```
```
SELECT Ename FROM EMPLOYEE
WHERE Ename like '%se%';
```
```
SELECT EName FROM EMPLOYEE
WHERE Ename like '_a%';
```

## Data Update and Deletion
Updation and deletion of data are also part of SQL Data
Manipulation Language (DML).
### Data Updation
We may need to make changes in the value(s) of one or
more columns of existing records in a table. For example,
we may require some changes in address, phone number
or spelling of name, etc. The `UPDATE` statement is used
to make such modifications in existing data.
```
UPDATE table_name
SET attribute1 = value1, attribute2 = value2, ...
WHERE condition;
```
Here’s a more general version of your statement:

> **Caution:** Omitting the `WHERE` clause in an `UPDATE` statement can result in all records in the table being modified unintentionally.

### Data Deletion
`DELETE` statement is used to delete/remove one or
more records from a table.
```
DELETE FROM table_name
WHERE condition;
```
**Caution**: Like `UPDATE` statement, we need to be careful to include
the `WHERE` clause while using a `DELETE` statement to delete
records in a table. Otherwise, all the records in the table will get
deleted.

## Functions in SQL
A function is used to perform some
particular task and it returns zero or more values as a
result. Functions are useful while writing SQL queries
also. Functions can be applied to work on single or
multiple records (rows) of a table. Depending on their
application in one or multiple rows, SQL functions are
categorised as Single Row functions and Aggregate
functions.<br>
### Single Row Functions
These are also known as `Scalar functions`. Single row
functions are applied on a single value and return
a single value.<br>


<!-- ---------------- Single Row Fuction Image is here ---------------- -->
![single_row_function](https://github.com/user-attachments/assets/72d2540e-fcc5-465a-b9ae-2b9147589b5d)
<p align="center"><b>single_row_function</b></p>


`Math` Functions accept numeric value
as input and return a numeric value
as a result. `String` Functions accept
character value as input and return
either character or numeric values as
output. `Date and Time` functions accept
date and time value as input and return
numeric or string or Date and Time as output.<br>
#### (A) Math Functions
Three commonly used numeric functions are `POWER()`, `ROUND()` and `MOD()`.
***Math Functions***

| **Function**                                     | **Description**                                                                                                         | **Example**                                                          | **Output**        |
| ------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------- | ----------------- |
| **POWER(X, Y)**<br>*(also written as POW(X, Y))* | Calculates **X** raised to the power **Y**.                                                                             | `mysql> SELECT POWER(2, 3);`                                         | `8`               |
| **ROUND(N, D)**                                  | Rounds off number **N** to **D** number of decimal places.<br>**Note:** If D = 0, it rounds off to the nearest integer. | `mysql> SELECT ROUND(2912.564, 1);`<br>`mysql> SELECT ROUND(283.2);` | `2912.6`<br>`283` |
| **MOD(A, B)**                                    | Returns the **remainder** after dividing number **A** by number **B**.                                                  | `mysql> SELECT MOD(21, 2);`                                          | `1`               |

#### (B) String Functions
String functions can perform various operations on
alphanumeric data which are stored in a table. They
can be used to change the case (uppercase to lowercase
or vice-versa), extract a substring, calculate the length
of a string and so on.



***String Functions***

| **Function**                                                                                               | **Description**                                                                                                                                       | **Example**                                                                         | **Output**                 |   |   |                            |
| ---------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- | -------------------------- | - | - | -------------------------- |
| **UCASE(string)**<br>**OR**<br>**UPPER(string)**                                                           | Converts a string into **uppercase**.                                                                                                                 | `mysql> SELECT UCASE("Informatics Practices");`                                     | `INFORMATICS PRACTICES`    |   |   |                            |
| **LCASE(string)**<br>**OR**<br>**LOWER(string)**                                                           | Converts a string into **lowercase**.                                                                                                                 | `mysql> SELECT LOWER("Informatics Practices");`                                     | `informatics practices`    |   |   |                            |
| **MID(string, pos, n)**<br>**OR**<br>**SUBSTRING(string, pos, n)**<br>**OR**<br>**SUBSTR(string, pos, n)** | Returns a **substring** of length **n** starting from position **pos**. If **n** is not specified, returns substring from **pos** till end of string. | `mysql> SELECT MID("Informatics", 3, 4);`<br>`mysql> SELECT MID("Informatics", 7);` | `form`<br>`atics`          |   |   |                            |
| **LENGTH(string)**                                                                                         | Returns the **number of characters** in the string.                                                                                                   | `mysql> SELECT LENGTH("Informatics");`                                              | `11`                       |   |   |                            |
| **LEFT(string, N)**                                                                                        | Returns **N** characters from the **left** side of the string.                                                                                        | `mysql> SELECT LEFT("Computer", 4);`                                                | `Comp`                     |   |   |                            |
| **RIGHT(string, N)**                                                                                       | Returns **N** characters from the **right** side of the string.                                                                                       | `mysql> SELECT RIGHT("SCIENCE", 3);`                                                | `NCE`                      |   |   |                            |
| **INSTR(string, substring)**                                                                               | Returns the **position** of the first occurrence of the substring in the string. Returns **0** if substring not found.                                | `mysql> SELECT INSTR("Informatics", "ma");`                                         | `6`                        |   |   |                            |
| **LTRIM(string)**                                                                                          | Removes **leading spaces** from the string.                                                                                                           | `mysql> SELECT LENGTH("   DELHI"), LENGTH(LTRIM("   DELHI"));`                      | `+--------+--------+`<br>` | 7 | 5 | `<br>`+--------+--------+` |
| **RTRIM(string)**                                                                                          | Removes **trailing spaces** from the string.                                                                                                          | `mysql> SELECT LENGTH("PEN   "), LENGTH(RTRIM("PEN   "));`                          | `+--------+--------+`<br>` | 5 | 3 | `<br>`+--------+--------+` |
| **TRIM(string)**                                                                                           | Removes **both leading and trailing spaces** from the string.                                                                                         | `mysql> SELECT LENGTH("   MADAM   "), LENGTH(TRIM("   MADAM   "));`                 | `+--------+--------+`<br>` | 9 | 5 | `<br>`+--------+--------+` |



#### (C) Date and Time Functions
There are various functions that are used to perform
operations on date and time data. Some of the operations
include displaying the current date, extracting each
element of a date (day, month and year), displaying day
of the week and so on.

***Date Functions***

| **Function**        | **Description**                                                   | **Example**                              | **Output**            |
| ------------------- | ----------------------------------------------------------------- | ---------------------------------------- | --------------------- |
| **NOW()**           | Returns the **current system date and time**.                     | `mysql> SELECT NOW();`                   | `2019-07-11 19:41:17` |
| **DATE(datetime)**  | Returns only the **date part** from a given date/time expression. | `mysql> SELECT DATE(NOW());`             | `2019-07-11`          |
| **MONTH(date)**     | Returns the **month** (in numeric form) from the date.            | `mysql> SELECT MONTH(NOW());`            | `7`                   |
| **MONTHNAME(date)** | Returns the **month name** from the specified date.               | `mysql> SELECT MONTHNAME("2003-11-28");` | `November`            |
| **YEAR(date)**      | Returns the **year** from the date.                               | `mysql> SELECT YEAR("2003-10-03");`      | `2003`                |
| **DAY(date)**       | Returns the **day** (numeric) from the date.                      | `mysql> SELECT DAY("2003-03-24");`       | `24`                  |
| **DAYNAME(date)**   | Returns the **name of the day** from the date.                    | `mysql> SELECT DAYNAME("2019-07-11");`   | `Thursday`            |


### Aggregate Functions
Aggregate functions are also called Multiple Row
functions. These functions work on a set of records as
a whole and return a single value for each column of
the records on which the function is applied.
***Differences between Single and Multiple Row Functions***
| **Feature**      | **Single Row Function**                                                                                    | **Multiple Row Function**                     |
| ---------------- | ---------------------------------------------------------------------------------------------------------- | --------------------------------------------- |
| **Operation**    | Operates on **one row at a time**                                                                          | Operates on **groups of rows**                |
| **Result**       | Returns **one result per row**                                                                             | Returns **one result for a group** of rows    |
| **Usage in SQL** | Can be used in **SELECT**, **WHERE**, and **ORDER BY** clauses                                             | Can be used **only in SELECT** clause         |
| **Examples**     | **Math:** POWER(), ROUND(), MOD()<br>**String:** UCASE(), LOWER(), MID()<br>**Date:** NOW(), DATE(), DAY() | MAX(), MIN(), AVG(), SUM(), COUNT(), COUNT(*) |

***Aggregate Functions in SQL***
| **Function**      | **Description**                                                                                         | **Example**                                  | **Output**      |
| ----------------- | ------------------------------------------------------------------------------------------------------- | -------------------------------------------- | --------------- |
| **MAX(column)**   | Returns the **largest value** from the specified column.                                                | `mysql> SELECT MAX(Price) FROM INVENTORY;`   | `673112.00`     |
| **MIN(column)**   | Returns the **smallest value** from the specified column.                                               | `mysql> SELECT MIN(Price) FROM INVENTORY;`   | `355205.00`     |
| **AVG(column)**   | Returns the **average** of the values in the specified column.                                          | `mysql> SELECT AVG(Price) FROM INVENTORY;`   | `576091.625000` |
| **SUM(column)**   | Returns the **sum** of the values in the specified column.                                              | `mysql> SELECT SUM(Price) FROM INVENTORY;`   | `4608733.00`    |
| **COUNT(*)**      | Returns the **number of records** in a table. Can be combined with `WHERE` to count only matching rows. | `mysql> SELECT COUNT(*) FROM MANAGER;`       | `4`             |
| **COUNT(column)** | Returns the **number of non-NULL values** in a column.                                                  | `mysql> SELECT COUNT(MEMNAME) FROM MANAGER;` | `3`             |


### GROUP BY Clause in SQL
To fetch a group of rows on the basis
of common values in a column. This can be done using
a `group by` clause. It groups the rows together that
contains the same values in a specified column. We
can use the aggregate functions (COUNT, MAX, MIN,
AVG and SUM) to work on the grouped values. HAVING
Clause in SQL is used to specify conditions on the rows
with `Group By` clause.

```
SELECT column_name1, COUNT(*) AS column_name2
FROM table_name
GROUP BY column_name1;
```


## Operations on Relations

We can perform certain operations on relations like
Union, Intersection and Set Difference to merge the
tuples of two tables. These three operations are binary
operations as they work upon two tables. Note here that
these operations can only be applied if both the relations
have the same number of attributes and corresponding
attributes in both tables have the same domain.

###  UNION (∪)
This operation is used to combine the selected rows of
two tables at a time. If some rows are same in both
the tables, then result of the Union operation will
show those rows only once.
<!-- -----------------UNION image -------------------- -->
<p align="center">
  <img src="https://github.com/user-attachments/assets/336d2814-4cca-4dd8-87c4-0a928fb5c621" alt="Description" />
</p>


<p align="center"><b>Union</b></p>


### INTERSECT (∩)
Intersect operation is used to get the common tuples
from two tables and is represented by symbol ∩.
<!-- -----------------INTERSECT image -------------------- -->
<p align="center">
  <img src="https://github.com/user-attachments/assets/506cb17a-e703-4ac9-b09a-8b5769beba54" alt="Description" />
</p>

<p align="center"><b>Intersection</b></p>

### MINUS (-)
This operation is used to get tuples/rows which are
in the first table but not in the second table and the
operation is represented by the symbol - (minus).
<!-- -----------------MINUS image -------------------- -->
<p align="center">
  <img src="https://github.com/user-attachments/assets/bd7bc6f3-e6c4-40aa-9fa8-3475bf12bd57" alt="Description" />
</p>

<p align="center"><b>Minus</b></p>

### Cartesian Product (X)
Cartesian product operation combines tuples from
two relations. It results in all pairs of rows from the
two input relations, regardless of whether or not they
have the same values on common attributes. It is
denoted as ‘X’.<br>
The degree of the resulting relation is calculated
as the sum of the degrees of both the relations under
consideration. The cardinality of the resulting relation is
calculated as the product of the cardinality of relations
on which cartesian product is applied.<br>
✅ Columns: 3 + 2 = 5

✅ Rows: 3 × 2 = 6

Columns add up → degree

Rows multiply → cardinality

### Using Two Relations in a Query


```
SELECT * FROM DANCE, MUSIC;
```
```
SELECT * FROM DANCE D, MUSIC M WHERE
D.Name = M.Name;
```

### JOIN on two tables
JOIN operation combines tuples from two tables on
specified conditions. This is unlike cartesian product
which make all possible combinations of tuples. While
using the JOIN clause of SQL, we specify conditions on
the related attributes of two tables within the FROM
clause. Usually, such an attribute is the primary key
in one table and foreign key in another table.

```
SELECT *
FROM table_name1 t1, table_name2 t2
WHERE t1.column_name = t2.column_name;
```
