# File Handling in Python


## Types of Files

Computers store every file as a collection of 0s and 1s
i.e., in binary form.<br>
There are
mainly two types of data files — text file and binary
file.<br><br>
**Difference Between Text File and Binary File**<br>
| **S. No.** | **Property**                     | **Text File**                                        | **Binary File**                                         |
| :--------: | -------------------------------- | ---------------------------------------------------- | ------------------------------------------------------- |
|      1     | **Data Storage**                 | Stores data as a sequence of readable characters.    | Stores data as a sequence of bytes (0s and 1s).         |
|      2     | **Method of Encoding**           | Uses ASCII or Unicode encoding.                      | Uses binary (machine) encoding.                         |
|      3     | **Human Readability**            | Easily readable by humans.                           | Not readable by humans.                                 |
|      4     | **Ease of Editability**          | Can be edited using text editors (e.g., Notepad).    | Requires special programs or hex editors.               |
|      5     | **Data Representation**          | Represents characters and symbols.                   | Represents raw binary data (e.g., images, executables). |
|      6     | **File Extension**               | Common: `.txt`, `.csv`, `.html`, `.xml`.             | Common: `.exe`, `.jpg`, `.mp3`, `.bin`, `.dat`.         |
|      7     | **File Size**                    | Usually larger due to character encoding.            | Usually smaller due to compact storage.                 |
|      8     | **Memory Space**                 | Consumes more memory for the same data.              | Consumes less memory.                                   |
|      9     | **System Compatibility**         | Highly portable between systems.                     | May vary due to different system architectures.         |
|     10     | **Error Handling**               | Errors can be spotted and corrected easily.          | Errors are hard to detect manually.                     |
|     11     | **Readability by Programs**      | Requires parsing or conversion to numeric data.      | Directly readable by programs.                          |
|     12     | **Data Accuracy**                | May lose precision during text-to-binary conversion. | Maintains high accuracy of stored data.                 |
|     13     | **End of Line Representation**   | Uses `\n` (Linux) or `\r\n` (Windows).               | No specific end-of-line markers.                        |
|     14     | **Mode of Access (Programming)** | Accessed using text mode (`"r"`, `"w"`).             | Accessed using binary mode (`"rb"`, `"wb"`).            |
|     15     | **Data Corruption**              | More likely during encoding/decoding conversions.    | Less likely unless file structure is damaged.           |
|     16     | **Use Cases**                    | Documents, source code, config files.                | Images, videos, executables, database files.            |



![file](https://github.com/user-attachments/assets/1f8056ab-d76e-439a-9cab-6a592855ee94)





















































## Text file

- A text file is a sequence of characters (letters, numbers, symbols).
- Common extensions: .txt, .py, .csv
- Internally stored as bytes (binary 0s and 1s).
- Encodings (ASCII, Unicode) map characters to byte values.
- Example: ASCII 65 (binary 1000001) → 'A'
- Each line ends with an End of Line (EOL) character (e.g., '\n').
- Values are commonly separated by whitespace, commas (','), or tabs ('\t').

## Binary Files
- Binary files are stored as bytes (0s and 1s) that represent actual content, not ASCII characters.
- Examples: images, audio, video, compressed files, executables.
- Binary files are not human-readable; opening them in a text editor shows garbage values.
- Specific software is needed to read/write binary files.
- Files are stored as a sequence of bytes; even a single bit change can corrupt them.
- Errors are difficult to fix since contents are not readable.
- Python can read and write both text and binary files.

## Opening and Closing a Text File
- Real-world programs handle data from sources like databases, CSV, HTML, XML, JSON.
- File operations include creating/opening, writing, traversing, and reading data.
- Python's `io` module provides functions for handling files.

## Opening a file
To open a file in Python, we use the open() function. The
syntax of open() is as follows:
```
file_object= open(file_name, access_mode)
```
This function returns a file object called file handle
which is stored in the variable file_object.<br>
We can
use this variable to transfer data to and from the file
(read and write) by calling the functions defined in the
Python’s io module.<br> If the file does not exist, the above
statement creates a new empty file and assigns it the
name we specify in the statement.<br>

The file_object has certain attributes that tells us
basic information about the file, such as:<br>
• `file.closed` returns true if the file is closed and
false otherwise.<br>
• `file.mode` returns the access mode in which the
file was opened.<br>
• `file.name` returns the name of the file.<br>

*The `file_name` should be the name of the file that has to be opened.*<br>
If the file is not in the current working
directory, then we need to specify the complete path of
the file along with its name.<br>
The `access_mode` is an optional argument that
represents the mode in which the file has to be accessed
by the program.<br>
It is also referred to as processing mode.
Here mode means the operation for which the file has
to be opened like `r` for reading, `w` for writing, `+`
for both reading and writing, `a` for appending at the
end of an existing file. ***The default is the read mode.*** <br>

In
addition, we can specify whether the file will be handled
as binary (`b`) or text mode. ***By default, files are opened in text mode that means strings can be read or written.***<br>
Files containing non-textual data are opened in binary
mode that means read/write are performed in terms of
bytes.

**File Open Modes**
| File Mode          | Description                                                                                                                 | File Offset Position  |
| ------------------ | --------------------------------------------------------------------------------------------------------------------------- | --------------------- |
| `<r>`              | Opens the file in read-only mode.                                                                                           | Beginning of the file |
| `<rb>`             | Opens the file in binary and read-only mode.                                                                                | Beginning of the file |
| `<r+>` or `<+r>`   | Opens the file in both read and write mode.                                                                                 | Beginning of the file |
| `<w>`              | Opens the file in write mode. If the file exists, its contents will be overwritten. Creates a new file if it doesn’t exist. | Beginning of the file |
| `<wb+>` or `<+wb>` | Opens the file in read, write, and binary mode. Overwrites existing contents or creates a new file if it doesn’t exist.     | Beginning of the file |
| `<a>`              | Opens the file in append mode. Creates a new file if it doesn’t exist.                                                      | End of the file       |
| `<a+>` or `<+a>`   | Opens the file in append and read mode. Creates a new file if it doesn’t exist.                                             | End of the file       |



### Closing a file
Once we are done with the read/write operations on a
file, it is a good practice to close the file. Python provides
a close() method to do so. While closing a file, the
system frees the memory allocated to it. The syntax of
`close()` is:<br>

```
file_object.close()
```
Python makes sure that any unwritten or unsaved
data is flushed off (written) to the file before it is closed.<br>
Also, if the file object is re-assigned to
some other file, the previous file is automatically closed.<br>
### Opening a file using with clause
The syntax of `with` clause is:<br>
```
with open (file_name, access_mode) as file_object:
```
The advantage of using with clause is that any file
that is opened using this clause is closed automatically,
once the control comes outside the with clause.<br
In
case the user forgets to close the file explicitly or if an
exception occurs, the file is closed automatically.<br>
It provides a simpler syntax:<br>
```
with open(“myfile.txt”,”r+”) as myObject:
    content = myObject.read()
```
**Note:** we don’t have to close the file explicitly using close() statement. Python will automatically close the file.<br>

## Writing to a Text File
For writing to a file, we first need to open it in write or
append mode.<br>
If we open an existing file in write mode,
the previous data will be erased, and the file object will
be positioned at the beginning of the file.<br>
In append mode, new data will be added at the
end of the previous data as the file object is at the end of
the file.<br> 
After opening the file, we can use the following
methods to write data in the file:<br>
• write() - for writing a single string<br>
• writelines() - for writing a sequence of strings<br>

## The `write()` method
`write()` method takes a string as an argument and writes
it to the text file.<br> It returns the number of characters
being written on single execution of the `write()` method.<br>
Also, we need to add a newline character (\n) at the end
of every sentence to mark the end of line.<br>
**For Example in following Code:**
```
myobject = open("myfile.txt", 'w')
myobject.write("Hey I have started #using files in Python\n")
myobject.close()

```
On execution, write() returns the number of characters
written on to the file.<br>
**Note:** ‘\n’ is treated as a single character<br>
If numeric data are to be written to a text file, the
data need to be converted into string before writing to
the file. For example:
```
myobject=open("myfile.txt",'w')
marks=58
#number 58 is converted to a string using
#str()
myobject.write(str(marks))
myobject.close()
```
The `write()` actually writes data onto a buffer. When
the `close()` method is executed, the contents from this
buffer are moved to the file located on the permanent
storage.

## The writelines() method
This method is used to write multiple strings to a file.
We need to pass an iterable object like lists, tuple, etc.
containing strings to the `writelines()` method.<br>
`write()`, the `writelines()` method does not return the
number of characters written in the file. The following
code explains the use of writelines().
```
myobject=open("myfile.txt",'w')
lines = ["Hello everyone\n", "Writing
#multiline strings\n", "This is the
#third line"]
myobject.writelines(lines)
myobject.close()
```
## The readline([n]) method
This method reads one complete line from a file where
each line terminates with a newline (\n) character.<br> It
can also be used to read a specified number (n) of bytes
of data from a file but maximum up to the newline
character (\n).
```
myobject=open("myfile.txt",'r')
myobject.readline(10)
#'Hello ever'
myobject.close()
```
If no argument or a negative number is specified, it
reads a complete line and returns string.
```
myobject=open("myfile.txt",'r')
print (myobject.readline())
#'Hello everyone\n'
```

*To read the entire file line by line using the readline(), we can use a loop. This process is known as looping/ iterating over a file object. It returns an empty string when EOF is reached.*

## The readlines() method
The method reads all the lines and returns the lines
along with newline as a list of strings.
**Example:**
```
myobject=open("myfile.txt", 'r')
print(myobject.readlines())
#['Hello everyone\n', 'Writing multiline strings\n', 'This is the third line']
myobject.close()
```
when we read a
file using readlines() function, lines in the file become
members of a list, where each list element ends with a
newline character (‘\n’).<br>

In case we want to display each word of a line
separately as an element of a list, then we can use split()
function. The following code demonstrates the use of
split() function.
```
myobject=open("myfile.txt",'r')
d=myobject.readlines()
for line in d:
    words=line.split()
    print(words)
#['Hello', 'everyone']
#['Writing', 'multiline', 'strings']
#['This', 'is', 'the', 'third', 'line']
```
If splitlines() is used instead of split(),
then each line is returned as element of a list, as shown
in the output below:
```
for line in d:
    words=line.splitlines()
    print(words)
#['Hello everyone']
#['Writing multiline strings']
#['This is the third line']
```
```
#Writing and reading to a text file
fobject=open("testfile.txt","w") # creating a data file
sentence=input("Enter the contents to be written in the file: ")
fobject.write(sentence) # Writing data to the file
fobject.close() # Closing a file
print("Now reading the contents of the file: ")
fobject=open("testfile.txt","r")
#looping over the file object to read the file
for str in fobject:
    print(str)
fobject.close()
```
## Setting Offsets In a File
Earlier function access the data sequentially from a file.<br>
To access data in a random fashion, use seek() and tell() functions to do so.
### The tell() method
This function returns an integer that specifies the
current position of the file object in the file. The position
so specified is the byte position from the beginning of
the file till the current position of the file object. The
syntax of using tell() is:<br>
`file_object.tell()`

### The seek() method
This method is used to position the file object at a
particular position in a file. The syntax of seek() is:<br>
`file_object.seek(offset [, reference_point])`
In the above syntax, `offset` is the number of bytes by
which the file object is to be moved. `reference_point`
indicates the starting position of the file object. That is,
with reference to which position, the offset has to be
counted. It can have any of the following values:<br>
0 - beginning of the file<br>
1 - current position of the file<br>
2 - end of file<br>
By default, the value of reference_point is 0, i.e.
the offset is counted from the beginning of the file.

*For example, the statement fileObject.seek(5,0) will position the file object at 5 th byte position from the beginning of the file.*


```
#Application of seek() and tell()
print("Learning to move the fi le object")
fi leobject=open("testfi le.txt","r+")
str=fi leobject.read()
print(str)
print("Initially, the position of the fi le object is: ",fi leobject.
tell())
fi leobject.seek(0)
print("Now the fi le object is at the beginning of the fi le:
",fi leobject.tell())
fi leobject.seek(10)
print("We are moving to 10th byte position from the beginning of
fi le")
print("The position of the fi le object is at", fi leobject.tell())
str=fi leobject.read()
print(str)
```
## CREATING AND TRAVERSING A TEXT FILE
### Creating a file and writing data
To create a text file, we use the open() method and
provide the filename and the mode. If the file already
exists with the same name, the open() function will
behave differently depending on the mode (write or
append) used. If it is in write mode (w), then all the
existing contents of file will be lost, and an empty file
will be created with the same name. But, if the file is created in append mode (a), then the new data will be
written after the existing data. In both cases, if the file
does not exist, then a new empty file will be created.

```
# program to create a text file and add data
fileobject=open("practice.txt","w+")
while True:
    data= input("Enter data to save in the text file: ")
    fileobject.write(data)
    ans=input("Do you wish to enter more data?(y/n): ")
    if ans=='n': break
fileobject.close()
```
### Traversing a file and displaying data
To read and display data that is stored in a text file, we
will refer to the previous example where we have created
the file practice.txt. The file will be opened in read mode
and reading will begin from the beginning of the file.

```
To display data from a text file
fileobject=open("practice.txt","r")
str = fileobject.readline()
while str:
    print(str)
    str=fileobject.readline()
fileobject.close()
```
```
To perform reading and writing operation in a
text file
fileobject=open("report.txt", "w+")
print ("WRITING DATA IN THE FILE")
print() # to display a blank line
while True:
    line= input("Enter a sentence ")
    fileobject.write(line)
    fileobject.write('\n')
    choice=input("Do you wish to enter more data? (y/n): ")
    if choice in ('n','N'): break
print("The byte position of file object is ",fileobject.tell())
fileobject.seek(0) #places file object at beginning of file
print()
print("READING DATA FROM THE FILE")
str=fileobject.read()
print(str)
fileobject.close()
```
## The Pickle Module


- In Python, everything (including lists, tuples, dictionaries) is an object.
- To save an object's state (e.g., game progress or data), use the pickle module.
- The pickle module handles serialization (pickling) and deserialization (unpickling).
- Serialization (pickling): converts a Python object to a byte stream for storage or transfer.
- Deserialization (unpickling): converts a byte stream back into a Python object.
- The pickle module works with binary files and provides:
- dump() — for pickling (saving objects)
- load() — for unpickling (retrieving objects)



### The dump() method
This method is used to convert (pickling) Python objects
for writing data in a binary file. The file in which data
are to be dumped, needs to be opened in binary write
mode (wb).<br>
Syntax of `dump()` is as follows:
```dump(data_object, file_object)```
where `data_object` is the object that has to be
dumped to the file with the file handle named `file_object`.

```
#Pickling data in Python
import pickle
listvalues=[1,"Geetika",'F', 26]
fileobject=open("mybinary.dat", "wb")
pickle.dump(listvalues,fileobject)
fileobject.close()
```
### The load() method
This method is used to load (unpickling) data from a
binary file. The file to be loaded is opened in binary read
(rb) mode. Syntax of load() is as follows:<br>
```Store_object = load(file_object)```
Here, the pickled Python object is loaded from the
file having a file handle named `file_object` and is
stored in a new file handle called `store_object`.

```
#Unpickling data in Python
import pickle
print("The data that were stored in file are: ")
fileobject=open("mybinary.dat","rb")
objectvar=pickle.load(fileobject)
fileobject.close()
print(objectvar)
```

### File handling using pickle module

```
# Program to write and read employee records in a binary file
import pickle

print("WORKING WITH BINARY FILES")

# Open the binary file in append mode
bfile = open("empfile.dat", "ab")

recno = 1
print("Enter Records of Employees\n")

# Taking data from user and dumping in the file as list object
while True:
    print("RECORD No.", recno)
    eno = int(input("\tEmployee number : "))
    ename = input("\tEmployee Name : ")
    ebasic = int(input("\tBasic Salary : "))
    allow = int(input("\tAllowances : "))
    totsal = ebasic + allow
    print("\tTOTAL SALARY : ", totsal)

    edata = [eno, ename, ebasic, allow, totsal]
    pickle.dump(edata, bfile)

    ans = input("Do you wish to enter more records (y/n)? ")
    recno += 1
    if ans.lower() == 'n':
        print("Record entry OVER\n")
        break

# Retrieving the size of file
print("Size of binary file (in bytes):", bfile.tell())
bfile.close()

# Reading the employee records from the file using load() method
print("Now reading the employee records from the file\n")

readrec = 1
try:
    with open("empfile.dat", "rb") as bfile:
        while True:
            edata = pickle.load(bfile)
            print("Record Number :", readrec)
            print(edata)
            readrec += 1
except EOFError:
    pass

```





