# Exception Handling in Python
In Python, exceptions are errors that
get triggered automatically. However, exceptions
can be forcefully triggered and handled through
program code.


## Syntax Errors
Syntax errors are detected when we have not
followed the rules of the particular programming
language while writing a program. These errors are
also known as parsing errors. On encountering a
syntax error, the interpreter does not execute the
program unless we rectify the errors, save and
rerun the program.<br>

**Example**

<img width="982" height="775" alt="image" src="https://github.com/user-attachments/assets/f1425ac0-97e9-4274-869e-4a03c2b5ac68" />

## Exceptions
Even if a statement or expression is syntactically
correct, there might arise an error during its execution.
For example:<br>
• trying to open a file that does not exist,<br>
• division by zero <br>
and so on.<br>
Such types of errors might
disrupt the normal execution of the program and are
called ***exceptions***.<br>
**An exception is a Python object that represents an error. When an error occurs during the execution of a program, an exception is said to have been raised.**<br>

### Built-in Exceptions
Commonly occurring exceptions are usually defined
in the compiler/interpreter. These are called built-in
exceptions.<br>
Python’s standard library is an extensive collection
of built-in exceptions that deals with the commonly
occurring errors (exceptions) by providing the
standardized solutions for such errors. On the occurrence
of any built-in exception, the appropriate exception
handler code is executed which displays the reason
along with the raised exception name.<br>

**Built-in Exceptions in Python**


| **S. No.** | **Name of the Built-in Exception**          | **Explanation**                                                                                                 |
| :--------: | :------------------------------------------ | :-------------------------------------------------------------------------------------------------------------- |
|    **1**   | `SyntaxError`                               | Raised when there is an error in the syntax of the Python code.                                                 |
|    **2**   | `ValueError`                                | Raised when a built-in operation or function receives an argument of the correct type but inappropriate value.  |
|    **3**   | `IOError` *(or `OSError` in modern Python)* | Raised when a file operation (like opening or reading) fails — e.g., the file doesn’t exist or can’t be opened. |
|    **4**   | `KeyboardInterrupt`                         | Raised when the user interrupts program execution (e.g., pressing **Ctrl+C**, **Delete**, or **Esc**).          |
|    **5**   | `ImportError`                               | Raised when the Python interpreter can’t find the module or object being imported.                              |
|    **6**   | `EOFError`                                  | Raised when the `input()` function hits end-of-file (EOF) without reading any data.                             |
|    **7**   | `ZeroDivisionError`                         | Raised when a number is divided by zero.                                                                        |
|    **8**   | `IndexError`                                | Raised when a sequence index (like a list or tuple index) is out of range.                                      |
|    **9**   | `NameError`                                 | Raised when a variable or function name is not defined.                                                         |
|   **10**   | `IndentationError`                          | Raised when code is not properly indented according to Python’s rules.                                          |
|   **11**   | `TypeError`                                 | Raised when an operation or function is applied to an object of inappropriate type.                             |
|   **12**   | `OverflowError`                             | Raised when the result of an arithmetic operation exceeds the allowed numeric limit.                            |


***Example***
```
# 1. SyntaxError
try:
    eval('x === 1')  # Invalid Python syntax
except SyntaxError as e:
    print("Caught SyntaxError:", e)

# 2. ValueError
try:
    int("abc")  # Cannot convert string to int
except ValueError as e:
    print("Caught ValueError:", e)

# 3. IOError / OSError
try:
    with open("non_existent_file.txt", "r") as f:
        f.read()
except IOError as e:
    print("Caught IOError:", e)

# 4. KeyboardInterrupt
# Can't reliably simulate in code; usually occurs when user presses Ctrl+C
# We'll simulate with manually raising it
try:
    raise KeyboardInterrupt
except KeyboardInterrupt as e:
    print("Caught KeyboardInterrupt:", e)

# 5. ImportError
try:
    import non_existent_module
except ImportError as e:
    print("Caught ImportError:", e)

# 6. EOFError
# Simulate EOFError by calling input() with empty input via StringIO
import sys
from io import StringIO
try:
    sys.stdin = StringIO('')  # Empty input simulates EOF
    input()
except EOFError as e:
    print("Caught EOFError:", e)
finally:
    sys.stdin = sys.__stdin__

# 7. ZeroDivisionError
try:
    1 / 0
except ZeroDivisionError as e:
    print("Caught ZeroDivisionError:", e)

# 8. IndexError
try:
    lst = [1, 2, 3]
    lst[5]
except IndexError as e:
    print("Caught IndexError:", e)

# 9. NameError
try:
    print(undefined_variable)
except NameError as e:
    print("Caught NameError:", e)

# 10. IndentationError
try:
    exec('def func():\nprint("hello")')  # Missing indentation
except IndentationError as e:
    print("Caught IndentationError:", e)

# 11. TypeError
try:
    'string' + 5  # Cannot add string and int
except TypeError as e:
    print("Caught TypeError:", e)

# 12. OverflowError
import math
try:
    math.exp(1000)  # Exceeds numeric limit
except OverflowError as e:
    print("Caught OverflowError:", e)

```

### Raising Exceptions
Each time an error is detected in a program, the Python
interpreter raises (throws) an exception. Exception
handlers are designed to execute when a specific
exception is raised. Programmers can also forcefully
raise exceptions in a program using the raise and assert
statements. Once an exception is raised, no further
statement in the current block of code is executed.

### The raise Statement
The raise statement can be used to throw an exception.
The syntax of raise statement is:
```
raise exception-name[(optional argument)]
```
The argument is generally a string that is displayed
when the exception is raised.<br>

**Note:** In this case, the user has only raised the exception but
has not displayed any error message explicitly.

### The assert Statement
An assert statement in Python is used to test an
expression in the program code. If the result after testing
comes false, then the exception is raised. This statement
is generally used in the beginning of the function or after
a function call to check for valid input. The syntax for
assert statement is:

```
assert Expression[,arguments]
```
**Example** 
```
def negativecheck(number):
    # Assert to check if the number is non-negative
    assert number >= 0, "OOPS... Negative Number"
    return number * number

# Testing the function
print(negativecheck(100))   # This should print 10000
print(negativecheck(-350))  # This will raise AssertionError

```

In the code, the assert statement checks for the
value of the variable number. In case the number gets
a negative value, AssertionError will be thrown, and
subsequent statements will not be executed. Hence,
on passing a negative value (-350) as an argument, it
results in AssertionError and displays the message
“OOPS…. Negative Number”.<br>

## Handling Exceptions
Each and every exception has to be handled by the
programmer to avoid the program from crashing
abruptly. This is done by writing additional code in
a program to give proper messages or instructions to
the user on encountering an exception. This process is
known as ***exception handling***.<br>

### Need for Exception Handling

It is a useful technique that helps
in capturing runtime errors and handling them so as to
avoid the program getting crashed. Following are some
of the important points regarding exceptions and their
handling:<br>
• Python categorises exceptions into distinct types so
that specific exception handlers (code to handle that
particular exception) can be created for each type.<br>
• Exception handlers separate the main logic of the
program from the error detection and correction
code. The segment of code where there is any
possibility of error or exception, is placed inside one
block. The code to be executed in case the exception
has occurred, is placed inside another block. These
statements for detection and reporting the exception
do not affect the main logic of the program.<br>
• The compiler or interpreter keeps track of the exact
position where the error has occurred.<br>
• Exception handling can be done for both user-defined
and built-in exceptions.<br>

### Process of Handling Exception
- When an error occurs, Python creates an exception object containing information about the error (type, file name, position).
- This object is handed over to the runtime system — a process called throwing an exception.
- Control jumps to an exception handler, skipping the remaining statements in the current block.
- The runtime searches the call stack for a suitable exception handler, starting from the method where the error occurred and moving up hierarchically.
- When a suitable handler is found, it is executed — this is called catching the exception.
- If no handler is found, the program execution stops.


***Steps of handling exception***
<img width="881" height="940" alt="image" src="https://github.com/user-attachments/assets/e12e3bfe-ce10-458e-885d-078879f77f5b" />

### Catching Exceptions

- An exception is caught when code designed to handle it is executed.
- Suspicious code that might raise an exception is placed inside a try block.
- The except block contains code to handle the possible exceptions.
- If an exception occurs, execution of the try block stops and control transfers to the except block.
- Syntax:
```
    try:
        # code that may raise an exception
    except ExceptionType:
        # code to handle the exception
```

**Example**
```
print("Practicing for try block")

try:
    numerator = 50
    denom = int(input("Enter the denominator: "))
    quotient = numerator / denom
    print("Division performed successfully. Quotient is:", quotient)
except ZeroDivisionError:
    print("Denominator as ZERO.... not allowed")

print("OUTSIDE try..except block")

```
```
print("Handling multiple exceptions")

try:
    numerator = 50
    denom = int(input("Enter the denominator: "))
    print(numerator / denom)
    print("Division performed successfully")
except ZeroDivisionError:
    print("Denominator as ZERO is not allowed")
except ValueError:
    print("Only INTEGERS should be entered")

```
```
print("Handling exceptions without naming them")

try:
    numerator = 50
    denom = int(input("Enter the denominator: "))
    quotient = numerator / denom
    print("Division performed successfully. Quotient is:", quotient)
except ValueError:
    print("Only INTEGERS should be entered")
except:
    print("OOPS.....SOME EXCEPTION RAISED")

```
### try...except…else clause


We can put an optional else clause along with the
try...except clause. An except block will be executed only if some exception is raised in the try block. But if
there is no error then none of the except blocks will
be executed. In this case, the statements inside the
else clause will be executed.

```
print("Handling exception using try...except...else")

try:
    numerator = 50
    denom = int(input("Enter the denominator: "))
    quotient = numerator / denom
    print("Division performed successfully")
except ZeroDivisionError:
    print("Denominator as ZERO is not allowed")
except ValueError:
    print("Only INTEGERS should be entered")
else:
    print("The result of division operation is", quotient)

```

### Finally Clause
The try statement in Python can also have an optional
finally clause. The statements inside the finally block
are always executed regardless of whether an exception
has occurred in the try block or not. It is a common
practice to use `finally` clause while working with files
to ensure that the file object is closed. If used, `finally`
should always be placed at the end of `try` clause, after
all `except` blocks and the `else` block.

**Syntax**
```
try:
    # code that may raise an exception
except SomeException:
    # code that runs if an exception occurs
finally:
    # code that always runs

```
```
print("Handling exception using try...except...else...finally")

try:
    numerator = 50
    denom = int(input("Enter the denominator: "))
    quotient = numerator / denom
    print("Division performed successfully")
except ZeroDivisionError:
    print("Denominator as ZERO is not allowed")
except ValueError:
    print("Only INTEGERS should be entered")
else:
    print("The result of division operation is", quotient)
finally:
    print("OVER AND OUT")

```




### Recovering and continuing with finally clause
If an error has been detected in the try block and the
exception has been thrown, the appropriate except
block will be executed to handle the error. But if the
exception is not handled by any of the except clauses,
then it is re-raised after the execution of the finally
block.

```
print (" Practicing for try block")
try:
numerator=50
denom=int(input("Enter the denominator"))
quotient=(numerator/denom)
print ("Division performed successfully")
except ZeroDivisionError:
print ("Denominator as ZERO is not allowed")
else:
print ("The result of division operation is ", quotient)
finally:
print ("OVER AND OUT")
```


