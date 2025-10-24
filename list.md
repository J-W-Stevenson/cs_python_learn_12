# Lists

The data type list is an ordered sequence which is mutable and made up of one or more elements.<br>
A list is very
useful to group together elements of mixed data types.
Elements of a list are enclosed in square brackets and
are separated by comma. Like string indices, list indices
also start from 0.<br>

```
# list1 is the list of six even numbers
list1 = [2, 4, 6, 8, 10, 12]
print(list1)

# list2 is the list of vowels
list2 = ['a', 'e', 'i', 'o', 'u']
print(list2)

# list3 is the list of mixed data types
list3 = [100, 23.5, 'Hello']
print(list3)

# list4 is a nested list (list of lists)
list4 = [['Physics', 101], ['Chemistry', 202], ['Maths', 303]]
print(list4)

```
**Accessing Elements in a List**<br>
The elements of a list are accessed in the same way as
characters are accessed in a string.<br>
```
# Initializes a list list1
list1 = [2, 4, 6, 8, 10, 12]

# Return first element of list1
print(list1[0])  # Output: 2

# Return fourth element of list1
print(list1[3])  # Output: 8

# Attempt to access an index out of range (will raise an error)
# print(list1[15])  # Uncommenting this line will raise: IndexError

# Expression resulting in an integer index
print(list1[1 + 4])  # Output: 12

# Return the last element using negative index
print(list1[-1])  # Output: 12

# Length of the list is assigned to n
n = len(list1)
print(n)  # Output: 6

# Return the last element using length
print(list1[n - 1])  # Output: 12

# Return the first element using negative index and length
print(list1[-n])  # Output: 2
```

**Lists are Mutable**<br>
In Python, lists are mutable. It means that the contents
of the list can be changed after it has been created.<br>

```
# List list1 of colors
list1 = ['Red', 'Green', 'Blue', 'Orange']

# Change/override the fourth element of list1
list1[3] = 'Black'

# Print the modified list
print(list1)  # Output: ['Red', 'Green', 'Blue', 'Black']

```



<br>






---

**List Operations**<br>
Python allows manipulation of list data types through various operations such as concatenation, repetition, membership, slicing, and traversal.<br>

---

**Concatenation**<br>
Python allows us to join two or more lists using the **concatenation operator** denoted by the symbol `+`.<br>

```
# list1 is a list of first five odd integers
list1 = [1, 3, 5, 7, 9]
# list2 is a list of first five even integers
list2 = [2, 4, 6, 8, 10]

# Concatenate list1 and list2
print(list1 + list2)
# Output: [1, 3, 5, 7, 9, 2, 4, 6, 8, 10]

# Another example with color names
list3 = ['Red', 'Green', 'Blue']
list4 = ['Cyan', 'Magenta', 'Yellow', 'Black']
print(list3 + list4)
# Output: ['Red', 'Green', 'Blue', 'Cyan', 'Magenta', 'Yellow', 'Black']
```

**Note:** Original lists (`list1`, `list2`, etc.) remain unchanged after concatenation.<br>
If we want to **store** the result, we must assign it to a new list using `=`.<br>
The `+` operator **only works between lists**. Trying to concatenate a list with another data type results in a **TypeError**.

```
list1 = [1, 2, 3]
str1 = "abc"
print(list1 + str1)
# TypeError: can only concatenate list (not "str") to list
```

---

**Repetition**<br>
Python allows repetition of list elements using the **repetition operator** `*`.<br>

```
list1 = ['Hello']
# Repeating the list elements 4 times
print(list1 * 4)
# Output: ['Hello', 'Hello', 'Hello', 'Hello']
```

**Note:** The original list remains unchanged after repetition.

---

**Membership**<br>
Python supports membership operators `in` and `not in` to check the presence of an element in a list.<br>

```
list1 = ['Red', 'Green', 'Blue']

# Checking if an item exists in the list
print('Green' in list1)
# Output: True

print('Cyan' in list1)
# Output: False

# Checking if an item does NOT exist in the list
print('Cyan' not in list1)
# Output: True

print('Green' not in list1)
# Output: False
```

---

**Slicing**<br>
Like strings, slicing can also be applied to lists to extract sublists using index positions.<br>

```
list1 = ['Red', 'Green', 'Blue', 'Cyan', 'Magenta', 'Yellow', 'Black']

# Slice from index 2 to 5 (6 is excluded)
print(list1[2:6])
# Output: ['Blue', 'Cyan', 'Magenta', 'Yellow']

# Slice beyond the list length (automatically adjusts to end)
print(list1[2:20])
# Output: ['Blue', 'Cyan', 'Magenta', 'Yellow', 'Black']

# First index > second index → results in empty list
print(list1[7:2])
# Output: []

# First index is omitted (defaults to 0)
print(list1[:5])
# Output: ['Red', 'Green', 'Blue', 'Cyan', 'Magenta']

# Slicing with step size
print(list1[0:6:2])
# Output: ['Red', 'Blue', 'Magenta']

# Slicing with negative indexes
print(list1[-6:-2])
# Output: ['Green', 'Blue', 'Cyan', 'Magenta']

# Slicing entire list with step size 2
print(list1[::2])
# Output: ['Red', 'Blue', 'Magenta', 'Black']

# Reversing the list using negative step size
print(list1[::-1])
# Output: ['Black', 'Yellow', 'Magenta', 'Cyan', 'Blue', 'Green', 'Red']
```

---

**Traversing a List**<br>
We can access or traverse each element of a list using **for** and **while** loops.<br>

**(A) Traversal Using `for` Loop:**<br>

```
list1 = ['Red', 'Green', 'Blue', 'Yellow', 'Black']

for item in list1:
    print(item)

# Output:
# Red
# Green
# Blue
# Yellow
# Black
```

We can also use `range()` and `len()` functions to access list elements using their indexes.

```
for i in range(len(list1)):
    print(list1[i])

# Output:
# Red
# Green
# Blue
# Yellow
# Black
```

**(B) Traversal Using `while` Loop:**<br>

```
list1 = ['Red', 'Green', 'Blue', 'Yellow', 'Black']
i = 0

while i < len(list1):
    print(list1[i])
    i += 1

# Output:
# Red
# Green
# Blue
# Yellow
# Black
```

Here, the `while` loop continues as long as the index `i` is less than the length of the list.<br>


| **Method**  | **Description**                                                                           | **Example**                                                                                                                                                                                         |
| ----------- | ----------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `len()`     | Returns the length (number of elements) of the list.                                      | `list1 = [10, 20, 30, 40, 50] `<br>` print(len(list1)) `<br>` # 5 `                                                                                                                            |
| `list()`    | Creates an empty list if no argument is passed; creates a list from a sequence.           | `list1 = list() `<br>` print(list1) `<br>` # [] `<br>` str1 = 'aeiou' `<br>` list2 = list(str1) `<br>` print(list2) `<br>` # ['a', 'e', 'i', 'o', 'u'] `                                                   |
| `append()`  | Appends a single element (can be a list) at the end of the list.                          | `list1 = [10, 20, 30, 40] `<br>` list1.append(50) `<br>` print(list1) `<br>` # [10, 20, 30, 40, 50] `<br>` list1.append([60, 70]) `<br>` print(list1) `<br>` # [10, 20, 30, 40, 50, [60, 70]] `            |
| `extend()`  | Appends each element of the iterable to the end of the list.                              | `list1 = [10, 20, 30] `<br>` list2 = [40, 50] `<br>` list1.extend(list2) `<br>` print(list1) `<br>` # [10, 20, 30, 40, 50] `                                                                         |
| `insert()`  | Inserts an element at a specified index in the list.                                      | `list1 = [10, 20, 30, 40, 50] `<br>` list1.insert(2, 25) `<br>` print(list1) `<br>` # [10, 20, 25, 30, 40, 50] `<br>` list1.insert(0, 5) `<br>` print(list1) `<br>` # [5, 10, 20, 25, 30, 40, 50] `        |
| `count()`   | Returns the number of times a specified element appears in the list.                      | `list1 = [10, 20, 30, 10, 40, 10] `<br>` print(list1.count(10)) `<br>` # 3 `<br>` print(list1.count(90)) `<br>` # 0 `                                                                                |
| `index()`   | Returns the index of the first occurrence of the element. Raises ValueError if not found. | `list1 = [10, 20, 30, 20, 40, 10] `<br>` print(list1.index(20)) `<br>` # 1 `<br>` list1.index(90) `<br>` # ValueError: 90 is not in list `                                                           |
| `remove()`  | Removes the first occurrence of the element. Raises ValueError if not found.              | `list1 = [10, 20, 30, 40, 50, 30] `<br>` list1.remove(30) `<br>` print(list1) `<br>` # [10, 20, 40, 50, 30] `<br>` list1.remove(90) `<br>` # ValueError: list.remove(x): x not in list `                |
| `pop()`     | Removes and returns the element at the given index. Defaults to last element.             | `list1 = [10, 20, 30, 40, 50, 60] `<br>` print(list1.pop(3)) `<br>` # 40 `<br>` print(list1) `<br>` # [10, 20, 30, 50, 60] `<br>` print(list1.pop()) `<br>` # 60 `<br>` print(list1) `<br>` # [10, 20, 30, 50] ` |
| `reverse()` | Reverses the order of the list in place.                                                  | `list1 = [34, 66, 12, 89, 28, 99] `<br>` list1.reverse() `<br>` print(list1) `<br>` # [99, 28, 89, 12, 66, 34] `                                                                                  |
| `sort()`    | Sorts the list in place. Use `reverse=True` for descending order.                         | `list1 = [34, 66, 12, 89, 28, 99] `<br>` list1.sort() `<br>` print(list1) `<br>` # [12, 28, 34, 66, 89, 99] `<br>` list1.sort(reverse=True) `<br>` print(list1) `<br>` # [99, 89, 66, 34, 28, 12] `        |
| `sorted()`  | Returns a new sorted list from the iterable.                                              | `list1 = [23, 45, 11, 67, 85, 56] `<br>` list2 = sorted(list1) `<br>` print(list1) `<br>` # [23, 45, 11, 67, 85, 56] `<br>` print(list2) `<br>` # [11, 23, 45, 56, 67, 85] `                            |
| `min()`     | Returns the smallest element in the list.                                                 | `list1 = [34, 12, 63, 39, 92, 44] `<br>` print(min(list1)) `<br>` # 12 `                                                                                                                       |
| `max()`     | Returns the largest element in the list.                                                  | `list1 = [34, 12, 63, 39, 92, 44] `<br>` print(max(list1)) `<br>` # 92 `                                                                                                                       |
| `sum()`     | Returns the sum of all elements in the list.                                              | `list1 = [34, 12, 63, 39, 92, 44] `<br>` print(sum(list1)) `<br>` # 284 `                                                                                                                      |


<br>


### Nested Lists

When a list appears as an element of another list, it is called a nested list.

```
list1 = [1, 2, 'a', 'c', [6, 7, 8], 4, 9]
print(list1[4])
print(list1[4][1])

'''
[6, 7, 8]
7
'''
```

To access an element of the nested list, use two indices: `list1[i][j]` — `i` for the outer list and `j` for the nested list element.

---

### Copying Lists

Assigning one list to another doesn’t create a new list, it just creates an alias:

```
list1 = [1, 2, 3]
list2 = list1
list1.append(10)
print(list1)
print(list2)

'''
[1, 2, 3, 10]
[1, 2, 3, 10]
'''
```

To create a **copy** (not an alias), use one of the following methods:

**Method 1: Using slicing**

```
list1 = [1, 2, 3, 4, 5]
list2 = list1[:]
print(list2)

'''
[1, 2, 3, 4, 5]
'''
```

**Method 2: Using `list()`**

```
list1 = [10, 20, 30, 40]
list2 = list(list1)
print(list2)

'''
[10, 20, 30, 40]
'''
```

**Method 3: Using `copy()` function**

```
import copy

list1 = [1, 2, 3, 4, 5]
list2 = copy.copy(list1)
print(list2)

'''
[1, 2, 3, 4, 5]
'''
```

---

### List as Argument to a Function<br>

#### Case A: List reference is passed<br>


Changes in the function affect the original list.<br>

*Program to increment the elements of a list. The list is passed as an argument to a function.*
```
def increment(list2):
    for i in range(len(list2)):
        list2[i] += 5
    print('Reference of list inside function:', id(list2))

list1 = [10, 20, 30, 40, 50]
print("Reference of list in main:", id(list1))
print("Before function call:", list1)
increment(list1)
print("After function call:", list1)

'''
Reference of list in main: 70615968
Before function call: [10, 20, 30, 40, 50]
Reference of list inside function: 70615968
After function call: [15, 25, 35, 45, 55]
'''
```

#### Case B: List is reassigned inside function<br>

Changes won't affect the original list.<br>
*Program to increment the elements of the list passed as parameter*

```
def increment(list2):
    print("ID before assignment:", id(list2))
    list2 = [15, 25, 35, 45, 55]
    print("ID after assignment:", id(list2))
    print("List inside function:", list2)

list1 = [10, 20, 30, 40, 50]
print("ID before function call:", id(list1))
print("Before function call:", list1)
increment(list1)
print("ID after function call:", id(list1))
print("After function call:", list1)

'''
ID before function call: 65565640
Before function call: [10, 20, 30, 40, 50]
ID before assignment: 65565640
ID after assignment: 65565600
List inside function: [15, 25, 35, 45, 55]
ID after function call: 65565640
After function call: [10, 20, 30, 40, 50]
'''
```

---

### List Manipulation (Menu-Driven Program)<br>
*Write a menu driven program to perform various list operations, such as:*
• *Append an element*
• *Insert an element*
• *Append a list to the given list*
• *Modify an existing element*
• *Delete an existing element from its position*
• *Delete an existing element with a given value*
• *Sort the list in ascending order*
• *Sort the list in descending order*
• *Display the list.*

```
myList = [22, 4, 16, 38, 13]
choice = 0

while True:
    print("The list 'myList' has the following elements", myList)
    print("\nL I S T   O P E R A T I O N S")
    print(" 1. Append an element")
    print(" 2. Insert an element at the desired position")
    print(" 3. Append a list to the given list")
    print(" 4. Modify an existing element")
    print(" 5. Delete an existing element by its position")
    print(" 6. Delete an existing element by its value")
    print(" 7. Sort the list in ascending order")
    print(" 8. Sort the list in descending order")
    print(" 9. Display the list")
    print("10. Exit")

    choice = int(input("ENTER YOUR CHOICE (1-10): "))

    if choice == 1:
        element = int(input("Enter the element to be appended: "))
        myList.append(element)
        print("Element appended\n")

    elif choice == 2:
        element = int(input("Enter the element to be inserted: "))
        pos = int(input("Enter the position: "))
        myList.insert(pos, element)
        print("Element inserted\n")

    elif choice == 3:
        newList = eval(input("Enter the elements (comma-separated): "))
        myList.extend(list(newList))
        print("List appended\n")

    elif choice == 4:
        i = int(input("Enter the position of the element to be modified: "))
        if i < len(myList):
            newElement = int(input("Enter the new element: "))
            oldElement = myList[i]
            myList[i] = newElement
            print("Element", oldElement, "modified\n")
        else:
            print("Invalid position")

    elif choice == 5:
        i = int(input("Enter the position of the element to be deleted: "))
        if i < len(myList):
            element = myList.pop(i)
            print("Element", element, "deleted\n")
        else:
            print("Invalid position")

    elif choice == 6:
        element = int(input("Enter the element to be deleted: "))
        if element in myList:
            myList.remove(element)
            print("Element", element, "deleted\n")
        else:
            print("Element not found")

    elif choice == 7:
        myList.sort()
        print("List sorted in ascending order\n")

    elif choice == 8:
        myList.sort(reverse=True)
        print("List sorted in descending order\n")

    elif choice == 9:
        print("The list is:", myList)

    elif choice == 10:
        break

    else:
        print("Invalid choice")
    
    input("Press Enter to continue...")
```

---

### Program to Calculate Average Marks
*A program to calculate average marks of n students using a function where n is entered by the user.*

```
def computeAverage(list1, n):
    total = 0
    for marks in list1:
        total += marks
    average = total / n
    return average

list1 = []
n = int(input("How many students marks you want to enter: "))
for i in range(n):
    marks = int(input(f"Enter marks of student {i+1}: "))
    list1.append(marks)

average = computeAverage(list1, n)
print("Average marks of", n, "students is:", average)

'''
Input:
5
45
89
79
76
55

Output:
Average marks of 5 students is: 68.8
'''
```

---

### Program to Search a Number in List (Linear Search)
*Write a user-defined function to check if a number is present in the list or not. If the number is present, return the position of the number. Print an appropriate message if the number is not present in the list.*

```
def linearSearch(num, list1):
    for i in range(len(list1)):
        if list1[i] == num:
            return i
    return None

list1 = []
maximum = int(input("How many numbers do you want to enter in the list: "))
for i in range(maximum):
    n = int(input())
    list1.append(n)

num = int(input("Enter the number to be searched: "))
result = linearSearch(num, list1)

if result is None:
    print("Number", num, "is not present in the list")
else:
    print("Number", num, "is present at", result + 1, "position")

'''
Input:
5
23
567
12
89
324
12

Output:
Number 12 is present at 3 position
'''
```


