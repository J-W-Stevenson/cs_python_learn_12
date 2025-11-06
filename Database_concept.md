# Database  Concept
## File System
A file can be understood as a container to store data in
a computer.<br> Files can be stored on the storage device
of a computer system.<br> Contents of a file can be texts,
computer program code, comma separated values
(CSV), etc.<br> Likewise, pictures, audios/videos, web pages
are also files.<br>
### Limitations of a File System
File system becomes difficult to handle when number of
files increases and volume of data also grows. Following
are some of the limitations of file system:<br>
#### (A) Difficulty in Access
Files themselves do not provide any mechanism to
retrieve data. Data maintained in a file system are
accessed through application programs.
#### (B) Data Redundancy
Redundancy means same data are duplicated in
different places (files).<br>Redundancy leads to excess storage use and may
cause data inconsistency also.
#### (C) Data Inconsistency
Data inconsistency occurs when same data maintained
in different places do not match.
#### (D) Data Isolation
Most of the time data are not linked together.
#### (E) Data Dependence
Data are stored in a specific format or structure in a file.
If the structure or format itself is changed, all the existing
application programs accessing that file also need to
be changed. Otherwise, the programs may not work
correctly. This is **data dependency**.
#### (F) Controlled Data Sharing
Not every user must see all the data. There must be a Authentication and Authorization check before access to data.
## Database Management System
Limitations faced in file system can be overcome by
storing the data in a database where data are logically
related. We can organise related data in a database so
that it can be managed in an efficient and easy way.<br>
A ***database management system (DBMS)*** or **database system** in short, is a software that can be used to
create and manage databases. DBMS lets users to
create a database, store, manage, update/modify and
retrieve data from that database by users or application
programs. Some examples of open source and
commercial DBMS include `MySQL`, `Oracle`, `PostgreSQL`,
`SQL Server`, `Microsoft Access`, `MongoDB`.<br>
A database system hides certain details about
how data are actually stored and maintained. Thus,
it provides users with an abstract view of the data. A
database system has a set of programs through which
users or other programs can access, modify and retrieve
the stored data.<br>
The DBMS serves as an interface between the
database and end users or application programs.
Retrieving data from a database through special type of
commands is called querying the database. In addition,
users can modify the structure of the database itself
through a DBMS.<br>

**Use of Database in Real-life Applications**
| **Application Name**                             | **Main Entities (Tables)** | **Key Fields / Attributes**                                                                         | **Purpose / Description**                      |
| ------------------------------------------------ | -------------------------- | --------------------------------------------------------------------------------------------------- | ---------------------------------------------- |
| **Banking System**                               | **Customer**               | Customer_ID (PK), Name, DOB, Address, Contact_No, Email                                             | Stores basic details of all banking customers. |
|                                                  | **Account**                | Account_No (PK), Customer_ID (FK), Account_Type, Balance, Open_Date, Branch_Code                    | Manages customer account information.          |
|                                                  | **Loan**                   | Loan_ID (PK), Customer_ID (FK), Loan_Type, Loan_Amount, Interest_Rate, Start_Date, End_Date, Status | Stores data about all customer loans.          |
|                                                  | **Transaction**            | Transaction_ID (PK), Account_No (FK), Date, Type (Credit/Debit), Amount, Description                | Tracks all account transactions.               |
|                                                  | **Branch**                 | Branch_Code (PK), Branch_Name, Location, Manager_ID                                                 | Stores details of bank branches.               |
| **Crop Loan / Kisan Credit Card**                | **Farmer**                 | Farmer_ID (PK), Name, Address, Contact_No, Aadhar_No                                                | Contains farmer’s personal data.               |
|                                                  | **Land**                   | Land_ID (PK), Farmer_ID (FK), Survey_No, Area, Location, Crop_Type                                  | Stores land and cultivation information.       |
|                                                  | **Crop_Loan**              | Loan_ID (PK), Farmer_ID (FK), Loan_Amount, Issue_Date, Due_Date, Interest_Rate                      | Maintains crop loan information.               |
|                                                  | **Repayment**              | Repayment_ID (PK), Loan_ID (FK), Payment_Date, Amount_Paid, Balance_Due                             | Records repayment history for loans.           |
| **Inventory Management**                         | **Product**                | Product_ID (PK), Name, Category, Price, Quantity, Supplier_ID                                       | Stores product details and stock information.  |
|                                                  | **Customer**               | Customer_ID (PK), Name, Address, Contact_No, Email                                                  | Holds customer data.                           |
|                                                  | **Order**                  | Order_ID (PK), Customer_ID (FK), Order_Date, Total_Amount, Status                                   | Tracks customer orders.                        |
|                                                  | **Order_Item**             | Order_Item_ID (PK), Order_ID (FK), Product_ID (FK), Quantity, Unit_Price                            | Lists products included in each order.         |
|                                                  | **Delivery**               | Delivery_ID (PK), Order_ID (FK), Delivery_Date, Delivery_Status, Courier_Name                       | Tracks order delivery information.             |
| **Organisation Resource Management (HR System)** | **Employee**               | Emp_ID (PK), Name, DOB, Address, Contact_No, Email, Dept_ID (FK), Branch_ID (FK)                    | Manages employee records.                      |
|                                                  | **Department**             | Dept_ID (PK), Dept_Name, Manager_ID                                                                 | Stores department details.                     |
|                                                  | **Salary**                 | Salary_ID (PK), Emp_ID (FK), Basic_Pay, Allowances, Deductions, Net_Salary, Pay_Date                | Maintains salary payment data.                 |
|                                                  | **Branch**                 | Branch_ID (PK), Branch_Name, Location, Manager_ID                                                   | Holds organization branch details.             |
| **Online Shopping System**                       | **User**                   | User_ID (PK), Username, Password_Hash, Email, Contact_No, Address                                   | Manages user login details.                    |
|                                                  | **Item**                   | Item_ID (PK), Item_Name, Description, Category, Price, Stock_Quantity                               | Describes available items.                     |
|                                                  | **User_Preference**        | Preference_ID (PK), User_ID (FK), Category, Keywords                                                | Stores user preferences for recommendations.   |
|                                                  | **Cart**                   | Cart_ID (PK), User_ID (FK), Created_Date                                                            | Represents user’s shopping cart.               |
|                                                  | **Cart_Item**              | Cart_Item_ID (PK), Cart_ID (FK), Item_ID (FK), Quantity                                             | Links items to the user’s cart.                |
|                                                  | **Order**                  | Order_ID (PK), User_ID (FK), Order_Date, Total_Amount, Status, Payment_Mode                         | Maintains user order information.              |
                              |


### Key Concepts in DBMS
In order to efficiently manage data using a DBMS, let us
understand certain key terms:<br>
#### (A) Database Schema
Database Schema is the design of a database.<br> It is the
skeleton of the database that represents the structure
(table names and their fields/columns), the type of data
each column can hold, constraints on the data to be
stored (if any), and the relationships among the tables.<br>
Database schema is also called the visual or logical
architecture as it tells us how the data are organised in
a database.<br>
#### (B) Data Constraint
Sometimes we put certain restrictions or limitations on
the type of data that can be inserted in one or more
columns of a table.<br> This is done by specifying one or
more constraints on that column(s) while creating the
tables.<br> For example, one can define the constraint that
the column mobile number can only have non-negative
integer values of exactly 10 digits.<br> Since each student
shall have one unique roll number, we can put the NOT
NULL and UNIQUE constraints on the RollNumber
column.<br> Constraints are used to ensure accuracy and
reliability of data in the database.<br>
#### (C) Meta-data or Data Dictionary
The database schema along with various constraints on
the data is stored by DBMS in a database catalog or
dictionary, called meta-data. A meta-data is data about
the data.
#### (D) Database Instance
When we define database structure or schema, state
of database is empty i.e. no data entry is there. After
loading data, the state or snapshot of the database
at any given time is the database instance. We may
then retrieve data through queries or manipulate data 
through updation, modification or deletion. Thus, the
state of database can change, and thus a database
schema can have many instances at different times.
#### (E) Query
A query is a request to a database for obtaining
information in a desired way.<br> Query can be made to get
data from one table or from a combination of tables.<br> To retrieve or manipulate data, the user needs to write
query using a query language called.
#### (F) Data Manipulation
Modification of database consists of three operations
viz. Insertion, Deletion or Update.
#### (G) Database Engine
Database engine is the underlying component or set of
programs used by a DBMS to create database and handle
various queries for data retrieval and manipulation.

#### Limitations of DBMS
##### Increased Complexity:
Use of DBMS
increases the
complexity of
maintaining
functionalities like
security, consistency,
sharing and integrity
##### Increased data vulnerability:
As data are stored
centrally, it increases
the chances of loss
of data due to any
failure of hardware or
software. It can bring
all operations to a halt
for all the users.


### DBMS Data Models
Different types of DBMS are available and their
classification is done based on the underlying data model.
A data model describes the structure of the database,
including how data are defined and represented,
relationships among data, and the constraints. The most
commonly used data model is Relational Data Model.
Other types of data models include object-oriented data
model, entity-relationship data model, document model
and hierarchical data model.


![Dbms_model](https://github.com/user-attachments/assets/946aa981-b46d-49b0-8565-a19639ca7f7b)

### Relational Data Model
In relational model, tables are called relations that
store data for different columns. Each table can have multiple columns where each column name should be
unique.<br>
a table consists of a collection of relationships.<br>
It is important to note here that relations in a database
are not independent tables, but are associated with each
other.
<br>
<br>
<br>
<br>
<br>
<br>
<br>
![Student_Table](https://github.com/user-attachments/assets/e749ac36-fa4e-4dfd-8d01-94caa09228e3)
<p align="center"><b>Student_Table</b></p>



![Gaurdian_table](https://github.com/user-attachments/assets/9eb6834e-8c90-4f39-85ea-7af677a0b0b3)
<p align="center"><b>Gaurdian_table</b></p>




![Attendance_table](https://github.com/user-attachments/assets/26041b79-4281-478b-89a0-9a4af3b43030)
<p align="center"><b>Attendance_table</b></p>


### Terminologies<br>
##### (i) ATTRIBUTE: 
Characteristic or parameters for
which data are to be stored in a relation. Simply
stated, the columns of a relation are the attributes
which are also referred as fields. For example, GUID,
GName, GPhone and GAddress are attributes of
relation GUARDIAN.<br>
##### (ii) TUPLE: 
Each row of data in a relation (table) is
called a tuple. In a table with n columns, a tuple is
a relationship between the n related values.<br>
##### (iii) DOMAIN: 
It is a set of values from which an attribute
can take a value in each row. Usually, a data type is
used to specify domain for an attribute. For example,
in STUDENT relation, the attribute RollNumber
takes integer values and hence its domain is a set of
integer values. Similarly, the set of character strings
constitutes the domain of the attribute SName.<br>
##### (iv) DEGREE: 
The number of attributes in a relation
is called the Degree of the relation. For example,
relation GUARDIAN with four attributes is a relation
of degree 4.<br>
##### (v) CARDINALITY: 
The number of tuples in a relation
is called the Cardinality of the relation. For example,
the cardinality of relation GUARDIAN is 5 as there
are 5 tuples in the table.<br>

### Three Important Properties of a Relation

In relational data model, following three properties
are observed with respect to a relation which makes a
relation different from a data file or a simple table.<br>
<br>
<br>
<br>
<br>
***Property 1***: imposes following rules on an attribute of
the relation.<br>
• Each attribute in a relation has a unique name.<br>
• Sequence of attributes in a relation is immaterial.
<br>
<br>
<br>
<br>
<br>
***Property 2***: governs following rules on a tuple of a
relation.<br>
• Each tuple in a relation is distinct. For example, data
values in no two tuples of relation ATTENDANCE
can be identical for all the attributes. Thus, each
tuple of a relation must be uniquely identified by
its contents.<br>
• Sequence of tuples in a relation is immaterial.
The tuples are not considered to be ordered, even
though they appear to be in tabular form.
<br>
<br>
<br>
<br>
<br>
***Property 3***: imposes following rules on the state of a
relation.<br>
• All data values in an attribute must be from the
same domain (same data type).<br>
• Each data value associated with an attribute
must be atomic (cannot be further divisible into
meaningful subparts). For example, GPhone of
relation GUARDIAN has ten digit numbers which
is indivisible.<br>
• No attribute can have many data values in one
tuple. For example, Guardian cannot specify
multiple contact numbers under GPhone attribute.<br>
• A special value “NULL” is used to represent
values that are unknown or non-applicable to
certain attributes. For example, if a guardian does
not share his or her contact number with the
school authorities, then GPhone is set to NULL
(data unknown).


#### Keys In A Relational Database
The tuples within a relation must be distinct. It means
no two tuples in a table should have same value for all
attributes. That is, there should be at least one attribute
in which data are distinct (unique) and not NULL.<br>
That
way, we can uniquely distinguish each tuple of a relation.
So, relational data model imposes some restrictions or
constraints on the values of the attributes and how the
contents of one relation be referred through another
relation. These restrictions are specified at the time of
defining the database through different types of keys as
given below:<br>

##### Candidate Key
A relation can have one or more attributes that takes
distinct values. Any of these attributes can be used
to uniquely identify the tuples in the relation. Such
attributes are called candidate keys as each of them
are candidates for the primary key.

##### Primary Key
Out of one or more candidate keys, the attribute chosen
by the database designer to uniquely identify the tuples
in a relation is called the primary key of that relation.
The remaining attributes in the list of candidate keys
are called the alternate keys.

##### Composite Primary Key
If no single attribute in a relation is able to uniquely
distinguish the tuples, then more than one attribute
are taken together as primary key. Such primary key
consisting of more than one attribute is called Composite
Primary key.
##### Foreign Key
A foreign key is used to represent the relationship
between two relations. A foreign key is an attribute
whose value is derived from the primary key of another
relation. This means that any attribute of a relation
(referencing), which is used to refer contents from
another (referenced) relation, becomes foreign key if
it refers to the primary key of referenced relation. The
referencing relation is called Foreign Relation. In some
cases, foreign key can take NULL value if it is not the
part of primary key of the foreign table. The relation in
which the referenced primary key is defined is called
primary relation or master relation.


