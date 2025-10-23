# Strings
String is a sequence which is made up of one or more
UNICODE characters. Here the character can be a letter,
digit, whitespace or any other symbol. A string can be
created by enclosing one or more characters in single,
double or triple quote.
```
str1 = 'Hello World!'
str2 = "Hello World!"
str3 = """Hello World!"""
str4 = '''Hello World!'''
```
**Accessing Characters in a String**<br>
Each individual character in a string can be accessed
using a technique called indexing. The index specifies
the character to be accessed in the string and is written
in square brackets ([ ]). The index of the first character
(from left) in the string is 0 and the last character is n-1
where n is the length of the string. If we give index value
out of this range then we get an IndexError. The index
must be an integer (positive, zero or negative).<br>
```
# Define a string
str1 = "Python"

# Access characters using positive indexing
print(str1[0])   # Output: P (1st character)
print(str1[3])   # Output: h (4th character)
print(str1[5])   # Output: n (6th and last character)

# Access characters using negative indexing
print(str1[-1])  # Output: n (last character)
print(str1[-6])  # Output: P (first character)

# Using expression as index (must be integer)
print(str1[2 + 1])  # Output: h (index 3)

# Invalid index: Out of range
print(str1[10])     # ❌ Raises IndexError

# Invalid index: Not an integer
print(str1[1.5])    # ❌ Raises TypeError

```

**Indexing of characters in string 'Hello World!'**
| Positive Indices  | 0   | 1   | 2   | 3  | 4  | 5  | 6  | 7  | 8  | 9  | 10 | 11 |
| ----------------- | --- | --- | --- | -- | -- | -- | -- | -- | -- | -- | -- | -- |
| String Characters | H   | e   | l   | l  | o  |    | W  | o  | r  | l  | d  | !  |
| Negative Indices  | -12 | -11 | -10 | -9 | -8 | -7 | -6 | -5 | -4 | -3 | -2 | -1 |


**Note:** : An inbuilt function len() in Python returns the length
of the string that is passed as parameter. For example,
the length of string str1 = 'Hello World!' is 12.<br>
<strong>Remember</strong> that len returns the number of characters in string not the last index of the string:<br>
As you can see in above example that last index of the string is 11 and len would return 12 (which is also equal to index of first character in negative indices.)
<br>


**String is Immutable**<br>
A string is an immutable data type. It means that
the contents of the string cannot be changed after it
has been created. An attempt to do this would lead to
an error.
```
str1 = "Hello World!"
#if we try to replace character 'e' with 'a' 
str1[1] = 'a'
#TypeError: 'str' object does not support item assignment
```

**String Operations**<br>
Python allows certain operations on string data type,
such as concatenation, repetition, membership and
slicing.<br>


**Concatenation**<br>
To concatenate means to join. Python allows us to join
two strings using concatenation operator plus which is
denoted by symbol +.<br>


```
str1 = 'Hello' #First string
str2 = 'World!' #Second string
print(str1 + str2) #Concatenated strings
#'HelloWorld!'
#str1 and str2 remain same
print(str1) #after this operation.
#'Hello'
print(str2)
#'World!'
```

**Repetition**<br>
Python allows us to repeat the given string using
repetition operator which is denoted by symbol *.<br>

```
#assign string 'Hello' to str1
str1 = 'Hello'
#repeat the value of str1 2 times
print(str1 * 2)
#'HelloHello'
#repeat the value of str1 5 times
print(str1 * 5)
#'HelloHelloHelloHelloHello'
```

**Note:** str1 still remains the same after the use of
repetition operator.<br>

**Membership**<br>
Python has two membership operators `in` and `not in` . The ' in ' operator takes two strings and returns
True if the first string appears as a substring in the
second string, otherwise it returns False.<br>
```
str1 = 'Hello World!'
print('W' in str1)
#True
print('Wor' in str1)
#True
print('My' in str1)
#False
```
The ` not in ` operator also takes two strings and
returns True if the first string does not appear as a
substring in the second string, otherwise returns False.<br>
```
str1 = 'Hello World!'
print('My' not in str1)
#True
print('Hello' not in str1)
#False
```

**Slicing**<br>
In Python, to access some part of a string or substring,
we use a method called slicing. This can be done by
specifying an index range. Given a string str1, the
slice operation str1[n:m] returns the part of the string
str1 starting from index n (inclusive) and ending at m
(exclusive)<br>
```
str1 = 'Hello World!'
##gives substring starting from index 1 to 4
print(str1[1:5])
#'ello'
#gives substring starting from 7 to 9
print(str1[7:10])
#'orl'
#index that is too big is truncated down to
#the end of the string
print(str1[3:20])
#'lo World!'
#first index > second index results in an
#empty '' string
print(str1[7:2])
#this would print an empty line
print("This is the end")
```
<br>


*If the first index is not mentioned, the slice starts from index.*
#gives substring from index 0 to 4
```
str1[:5]
'Hello'
```
*If the second index is not mentioned, the slicing is done till the length of the string.*
#gives substring from index 6 to end
```
str1[6:]
'World!'
```
*The slice operation can also take a third index that specifies the ‘step size’. For example, str1[n:m:k], means every k th character has to be extracted from the string str1 starting from n and ending at m-1. By default, the step size is one.*
```
str1[0:10:2]
'HloWr'
```
```
str1[0:10:3]
'HlWl'
```
*Negative indexes can also be used for slicing.*
```
#characters at index -6,-5,-4,-3 and -2 are
#sliced
str1[-6:-1]
'World'
```
*If we ignore both the indexes and give step size as -1*
```
#str1 string is obtained in the reverse order
str1[::-1]
'!dlroW olleH'
```

**Traversing a String**<br>
We can access each character of a string or traverse a
string using for loop and while loop.<br>
**(A) String Traversal Using for Loop:**<br>
```
str1 = 'Hello World!'
for ch in str1:
    print(ch,end = '')
#Hello World! #output of for loop
```
In the above code, the loop starts from the first
character of the string str1 and automatically ends
when the last character is accessed.<br>
**(B) String Traversal Using while Loop:**
```
str1 = 'Hello World!'
index = 0
#len(): a function to get length of string

while index < len(str1):
    print(str1[index],end = '')
    index += 1
#Hello World! #output of while loop

```
Here while loop runs till the condition index
< len(str) is True, where index varies from 0 to
len( st r1) -1.<br>

**StrIng MethodS and Built - In Functions**<br>


| **Method**               | **Description**                                                                | **Example**                                                                                                                                                                                                                                                       |
| ------------------------ | ------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `len()`                  | Returns the length of the given string.                                        | `str1 = 'Hello World!' `<br>` len(str1) `<br>`# 12 `                                                                                                                                                                                                            |
| `title()`                | Converts first letter of every word to uppercase, rest to lowercase.           | `str1 = 'hello WORLD!' `<br>` str1.title() `<br>`# 'Hello World!' `                                                                                                                                                                                             |
| `lower()`                | Converts all characters to lowercase.                                          | `str1 = 'hello WORLD!' `<br>` str1.lower() `<br>`# 'hello world!' `                                                                                                                                                                                             |
| `upper()`                | Converts all characters to uppercase.                                          | `str1 = 'hello WORLD!' `<br>` str1.upper() `<br>`# 'HELLO WORLD!' `                                                                                                                                                                                             |
| `count(str, start, end)` | Returns the number of times `str` occurs between `start` and `end` (if given). | `str1 = 'Hello World! Hello Hello' `<br>` str1.count('Hello', 12, 25) `<br>`# 2 `<br>` str1.count('Hello') `<br>`# 3 `                                                                                                                                                   |
| `find(str, start, end)`  | Returns index of first occurrence of `str` or -1 if not found.                 | `str1 = 'Hello World! Hello Hello' `<br>` str1.find('Hello', 10, 20) `<br>`# 13 `<br>` str1.find('Hello', 15, 25) `<br>`# 19 `<br>` str1.find('Hello') `<br>`# 0 `<br>` str1.find('Hee') `<br>`# -1 `                                                                                      |
| `index(str, start, end)` | Like `find()`, but raises ValueError if not found.                             | `str1 = 'Hello World! Hello Hello' `<br>` str1.index('Hello') `<br>`# 0 `<br>` str1.index('Hee') `<br>`# ValueError: substring not found `                                                                                                                               |
| `endswith()`             | Returns True if string ends with given substring.                              | `str1 = 'Hello World!' `<br>` str1.endswith('World!') `<br>`# True `<br>` str1.endswith('!') `<br>`# True `<br>` str1.endswith('lde') `<br>`# False `                                                                                                                             |
| `startswith()`           | Returns True if string starts with given substring.                            | `str1 = 'Hello World!' `<br>` str1.startswith('He') `<br>`# True `<br>` str1.startswith('Hee') `<br>`# False `                                                                                                                                                           |
| `isalnum()`              | Returns True if all characters are alphanumeric.                               | `str1 = 'HelloWorld' `<br>` str1.isalnum() `<br>`# True `<br>` str1 = 'HelloWorld2' `<br>` str1.isalnum() `<br>`# True `<br>` str1 = 'HelloWorld!!' `<br>` str1.isalnum() `<br>`# False `                                                                                               |
| `islower()`              | Returns True if all letters are lowercase.                                     | `str1 = 'hello world!' `<br>` str1.islower() `<br>`# True `<br>` str1 = 'hello 1234' `<br>` str1.islower() `<br>`# True `<br>` str1 = 'hello ??' `<br>` str1.islower() `<br>`# True `<br>` str1 = '1234' `<br>` str1.islower() `<br>`# False `<br>` str1 = 'Hello World!' `<br>` str1.islower() `<br>`# False ` |
| `isupper()`              | Returns True if all letters are uppercase.                                     | `str1 = 'HELLO WORLD!' `<br>` str1.isupper() `<br>`# True `<br>` str1 = 'HELLO 1234' `<br>` str1.isupper() `<br>`# True `<br>` str1 = 'HELLO ??' `<br>` str1.isupper() `<br>`# True `<br>` str1 = '1234' `<br>` str1.isupper() `<br>`# False `<br>` str1 = 'Hello World!' `<br>` str1.isupper() `<br>`# False ` |
| `isspace()`              | Returns True if string has only whitespace characters.                         | `str1 = ' \n \t \r' `<br>` str1.isspace() `<br>`# True `<br>` str1 = 'Hello \n' `<br>` str1.isspace() `<br>`# False `                                                                                                                                                       |
| `istitle()`              | Returns True if string is in title case.                                       | `str1 = 'Hello World!' `<br>` str1.istitle() `<br>`# True `<br>` str1 = 'hello World!' `<br>` str1.istitle() `<br>`# False `                                                                                                                                                |
| `lstrip()`               | Removes whitespace from the left side.                                         | `str1 = '   Hello World! ' `<br>` str1.lstrip() `<br>`# 'Hello World! ' `                                                                                                                                                                                       |
| `rstrip()`               | Removes whitespace from the right side.                                        | `str1 = ' Hello World!   ' `<br>` str1.rstrip() `<br>`# ' Hello World!' `                                                                                                                                                                                       |
| `strip()`                | Removes whitespace from both sides.                                            | `str1 = ' Hello World! ' `<br>` str1.strip() `<br>`# 'Hello World!' `                                                                                                                                                                                           |
| `replace(old, new)`      | Replaces all occurrences of `old` with `new`.                                  | `str1 = 'Hello World!' `<br>` str1.replace('o', '*') `<br>`# 'Hell* W*rld!' `<br>` str1.replace('World', 'Country') `<br>`# 'Hello Country!' `<br>` str1 = 'Hello World! Hello' `<br>` str1.replace('Hello', 'Bye') `<br>`# 'Bye World! Bye' `                                       |
| `join()`                 | Joins characters using a separator.                                            | `str1 = 'HelloWorld!' `<br>` str2 = '-' `<br>` str2.join(str1) `<br>`# 'H-e-l-l-o-W-o-r-l-d-!' `                                                                                                                                                                   |
| `partition(sep)`         | Splits string at first occurrence of `sep` into a tuple: (before, sep, after). | `str1 = 'India is a Great Country' `<br>` str1.partition('is') `<br>`# ('India ', 'is', ' a Great Country') `<br>` str1.partition('are') `<br>`# ('India is a Great Country', '', '') `                                                                                  |
| `split(sep)`             | Splits string into list of substrings.                                         | `str1 = 'India is a Great Country' `<br>` str1.split() `<br>`# ['India', 'is', 'a', 'Great', 'Country'] `<br>` str1.split('a') `<br>`# ['Indi', ' is ', ' Gre', 't Country'] `                                                                                           |





**Handling Strings**

*Write a program with a user defined function to count the number of times a character (passed as argument) occurs in the given string.*
```
#Function to count the number of times a character occurs in a
#string
def charCount(ch,st):
count = 0
for character in st:
if character == ch:
count += 1
return count
#end of function
st = input("Enter a string: ")
ch = input("Enter the character to be searched: ")
count = charCount(ch,st)
print("Number of times character",ch,"occurs in the string
is:",count)
'''
Output:
Enter a string: Today is a Holiday
Enter the character to be searched: a
Number of times character a occurs in the string is: 3
'''
```
*Write a program with a user defined function with string as a parameter which replaces all vowels in the string with '*'.*
```
#Function to replace all vowels in the string with '*'
def replaceVowel(st):
#create an empty string
newstr = ''
for character in st:
#check if next character is a vowel
if character in 'aeiouAEIOU':
#Replace vowel with *
newstr += '*'
else:
newstr += character
return newstr
#end of function
st = input("Enter a String: ")
st1 = replaceVowel(st)
print("The original String is:",st)
print("The modified String is:",st1)
'''
Output:
Enter a String: Hello World
The original String is: Hello World
The modified String is: H*ll* W*rld
'''
```
*Write a program to input a string from the user and print it in the reverse order without creating a new string.*
```

#Program to display string in reverse order
st = input("Enter a string: ")
for i in range(-1,-len(st)-1,-1):
print(st[i],end='')
'''
Output:
Enter a string: Hello World
dlroW olleH
'''
```
*Write a program which reverses a string passed as parameter and stores the reversed string in a new string. Use a user defined function for reversing the string.*
```
#Program 8-4
#Function to reverse a string
def reverseString(st):
newstr = '' #create a new string
length = len(st)
for i in range(-1,-length-1,-1):
newstr += st[i]
return newstr
#end of function
st = input("Enter a String: ")
st1 = reverseString(st)
print("The original String is:",st)
print("The reversed String is:",st1)
'''
Output:
Enter a String: Hello World
The original String is: Hello World
The reversed String is: dlroW olleH
'''
```
*Write a program using a user defined function to check if a string is a palindrome or not. (A string is called palindrome if it reads same backwards as forward. For example, Kanak is a palindrome.)*
```
#Function to check if a string is palindrome or not
def checkPalin(st):
i = 0
j = len(st) - 1
while(i <= j):
if(st[i] != st[j]):
return False
i += 1
j -= 1
return True
#end of function
st = input("Enter a String: ")
result = checkPalin(st)
if result == True:
print("The given string",st,"is a palindrome")
else:
print("The given string",st,"is not a palindrome")
'''
Output 1:
Enter a String: kanak
The given string kanak is a palindrome
Output 2:
Enter a String: computer
The given string computer is not a palindrome
'''
```
