# Function
### Function can be defined as a named group of instructions that accomplish a specific task when it is invoked. 
### Once defined, a function can be called repeatedly from different places of the program without writing all the codes of that function everytime, or it can be called from inside another function, by simply writing the name of the function and passing the required parameters, if any.
<img width="1895" height="895" alt="function_label" src="https://github.com/user-attachments/assets/a72e843d-c1f9-4514-bbd9-630720f0ce9d" />

## code
```
def name(parameter1, parameter2):
    print(parameter1)
    return parameter2

b = name(1,2)
print(b)

```
## The Advantages of Function
• *Increases readability, particularly for longer code
as by using functions, the program is better
organised and easy to understand.* <br>
• *Reduces code length as same code is not required
to be written at multiple places in a program. This
also makes debugging easier*. <br>
• *Increases reusability, as function can be called from
another function or another program. Thus, we can
reuse or build upon already defined functions and
avoid repetitions of writing the same piece of code*. <br>
• *Work can be easily divided among team members
and completed in parallel*. <br>

**A function defined to achieve some task as per the programmer's requirement is called a User Defined Function.**

## Default Parameter
A default value is a value that is predecided and assignedto the parameter when the function call does not have its corresponding argument. 
```
def name(parameter1=5, parameter2=7):
    print(parameter1)
    return parameter2

b = name(1,2)
print(b)
a = name()
print(a)
```

**Note:**
• A function argument can also be an expression, such as
```
mixedFraction(num+5,deno+5)
```
In such a case, the argument is evaluated before calling
the function so that a valid value can be assigned to the
parameter. <br>
• The parameters should be in the same order as that of
the arguments.

## Functions Returning Value
Sometimes we need to send value(s) from the function to its calling function.<br>
This is done using return statement. The return statement does the following:<br>
• returns the control to the calling function.<br>
• return value(s) or None.<br>
## In Python, as per our requirements, we can have the function in either of the following ways:
• Function with no argument and no return value<br>
• Function with no argument and with return value(s)<br>
• Function with argument(s) and no return value<br>
• Function with argument(s) and return value(s)<br>

## Scope of a VarIable
A variable defined inside a function cannot be
accessed outside it. Every variable has a well-defined
accessibility. The part of the program where a
variable is accessible can be defined as the scope
of that variable.<br>
<div align="center">
<img width="597" height="395" alt="image" src="https://github.com/user-attachments/assets/1657472b-037a-44b3-9acd-c3a72ebcb317" />
</div>


**(A) Global Variable** <br>
In Python, a variable that is defined outside any function
or any block is known as a global variable. It can be
accessed in any functions defined onwards. Any change
made to the global variable will impact all the functions
in the program where that variable can be accessed.<br>
**(B) Local Variable** <br>
A variable that is defined inside any function or a block
is known as a local variable. It can be accessed only in
the function or a block where it is defined. It exists only
till the function executes.<br>

**Note:**
• Any modification to global variable is permanent and
affects all the functions where it is used.<br>
• If a variable with the same name as the global variable
is defined inside a function, then it is considered local
to that function and hides the global variable.<br>
• If the modified value of a global variable is to be used
outside the function, then the keyword global should
be prefixed to the variable name in the function.<br>
```
# Global variable
message = "Hello from global!"

def greet():
    # Local variable (only accessible inside this function)
    message = "Hello from local!"
    print("Inside function:", message)

def greet_global():
    global message  # This tells Python to use the global variable
    message = "Changed from inside function using global"
    print("Inside greet_global:", message)

# Calling functions
greet()
print("After greet() call:", message)  # Will still show global message

greet_global()
print("After greet_global() call:", message)  # Global message is changed

```

| Feature                                  | **Global Variable**                                   | **Local Variable**                                        |
| ---------------------------------------- | ----------------------------------------------------- | --------------------------------------------------------- |
| **Scope**                                | Available throughout the program                      | Available only within the function or block where defined |
| **Declared outside or inside function?** | Declared outside all functions                        | Declared inside a function or block                       |
| **Accessibility**                        | Accessible in all functions (if not shadowed)         | Only accessible within the same function                  |
| **Lifetime**                             | Exists until the program ends                         | Exists only while the function is running                 |
| **Modification inside function**         | Must use `global` keyword to modify inside a function | Can be modified directly within the function              |
| **Example**                              | `x = 10` outside any function                         | `x = 5` inside `def my_function():`                       |


**Quick Example**
```
x = 10  # Global variable

def example():
    x = 5  # Local variable
    print(x)  # Prints 5

example()
print(x)  # Prints 10 (global variable remains unchanged)

```

## Python Standard Library
Python has a very extensive
standard library. It is a
collection of many built
in functions that can be
called in the program as
and when required<br>
<img width="1005" height="373" alt="image" src="https://github.com/user-attachments/assets/7731d99f-3d1b-4d0d-8c15-6cf474d78c67" />

**Built-in functions**<br>
Built-in functions are the ready-made functions in
Python that are frequently used in programs.<br>
``` input(), int() and print() ```
are the built-in functions. The set of instructions to be
executed for these built-in functions are already defined
in the python interpreter.

<div align="center">
  <img width="1399" height="738" alt="image" src="https://github.com/user-attachments/assets/aacb5b35-1b5f-4864-8626-ac1afd314c43" />

</div>
<br>
<div align="center">
<strong>Commonly used built-in functions</strong>
</div><br><br>

| **Function** | **Syntax**                             | **Arguments**                                          | **Returns**                                                  | **Example**                                                                                                          | **Output**                      |
| ------------ | -------------------------------------- | ------------------------------------------------------ | ------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------- | ------------------------------- |
| `abs()`      | `abs(x)`                               | x may be an integer or floating-point number           | Absolute value of x                                          | `abs(4)`<br>`abs(-5.7)`                                                                                              | 4<br>5.7                        |
| `divmod()`   | `divmod(x, y)`                         | x and y are integers or floats                         | A tuple: (quotient, remainder)                               | `divmod(7, 2)`<br>`divmod(7.5, 2)`<br>`divmod(-7, 2)`                                                                | (3, 1)<br>(3.0, 1.5)<br>(-4, 1) |
| `max()`      | `max(sequence)`<br>`max(x, y, z, ...)` | x, y, z may be integers, floats, or strings            | Largest value in the sequence or among arguments             | `max([1, 2, 3, 4])`<br>`max("Sincerity")`<br>`max(23, 4, 56)`                                                        | 4<br>'y'<br>56                  |
| `min()`      | `min(sequence)`<br>`min(x, y, z, ...)` | x, y, z may be integers, floats, or strings            | Smallest value in the sequence or among arguments            | `min([1, 2, 3, 4])`<br>`min("Sincerity")`<br>`min(23, 4, 56)`                                                        | 1<br>'S'<br>4                   |
| `pow()`      | `pow(x, y[, z])`                       | x, y, z may be integers or floats. z is optional.      | x raised to the power y.<br>If z is provided: `(x ** y) % z` | `pow(5, 2)`<br>`pow(5.3, 2.2)`<br>`pow(5, 2, 4)`                                                                     | 25.0<br>39.2<br>1               |
| `sum()`      | `sum(x[, num])`                        | x is a numeric sequence (list, tuple); num is optional | Sum of all elements in x. Adds `num` if provided.            | `sum([2, 4, 7, 3])`<br>`sum([2, 4, 7, 3], 3)`<br>`sum((52, 8, 4, 2))`                                                | 16<br>19<br>66                  |
| `len()`      | `len(x)`                               | x can be a sequence (str, list, tuple) or dictionary   | Count of elements in x                                       | `len("Patience")`<br>`len([12, 34, 98])`<br>`len((9, 45))`<br>`len({1:"Anuj", 2:"Razia", 3:"Gurpreet", 4:"Sandra"})` | 8<br>3<br>2<br>4                |


**Module**<br>
While a function is a grouping of instructions, a module
is a grouping of functions.<br>
To use a module, we need to import the module. Once
we import a module, we can directly use all the functions
of that module. The syntax of import statement is as
follows:<br>
```import modulename1 [,modulename2, …]``` <br>
This gives us access to all the functions in the
module(s). To call a function of a module, the function
name should be preceded with the name of the module
with a dot(.) as a separator.
The syntax is as shown below:<br>
```modulename.functionname()```<br>
**(A) Built-in Modules**
Python library has many built-in modules that are really
handy to programmers.<br>
**Commonly used built in modules**
<img width="1179" height="502" alt="image" src="https://github.com/user-attachments/assets/4d1039cc-520e-4f5a-b8c5-b186081837d5" />
**1. Module name : math**<br>
It contains different types of mathematical functions.<br>
Most of the functions in this module return a float value.<br>
```import math```
***Commonly used functions in math module***

| **Function**        | **Syntax**          | **Arguments**                        | **Returns**                            | **Examples**                                                                                     | **Output(s)**                          |
| ------------------- | ------------------- | ------------------------------------ | -------------------------------------- | ------------------------------------------------------------------------------------------------ | -------------------------------------- |
| `math.ceil(x)`      | `math.ceil(x)`      | `x`: int or float                    | Ceiling value of `x`                   | `math.ceil(-9.7)`<br>`math.ceil(9.7)`<br>`math.ceil(9)`                                          | `-9`<br>`10`<br>`9`                    |
| `math.floor(x)`     | `math.floor(x)`     | `x`: int or float                    | Floor value of `x`                     | `math.floor(-4.5)`<br>`math.floor(4.5)`<br>`math.floor(4)`                                       | `-5`<br>`4`<br>`4`                     |
| `math.fabs(x)`      | `math.fabs(x)`      | `x`: int or float                    | Absolute value of `x` (float)          | `math.fabs(6.7)`<br>`math.fabs(-6.7)`<br>`math.fabs(-4)`                                         | `6.7`<br>`6.7`<br>`4.0`                |
| `math.factorial(x)` | `math.factorial(x)` | `x`: positive integer                | Factorial of `x`                       | `math.factorial(5)`                                                                              | `120`                                  |
| `math.fmod(x, y)`   | `math.fmod(x, y)`   | `x`, `y`: int or float               | Remainder of `x / y`, sign of `x`      | `math.fmod(4, 4.9)`<br>`math.fmod(4.9, 4.9)`<br>`math.fmod(-4.9, 2.5)`<br>`math.fmod(4.9, -4.9)` | `4.0`<br>`0.0`<br>`-2.4`<br>`0.0`      |
| `math.gcd(x, y)`    | `math.gcd(x, y)`    | `x`, `y`: positive integers          | Greatest common divisor of `x` and `y` | `math.gcd(10, 2)`                                                                                | `2`                                    |
| `math.pow(x, y)`    | `math.pow(x, y)`    | `x`, `y`: int or float               | `x` raised to power `y` (float)        | `math.pow(3, 2)`<br>`math.pow(4, 2.5)`<br>`math.pow(6.5, 2)`<br>`math.pow(5.5, 3.2)`             | `9.0`<br>`32.0`<br>`42.25`<br>`233.97` |
| `math.sqrt(x)`      | `math.sqrt(x)`      | `x`: positive int or float           | Square root of `x`                     | `math.sqrt(144)`<br>`math.sqrt(0.64)`                                                            | `12.0`<br>`0.8`                        |
| `math.sin(x)`       | `math.sin(x)`       | `x`: angle in radians (int or float) | Sine of `x`                            | `math.sin(0)`<br>`math.sin(6)`                                                                   | `0.0`<br>`-0.279`                      |

<br>

**2. Module name : random**<br>
This module contains functions that are used for
generating random numbers.<br>
```import random```
***Commonly used functions in random module***<br>
| **Function**             | **Syntax**               | **Arguments**                                       | **Returns**                                  | **Examples**                                                                  | **Output**          |
| ------------------------ | ------------------------ | --------------------------------------------------- | -------------------------------------------- | ----------------------------------------------------------------------------- | ---------------------- |
| `random.random()`        | `random.random()`        | No arguments                                        | Random float in range `[0.0, 1.0)`           | `random.random()`                                                             | `0.65333522` |
| `random.randint(x, y)`   | `random.randint(x, y)`   | `x`, `y`: integers where `x <= y`                   | Random integer in range `[x, y]` (inclusive) | `random.randint(3, 7)`<br>`random.randint(-3, 5)`<br>`random.randint(-5, -3)` | `4`<br>`1`<br>`-5`     |
| `random.randrange(y)`    | `random.randrange(y)`    | `y`: positive integer (stop value)                  | Random integer from `0` to `y - 1`           | `random.randrange(5)`                                                         | `4`                    |
| `random.randrange(x, y)` | `random.randrange(x, y)` | `x`, `y`: positive integers (start and stop values) | Random integer from `x` to `y - 1`           | `random.randrange(2, 7)`                                                      | `2`                    |


<br>

**3. Module name : statistics** <br>
This module provides functions for calculating statistics
of numeric (Real-valued) data.<br>
```import statistics```
***Commonly used functions in statistics module***<br>
| **Function**           | **Syntax**             | **Arguments**                       | **Returns**                            | **Example(s)**                                                                       | **Output(s)**   |
| ---------------------- | ---------------------- | ----------------------------------- | -------------------------------------- | ------------------------------------------------------------------------------------ | --------------- |
| `statistics.mean(x)`   | `statistics.mean(x)`   | `x`: numeric sequence (list, tuple) | Arithmetic mean (average)              | `statistics.mean([11, 24, 32, 45, 51])`                                              | `32.6`          |
| `statistics.median(x)` | `statistics.median(x)` | `x`: numeric sequence               | Median (middle value)                  | `statistics.median([11, 24, 32, 45, 51])`                                            | `32`            |
| `statistics.mode(x)`   | `statistics.mode(x)`   | `x`: sequence (numbers or strings)  | Mode (most frequently occurring value) | `statistics.mode([11, 24, 11, 45, 11])`<br>`statistics.mode(("red", "blue", "red"))` | `11`<br>`'red'` |

<br>

**Note:** <br>
• ```import``` statement can be written anywhere in the
program<br>
• Module must be imported only once
• In order to get a list of modules available in Python, we
can use the following statement:<br>
```help("module")```<br>
• To view the content of a module say math, type the
following:<br>
```help("math")```
• The modules in the standard library can be found in
the Lib folder of Python.<br>

**(B) From Statement** <br>
Instead of loading all the functions into memory by
importing a module, from statement can be used to
access only the required functions from a module. It
loads only the specified function(s) instead of all the
functions in a module.
Its syntax is
```from modulename import functionname [,functionname,...]``` <br>
To use the function when imported using "from
statement" we do not need to precede it with the module
name.

```
from random import random
random() #Function called withoutthe module name
```

**Output**
0.48288328923583423
