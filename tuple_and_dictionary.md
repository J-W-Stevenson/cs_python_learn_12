# Tuples and Dictionaries
## Tuple
A tuple is an ordered sequence of elements of different
data types, such as integer, float, string, list or even a
tuple. Elements of a tuple are enclosed in parenthesis
(round brackets) and are separated by commas. Like list
and string, elements of a tuple can be accessed using
index values, starting from 0.

```
# tuple1 is a tuple of integers
tuple1 = (1, 2, 3, 4, 5)
print(tuple1)  # Output: (1, 2, 3, 4, 5)

# tuple2 is a tuple of mixed data types
tuple2 = ('Economics', 87, 'Accountancy', 89.6)
print(tuple2)  # Output: ('Economics', 87, 'Accountancy', 89.6)

# tuple3 is a tuple with a list as an element
tuple3 = (10, 20, 30, [40, 50])
print(tuple3)  # Output: (10, 20, 30, [40, 50])

# tuple4 is a tuple with another tuple as an element
tuple4 = (1, 2, 3, 4, 5, (10, 20))
print(tuple4)  # Output: (1, 2, 3, 4, 5, (10, 20))

```

If there is only a single element in a tuple then the
element should be followed by a comma. If we assign the
value without comma it is treated as integer. It should
be noted that a sequence without parenthesis is treated
as tuple by default.
```
# Incorrect way of assigning a single element to a tuple
# tuple5 is assigned a single element without a comma
tuple5 = (20)
print(tuple5)           # Output: 20
print(type(tuple5))     # Output: <class 'int'> — it's treated as an integer

# Correct way of assigning a single element to a tuple
# The element is followed by a comma
tuple5 = (20,)
print(tuple5)           # Output: (20,)
print(type(tuple5))     # Output: <class 'tuple'>

# A sequence without parentheses is treated as a tuple by default
seq = 1, 2, 3  # Comma-separated values without parentheses
print(type(seq))        # Output: <class 'tuple'>
print(seq)              # Output: (1, 2, 3)


```

### Accessing Elements in a Tuple

Elements of a tuple can be accessed in the same way as
a list or string using indexing and slicing.
```
# Initializes a tuple tuple1
tuple1 = (2, 4, 6, 8, 10, 12)

# Returns the first element of tuple1
print(tuple1[0])  # Output: 2

# Returns the fourth element of tuple1
print(tuple1[3])  # Output: 8

# Attempting to access an index out of range (will raise an error)
# print(tuple1[15])  # Uncommenting this line will raise: IndexError

# An expression resulting in an integer index
print(tuple1[1 + 4])  # Output: 12

# Returns the first element from the right (last element)
print(tuple1[-1])  # Output: 12

```

### Tuple is Immutable
Tuple is an immutable data type. It means that the
elements of a tuple cannot be changed after it has been
created. An attempt to do this would lead to an error.
```
# Create a tuple with all integer elements
tuple1 = (1, 2, 3, 4, 5)

# Tuples are immutable — trying to modify an element will raise an error
# tuple1[4] = 10  # Uncommenting this line will raise:
# TypeError: 'tuple' object does not support item assignment

# Tuples are often used to store elements of different data types,
# while lists are commonly used for elements of the same type.
```
However, a tuple can contain mutable elements like lists
```
# The 4th element of tuple2 is a list
tuple2 = (1, 2, 3, [8, 9])

# Modify an element within the list inside the tuple
tuple2[3][1] = 10

# The modification is reflected in the tuple
print(tuple2)  # Output: (1, 2, 3, [8, 10])

```
### Tuple Operations
**Concatenation**<br>
Python allows us to join tuples using concatenation
operator depicted by symbol +. We can also create a new
tuple which contains the result of this concatenation
operation.<br>
```
# Create two tuples of odd and even numbers
tuple1 = (1, 3, 5, 7, 9)
tuple2 = (2, 4, 6, 8, 10)

# Concatenate the two tuples
print(tuple1 + tuple2)  
# Output: (1, 3, 5, 7, 9, 2, 4, 6, 8, 10)

# Create tuples of color names
tuple3 = ('Red', 'Green', 'Blue')
tuple4 = ('Cyan', 'Magenta', 'Yellow', 'Black')

# Concatenate tuple3 and tuple4 into tuple5
tuple5 = tuple3 + tuple4
print(tuple5)  
# Output: ('Red', 'Green', 'Blue', 'Cyan', 'Magenta', 'Yellow', 'Black')
```
Concatenation operator can also be used for
extending an existing tuple. When we extend a tuple
using concatenation a new tuple is created.
```
# Create a tuple tuple6
tuple6 = (1, 2, 3, 4, 5)

# Append a single element to tuple6 (note the comma to form a tuple)
tuple6 = tuple6 + (6,)
print(tuple6)  
# Output: (1, 2, 3, 4, 5, 6)

# Append multiple elements to tuple6
tuple6 = tuple6 + (7, 8, 9)
print(tuple6)  
# Output: (1, 2, 3, 4, 5, 6, 7, 8, 9)

```
**Repetition**<br>
Repetition operation is depicted by the symbol *. It is
used to repeat elements of a tuple. We can repeat the
tuple elements. The repetition operator requires the first
operand to be a tuple and the second operand to be an
integer only.<br>
```
# Create a tuple with two string elements
tuple1 = ('Hello', 'World')

# Repeat the tuple 3 times using the * operator
print(tuple1 * 3)
# Output: ('Hello', 'World', 'Hello', 'World', 'Hello', 'World')

# Create a tuple with a single element (note the comma)
tuple2 = ('Hello',)

# Repeat the single-element tuple 4 times
print(tuple2 * 4)
# Output: ('Hello', 'Hello', 'Hello', 'Hello')

```
**Membership**<br>
The in operator checks if the element is present in the
tuple and returns True, else it returns False.
```
# Create a tuple of colors
tuple1 = ('Red', 'Green', 'Blue')

# Check if 'Green' is in the tuple
print('Green' in tuple1)  
# Output: True

```
The not in operator returns True if the element is
not present in the tuple, else it returns False.
```
# Create a tuple of colors
tuple1 = ('Red', 'Green', 'Blue')

# Check if 'Green' is not in the tuple
print('Green' not in tuple1)  
# Output: False

```
**Slicing**<br>
Like string and list, slicing can be applied to tuples also.
```
# tuple1 is a tuple
tuple1 = (10, 20, 30, 40, 50, 60, 70, 80)

# Elements from index 2 to index 6 (7 is excluded)
print(tuple1[2:7])  
# Output: (30, 40, 50, 60, 70)

# All elements of the tuple using slicing
print(tuple1[0:len(tuple1)])  
# Output: (10, 20, 30, 40, 50, 60, 70, 80)

# Slice starting from index 0 to index 4
print(tuple1[:5])  
# Output: (10, 20, 30, 40, 50)

# Slice from index 2 to the end of the tuple
print(tuple1[2:])  
# Output: (30, 40, 50, 60, 70, 80)

# Slice with step size of 2
print(tuple1[0:len(tuple1):2])  
# Output: (10, 30, 50, 70)

# Negative indexing: elements from index -6 to -4 (excluding -4)
print(tuple1[-6:-4])  
# Output: (30, 40)

# Reverse the tuple using slicing
print(tuple1[::-1])  
# Output: (80, 70, 60, 50, 40, 30, 20, 10)

```
**Built-in functions and methods for tuples**

| **Method**       | **Description**                                                                                 | **Example**                                                                                                                                                            |
|------------------|------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `len()`          | Returns the length or the number of elements in the tuple.                                     | `tuple1 = (10, 20, 30, 40, 50) `<br> ` len(tuple1) # 5`                                                                                                        |
| `tuple()`        | Creates an empty tuple if no argument is passed; creates a tuple from a sequence if given.     | `tuple1 = tuple() `<br> ` tuple1 # () `<br> ` tuple1 = tuple('aeiou') `<br> ` tuple1 # ('a', 'e', 'i', 'o', 'u') `<br> ` tuple2 = tuple([1, 2, 3]) `<br> ` tuple2 # (1, 2, 3)`  |
| `count()`        | Returns the number of times the given element appears in the tuple.                            | `tuple1 = (10, 20, 30, 10, 40, 10, 50) `<br> ` tuple1.count(10) # 3 `<br> ` tuple1.count(90) # 0`                                                                  |
| `index()`        | Returns the index of the first occurrence of the element. Raises ValueError if not found.      | `tuple1 = (10, 20, 30, 40, 50) `<br> ` tuple1.index(30) # 2 `<br> ` tuple1.index(90) # ValueError: tuple.index(x): x not in tuple`                                  |
| `sorted()`       | Returns a new sorted list of the tuple’s elements without modifying the original tuple.        | `tuple1 = ("Rama","Heena","Raj","Mohsin","Aditya") `<br> ` sorted(tuple1) # ['Aditya', 'Heena', 'Mohsin', 'Raj', 'Rama']`                                        |
| `min()`          | Returns the smallest element in the tuple.                                                    | `tuple1 = (19, 12, 56, 18, 9, 87, 34) `<br> ` min(tuple1) # 9`                                                                                                |
| `max()`          | Returns the largest element in the tuple.                                                     | `tuple1 = (19, 12, 56, 18, 9, 87, 34) `<br> ` max(tuple1) # 87`                                                                                               |
| `sum()`          | Returns the sum of all elements in the tuple.                                                 | `tuple1 = (19, 12, 56, 18, 9, 87, 34) `<br> ` sum(tuple1) # 235`                                                                                              |





### Tuple Assignment

It allows a tuple of variables on the left side of the
assignment operator to be assigned respective values
from a tuple on the right side. The number of variables
on the left should be same as the number of elements
in the tuple.

```
# Assign values using tuple unpacking
num1, num2 = 10, 20
print(num1)   # Output: 10
print(num2)   # Output: 20

# Another example with a tuple
record = ("Pooja", 40, "CS")
name, rollNo, subject = record
print(name)     # Output: Pooja
print(rollNo)   # Output: 40
print(subject)  # Output: CS

# Example showing unpacking error
a, b, c, d = (5, 6, 8)  # This will raise a ValueError

```
If there is an expression on the right side then first
that expression is evaluated and finally the result is
assigned to the tuple.

```
# 15 is assigned to num3 and 25 is assigned to num4
num3, num4 = (10 + 5, 20 + 5)
print(num3)  # Output: 15
print(num4)  # Output: 25

```

### Nested Tuples

A tuple inside another tuple is called a nested tuple.

```
#This is a program to create a nested tuple to store roll number, name and marks of students

st=((101,"Aditya",98),(102,"Sameer",95),(103,"Sahil",87),(104,"Priyanka",79))
print("S_No"," Roll_No"," Name"," Marks")
for i in range(0,len(st)):
print((i+1),'\t',st[i][0],'\t',st[i][1],'\t',st[i][2])
```
### Tuple Handling

```
#Write a program to swap two numbers without using a temporary variable.
num1 = int(input('Enter the first number: '))
num2 = int(input('Enter the second number: '))

print("\nNumbers before swapping:")
print("First Number:", num1)
print("Second Number:", num2)

# Swap the numbers using tuple unpacking
num1, num2 = num2, num1

print("\nNumbers after swapping:")

# \t is an escape character used for adding horizontal tab space.
# Another commonly used escape character is \n, used for inserting a new line.

print("First Number:", num1)
print("Second Number:", num2)

```
```
#Write a program to compute the area and circumference of a circle using a function.
def circle(r):
    area = 3.14 * r * r
    circumference = 2 * 3.14 * r
    # Returns a tuple having two elements: area and circumference
    return (area, circumference)
    # end of function

radius = int(input('Enter radius of circle: '))
area, circumference = circle(radius)

print('Area of circle is:', area)
print('Circumference of circle is:', circumference)

```

```
#Write a program to input n numbers from the user. Store these numbers in a tuple. Print the maximum and minimum number from this tuple.
numbers = tuple()  # create an empty tuple 'numbers'
n = int(input("How many numbers you want to enter?: "))

for i in range(n):
    num = int(input())
    # add the entered number to the tuple 'numbers'
    numbers = numbers + (num,)

print('\nThe numbers in the tuple are:')
print(numbers)

print("\nThe maximum number is:")
print(max(numbers))

print("The minimum number is:")
print(min(numbers))

```
## Introduction to Dictionaries
The data type dictionary fall under mapping. It is a
mapping between a set of keys and a set of values.
The key-value pair is called an item. A key is separated
from its value by a colon(:) and consecutive items are
separated by commas. Items in dictionaries are ordered,
so we will get back the data in the same order in which
we had entered the data initially in the dictionary.<br>


**Creating a Dictionary**<br>
*To create a dictionary, the items entered are separated by commas and enclosed in curly braces.<br> Each item is a key value pair, separated through colon (:).<br> The keys in the dictionary must be unique and should be of any immutable data type, i.e., number, string or tuple.<br> The values can be repeated and can be of any data type.*

```
# dict1 is an empty dictionary created using curly braces
dict1 = {}
print(dict1)  # Output: {}

# dict2 is an empty dictionary created using the built-in dict() function
dict2 = dict()
print(dict2)  # Output: {}

# dict3 is a dictionary mapping student names to their marks in percentage
dict3 = {
    'Mohan': 95,
    'Ram': 89,
    'Suhel': 92,
    'Sangeeta': 85
}
print(dict3)
# Output: {'Mohan': 95, 'Ram': 89, 'Suhel': 92, 'Sangeeta': 85}

```
**Accessing Items in a Dictionary**<br>
The items of a dictionary are accessed
via the keys rather than via their relative positions
or indices. Each key serves as the index and maps to
a value.
```
dict3 = {'Mohan': 95, 'Ram': 89, 'Suhel': 92, 'Sangeeta': 85}

# Accessing existing keys
print(dict3['Ram'])       # Output: 89
print(dict3['Sangeeta'])  # Output: 85

# Accessing a key that does not exist raises a KeyError
# Uncommenting the next line will cause an error:
# print(dict3['Shyam'])  # KeyError: 'Shyam'

# To avoid error, you can use dict.get() which returns None (or a default value) if key is missing:
print(dict3.get('Shyam'))          # Output: None
print(dict3.get('Shyam', 'Not Found'))  # Output: Not Found

```


**Dictionaries are mutable**<br>
Dictionaries are mutable which implies that the
contents of the dictionary can be changed after it has
been created.<br>

**Adding a new item**
```
dict1 = {'Mohan': 95, 'Ram': 89, 'Suhel': 92, 'Sangeeta': 85}

# Adding a new key-value pair to the dictionary
dict1['Meena'] = 78

print(dict1)
# Output: {'Mohan': 95, 'Ram': 89, 'Suhel': 92, 'Sangeeta': 85, 'Meena': 78}

```
**Modifying an Existing Item**
```
dict1 = {'Mohan': 95, 'Ram': 89, 'Suhel': 92, 'Sangeeta': 85}

# Update marks of Suhel to 93.5
dict1['Suhel'] = 93.5

print(dict1)
# Output: {'Mohan': 95, 'Ram': 89, 'Suhel': 93.5, 'Sangeeta': 85}

```

**Dictionary operations**

**Membership in Dictionaries**<br>
Python uses the membership operators `in` and `not in` to check if a key exists in a dictionary. The `in` operator returns `True` if the key is present, otherwise `False`. Conversely, `not in` returns `True` if the key is not present, otherwise `False`.

```
dict1 = {'Mohan': 95, 'Ram': 89, 'Suhel': 92, 'Sangeeta': 85}

# Check if 'Suhel' is a key in the dictionary
print('Suhel' in dict1)
# Output: True

# Check if 'Suhel' is NOT a key in the dictionary
print('Suhel' not in dict1)
# Output: False
```

**Note:** Membership operators check only the keys of the dictionary, not the values.

---

**Traversing a Dictionary**<br>
You can access each key-value pair in a dictionary using a `for` loop. There are two common methods to traverse a dictionary:

**Method 1:** Iterate through keys and access values using the key.

```
dict1 = {'Mohan': 95, 'Ram': 89, 'Suhel': 92, 'Sangeeta': 85}

for key in dict1:
    print(key, ':', dict1[key])

'''
Mohan : 95
Ram : 89
Suhel : 92
Sangeeta : 85
'''
```

Output:



**Method 2:** Use the `.items()` method to get key-value pairs directly.

```
for key, value in dict1.items():
    print(key, ':', value)
#Output is the same as above.
```


---

**Built-in functions and methods for dictionary**



| Method     | Description                                                       | Example                                                                                                                                                                                 |
| ---------- | ----------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `len()`    | Returns the length or number of key:value pairs in the dictionary | `dict1 = {'Mohan':95,'Ram':89,'Suhel':92,'Sangeeta':85}`<br>`print(len(dict1))`<br>`# Output: 4`                                                                                  |
| `dict()`   | Creates a dictionary from a sequence of key-value pairs           | `pair1 = [('Mohan',95), ('Ram',89), ('Suhel',92), ('Sangeeta',85)]`<br>`dict1 = dict(pair1)`<br>`print(dict1)`<br>`# Output: {'Mohan': 95, 'Ram': 89, 'Suhel': 92, 'Sangeeta': 85}` |
| `keys()`   | Returns a list of keys in the dictionary                          | `print(dict1.keys())`<br>`# Output: dict_keys(['Mohan', 'Ram', 'Suhel', 'Sangeeta'])`                                                                                           |
| `values()` | Returns a list of values in the dictionary                        | `print(dict1.values())`<br>`# Output: dict_values([95, 89, 92, 85])`                                                                                                            |
| `items()`  | Returns a list of tuples (key, value) pairs                       | `print(dict1.items())`<br>`# Output: dict_items([('Mohan', 95), ('Ram', 89), ('Suhel', 92), ('Sangeeta', 85)])`                                                                 |
| `get()`    | Returns the value for a given key; returns None if key absent     | `print(dict1.get('Sangeeta'))`<br>`# Output: 85`<br>`print(dict1.get('Sohan'))`<br>`# Output: None`                                                                                 |
| `update()` | Adds key-value pairs from another dictionary                      | `dict2 = {'Sohan':79,'Geeta':89}`<br>`dict1.update(dict2)`<br>`print(dict1)`<br>`# Output: {'Mohan': 95, 'Ram': 89, 'Suhel': 92, 'Sangeeta': 85, 'Sohan': 79, 'Geeta': 89}`         |
| `del`      | Deletes an item with the given key or deletes the dictionary      | `del dict1['Ram']`<br>`# Removes 'Ram' key`<br>`del dict1`<br>`# Deletes entire dict`<br>`print(dict1)  # NameError`                                                                  |
| `clear()`  | Deletes or clears all items of the dictionary                     | `dict1.clear()`<br>`print(dict1)`<br>`# Output: {}`                                                                                                                               |



**Manipulating Dictionaries**<br>

Create a dictionary **ODD** of odd numbers between 1 and 10, where the key is the decimal number and the value is the corresponding number in words. Perform the following operations on this dictionary:

(a) *Display the keys* <br>
(b) *Display the values* <br>
(c) *Display the items* <br>
(d) *Find the length of the dictionary* <br>
(e) *Check if 7 is present or not* <br>
(f) *Check if 2 is present or not* <br>
(g) *Retrieve the value corresponding to the key 9* <br>
(h) *Delete the item from the dictionary corresponding to the key 9* <br>

```python
ODD = {1:'One', 3:'Three', 5:'Five', 7:'Seven', 9:'Nine'}
print(ODD)
# {1: 'One', 3: 'Three', 5: 'Five', 7: 'Seven', 9: 'Nine'}

# (a) Display the keys
print(ODD.keys())
# dict_keys([1, 3, 5, 7, 9])

# (b) Display the values
print(ODD.values())
# dict_values(['One', 'Three', 'Five', 'Seven', 'Nine'])

# (c) Display the items
print(ODD.items())
# dict_items([(1, 'One'), (3, 'Three'), (5, 'Five'), (7, 'Seven'), (9, 'Nine')])

# (d) Find the length of the dictionary
print(len(ODD))
# 5

# (e) Check if 7 is present or not
print(7 in ODD)
# True

# (f) Check if 2 is present or not
print(2 in ODD)
# False

# (g) Retrieve the value corresponding to the key 9
print(ODD.get(9))
# 'Nine'

# (h) Delete the item from the dictionary corresponding to the key 9
del ODD[9]
print(ODD)
# {1: 'One', 3: 'Three', 5: 'Five', 7: 'Seven'}
```

***Write a program to enter names of employees and their salaries as input and store them in a dictionary.***

```
num = int(input("Enter the number of employees whose data to be stored: "))
count = 1
employee = dict()  # create an empty dictionary

while count <= num:
    name = input("Enter the name of the Employee: ")
    salary = int(input("Enter the salary: "))
    employee[name] = salary
    count += 1

print("\n\nEMPLOYEE_NAME\tSALARY")
for k in employee:
    print(k, '\t\t', employee[k])

'''
Output:
Enter the number of employees to be stored: 5
Enter the name of the Employee: 'Tarun'
Enter the salary: 12000
Enter the name of the Employee: 'Amina'
Enter the salary: 34000
Enter the name of the Employee: 'Joseph'
Enter the salary: 24000
Enter the name of the Employee: 'Rahul'
Enter the salary: 30000
Enter the name of the Employee: 'Zoya'
Enter the salary: 25000
EMPLOYEE_NAME    SALARY
'Tarun'          12000
'Amina'          34000
'Joseph'         24000
'Rahul'          30000
'Zoya'           25000

'''


```
***Write a program to count the number of times a character appears in a given string.***
```
st = input("Enter a string: ")
dic = {}  # creates an empty dictionary

for ch in st:
    if ch in dic:  # if next character is already in the dictionary
        dic[ch] += 1
    else:
        dic[ch] = 1  # if ch appears for the first time

for key in dic:
    print(key, ':', dic[key])

'''
Output:
Enter a string: HelloWorld
H : 1
e : 1
l : 3
o : 2
W : 1
r : 1
d : 1
'''
```
***Write a function to convert a number entered by the user into its corresponding number in words. For example, if the input is 876 then the output should be ‘Eight Seven Six’.***
```
def convert(num):
    # numberNames is a dictionary of digits and corresponding number names
    numberNames = {
        0: 'Zero', 1: 'One', 2: 'Two', 3: 'Three', 4: 'Four',
        5: 'Five', 6: 'Six', 7: 'Seven', 8: 'Eight', 9: 'Nine'
    }
    result = ''
    for ch in num:
        key = int(ch)  # converts character to integer
        value = numberNames[key]
        result = result + ' ' + value
    return result

num = input("Enter any number: ")  # number is stored as string
result = convert(num)
print("The number is:", num)
print("The numberName is:", result)


'''
Output:
Enter any number: 6512
The number is: 6512
The numberName is: Six Five One Two
'''
```
