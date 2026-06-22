## 1. What is Python?
Answer: Python is a high-level, interpreted, object-oriented, and dynamically typed programming language. It is easy to learn and supports multiple programming paradigms such as procedural, object-oriented, and functional programming.

Features:
- Easy syntax
- Cross-platform
- Large standard library
- Open source
- Automatic memory management

## 2. What are the key differences between Python 2 and Python 3?
  
| Python 2             | Python 3             |
| -------------------- | ---------------------- |
| print statement      | print() function       |
| xrange()             | range()                |
| Less Unicode support | Better Unicode support |
| No longer supported  | Currently supported    |

Example:
*Python 2*
print "Hello"

*Python 3*
print("Hello")

## what is variable ??
 A variable is a container that stores data values in memory and can be reused throughout the program.

you assign a value to it using the = operator.
ex:- 
name = "Vinod"
age = 25
salary = 50000.50

## Multiple Variable Assignment
Assign multiple values

a, b, c = 10, 20, 30

print(a)
print(b)
print(c)      //output 10 20 30

## Assign same value to multiple variables

x = y = z = 100

print(x, y, z)         //output  100 100 100

## Checking Variable Type

Use the type() function.

age = 25

print(type(age))

## Local and Global Variables

## Local Variable

A local variable is declared inside a function or block and can only be accessed within that function or block.

def greet():

    message = "Hello"  # Local variable

    print(message)

greet()
*print(message)  # Error: message is not accessible here*

## Characteristics:

- Declared inside a function/block.
- Accessible only within that function/block.
- Exists only while the function is executing.

## Global Variable

A global variable is declared outside all functions and can be accessed from any part of the program.

message = "Hello"  # Global variable

def greet():

    print(message)

greet()

print(message)

## Comparison

| Feature       | Local Variable                 | Global Variable              |
| ------------- | ------------------------------ | ---------------------------- |
| Declaration   | Inside a function/block        | Outside all functions        |
| Scope         | Only within the function/block | Entire program               |
| Lifetime      | Until function ends            | Throughout program execution |
| Accessibility | Limited                        | Wide                         |


## Operators in Python

Operators are special symbols that perform operations on variables and values.

## Arithmetic Operators

Used for mathematical calculations.

| Operator | Description         | Example       |
| -------- | ------------------- | ------------- |
| `+`      | Addition            | `5 + 3 = 8`   |
| `-`      | Subtraction         | `5 - 3 = 2`   |
| `*`      | Multiplication      | `5 * 3 = 15`  |
| `/`      | Division            | `5 / 2 = 2.5` |
| `//`     | Floor Division      | `5 // 2 = 2`  |
| `%`      | Modulus (Remainder) | `5 % 2 = 1`   |
| `**`     | Exponent            | `5 ** 2 = 25` |

## Comparison (Relational) Operators

Used to compare values.

| Operator | Meaning                  |
| -------- | ------------------------ |
| `==`     | Equal to                 |
| `!=`     | Not equal to             |
| `>`      | Greater than             |
| `<`      | Less than                |
| `>=`     | Greater than or equal to |
| `<=`     | Less than or equal to    |

## Assignment Operators

Used to assign values.

| Operator | Example  | Equivalent To |
| -------- | -------- | ------------- |
| `=`      | `x = 5`  | Assign 5      |
| `+=`     | `x += 2` | `x = x + 2`   |
| `-=`     | `x -= 2` | `x = x - 2`   |
| `*=`     | `x *= 2` | `x = x * 2`   |
| `/=`     | `x /= 2` | `x = x / 2`   |

## Logical Operators
Used to combine conditions.

| Operator | Description                            |
| -------- | -------------------------------------- |
| `and`    | True if both conditions are True       |
| `or`     | True if at least one condition is True |
| `not`    | Reverses the result                    |

a = 10

b = 5

print(a > 5 and b > 2)  # True

print(a < 5 or b > 2)   # True

print(not(a > 5))       # False


## Membership Operators

Used to check if a value exists in a sequence.

| Operator | Description          |
| -------- | -------------------- |
| `in`     | Value exists         |
| `not in` | Value does not exist |

fruits = ["apple", "banana", "mango"]

print("apple" in fruits)      # True
print("orange" not in fruits) # True

## Identity Operators

Used to compare object memory locations.

| Operator | Description      |
| -------- | ---------------- |
| `is`     | Same object      |
| `is not` | Different object |

x = [1, 2, 3]

y = x

z = [1, 2, 3]

print(x is y)      # True

print(x is z)      # False

print(x == z)      # True

# Bitwise Operators

Work on binary numbers.

| Operator | Description |    |
| -------- | ----------- | -- |
| `&`      | AND         |    |
| `        | `           | OR |
| `^`      | XOR         |    |
| `~`      | NOT         |    |
| `<<`     | Left Shift  |    |
| `>>`     | Right Shift |    |



## 3.What are Python Data Types? (Definition)
Ans: Python Data Types are classifications that specify the type of value a variable can store and determine the operations that can be performed on that value.

like numbers, strings, list, dictionaries, etc.

## Built-in data types:
- int
- float
- str
- bool
- list
- tuple
- set
- dict

*Python is a dynamically typed language, which means you don't need to declare the data type explicitly.*

## Built-in Python Data Types (Overview)

- Numeric types:  int, float, complex.
- equence types:  str, list, tuple, range.
- Mapping type:   dict (key-value pairs).
- Set types:      set, frozenset (unique values).
- Boolean type:   bool (True or False).
- None type:      NoneType (no value).

## Numeric Data Types:- Used to store numerical values.

# Integer (int):- web con store number
Features:-
- Positive and negative numbers
- No decimal point
- Unlimited size in Python

## Complex (complex)

Stores complex numbers.
Example:-
a + bj

x = 3 + 4j
print(type(x))

Accessing parts:

- print(x.real)
- print(x.imag)

# String Data Type (str)
ans:- A string is a sequence of characters enclosed in quotes.

Example:- 
- print(type(name))   //type check
# Concatenation
  first = "Hello"

  second = "World"

  print(first + " " + second)       //output->  hello world

  # Repetition

  print("Python " * 3)     //output->   python python python

  # Indexing
  text = "Python"

   print(text[0])          //output->  p

  ## Slicing
  print(text[0:3])       //output->  pyt 

  # What is bytes in Python?
  bytes is a built-in data type used to store binary data

  A bytes object is immutable, which means its values cannot be changed after creation.

  bytes is an immutable binary data type in Python used to store sequences of bytes. It is commonly used for file handling, image processing, and network communication. Once created, a bytes object cannot be modified.

Example:-
  data = b"Hello"

  print(data)

  print(type(data))        /// b'Hello'  <class 'bytes'>

## Why is b Used?

The prefix b tells Python that the data should be stored as bytes instead of a normal string.

Examle:-

text = "Hello"     # String

data = b"Hello"    # Bytes

## Access Bytes

data = b"Hello"

print(data[0])            /// out   72 is the ASCII value of 'H'

## Bytes are Immutable

data = b"Hello"

data[0] = 74

TypeError: 'bytes' object does not support item assignment

### What is bytearray in Python?

A bytearray is a sequence of bytes that can be changed (mutable) after creation

data = bytearray(b"Hello")

data[0] = 74   # ASCII value of 'J'

print(data)    //output  bytearray(b'Jello')   Here we changed H → J.


## What is memoryview in Python?

memoryview is a built-in data type that allows you to access the memory of another binary object (such as bytes or bytearray) without copying the data.

This makes data processing faster and more memory-efficient.

data = bytes(5)

mv = memoryview(data)

print(mv)     /// Output:  <memory at 0x00000123456789>

## Collection Data Types
In Python, Collection Data Types are used to store multiple values in a single variable.

## 4. what is List ??
ans:- A List is a Python collection data type used to store multiple values in a single variable. It is an ordered and mutable (changeable) that allows duplicate values and is represented using square brackets []
- Supports indexing and slicing
- Can store different data types
- 
- Ordered
- Mutable
- Allows duplicates
- Uses []

fruits = ["apple", "banana", "mango", "apple"]

print(fruits)

## what is Tuple ???

A Tuple is a Python collection data type used to store multiple values in a single variable. It is an ordered and immutable (con not change) that allows duplicate values and is represented using parentheses ()

- Ordered
- Immutable
- Allows duplicates
- Uses ()

colors = ("red", "green", "blue", "red")

print(colors)

## what is  Set ?? 
A Set is a Python collection data type used to store multiple values in a single variable. It is an unordered and mutable (changeable) that does not allow duplicate values and is represented using curly braces {}.

numbers = {1, 2, 3, 4, 4, 5}

print(numbers)

- Unordered
- Mutable
- No duplicates
- Uses {}
  
  ## what is Dictionary

A Dictionary is a Python collection data type used to store multiple values in the form of key-value pairs. It is an ordered and mutable (changeable) where keys are unique, and it is represented using curly braces {}.

student = {
    "name": "Vinod",
    "age": 25,
    "city": "Delhi"
}

- Key-value pairs
- Mutable
- Keys must be unique
- Uses {key: value}

| Data Type  | Ordered | Mutable | Duplicates | Syntax        |
| ---------- | ------- | ------- | ---------- | ------------- |
| List       | Yes     | Yes     | Yes        | `[]`          |
| Tuple      | Yes     | No      | Yes        | `()`          |
| Set        | No      | Yes     | No         | `{}`          |
| Dictionary | Yes*    | Yes     | Keys No    | `{key:value}` |

## Difference between List and Tuple?
| List    | Tuple     |
| ------- | --------- |
| Mutable | Immutable |
| Uses [] | Uses ()   |
| Slower  | Faster    |



## What is the difference between == and is?
==

Compares values.

is

Compares memory locations.

a = [1,2]

b = [1,2]

print(a == b)  # True

print(a is b)  # False

## What are *args and **kwargs?

## *args
Accepts multiple positional arguments.

def total(*args):

    return sum(args)

print(total(1,2,3))

## **kwargs

Accepts multiple keyword arguments.

def display(**kwargs):

    print(kwargs)

display(name="Vinod", age=25)

## What is a Function in Python?

A function is a block of reusable code that performs a specific task. Functions help make programs more organized, readable, and reusable.

Ex:- 

def function_name(parameters):

    # code block

    return value

## Types of Functions in Python

## 1. Built-in Functions

 Python provides many built-in functions.

 print("Hello")

len("Python")

sum([1, 2, 3, 4])

## 2. User-Defined Functions

Created by the programmer.

def add(a, b):

    return a + b

print(add(10, 20))

## Function with No Parameters
def welcome():

    print("Welcome to Python")

welcome()

## Function with Parameters
def multiply(a, b):

    return a * b

print(multiply(5, 4))

## Function with Default Parameters

def greet(name="Guest"):

    print("Hello", name)

greet()

greet("Vinod")

## What is a Lambda Function in Python?

A Lambda Function is a small anonymous function (a function without a name) that can have any number of arguments but only one expression.

square = lambda x: x * x

print(square(5))

## Difference Between def and lambda

| `def` Function              | `lambda` Function         |
| --------------------------- | ------------------------- |
| Has a name                  | Anonymous (no name)       |
| Multiple statements allowed | Only one expression       |
| Uses `def` keyword          | Uses `lambda` keyword     |
| Better for complex logic    | Best for short operations |


## What is List Comprehension in Python?

List Comprehension is a concise way to create lists in Python using a single line of code. It makes code shorter, cleaner, and often faster than using traditional loops.
ex:-
new_list = [expression for item in iterable]

squares = [x * x for x in range(1, 6)]

print(squares)

## What is Exception Handling in Python?

Exception Handling is a mechanism used to handle runtime errors (exceptions) so that the program does not terminate unexpectedly.

It allows you to catch errors and execute alternative code when an error occurs.

- Why Use Exception Handling?
- Prevents program crashes.
- Handles errors gracefully.
- Improves program reliability.
- Allows custom error messages.

try:

    # Code that may cause an exception

except:

    # Code to handle the exception

<!-- -------- -->
try:
    num = int(input("Enter a number: "))

    result = 10 / num

    print(result)

except ValueError:

    print("Please enter a valid number!")

except ZeroDivisionError:

    print("Cannot divide by zero!")


## Using else

The else block executes if no exception occurs.

try:
    num = 10 / 2

except ZeroDivisionError:

    print("Error!")

else:

    print("Result:", num)

### Using finally

The finally block always executes whether an exception occurs or not.

try:

    print("Inside try block")

except:

    print("Error occurred")

finally:

    print("This always executes")

## Keywords Used in Exception Handling
| Keyword   |    Purpose                               |
| --------- | ----------------------------------------- |

| `try`     | Contains code that may raise an exception |

| `except`  | Handles the exception                     |

| `else`    | Executes if no exception occurs           |

| `finally` | Executes regardless of exceptions         |

| `raise`   | Manually raises an exception              |

| --------- | ----------------------------------------- |


- Error: A serious issue that usually stops program execution (e.g., syntax errors).
- Exception: A runtime problem that can be caught and handled using exception handling (e.g., ZeroDivisionError, ValueError).

## What is a Module in Python?

A Module is a file containing Python code (functions, classes, variables, and statements) that can be reused in other Python programs.

A module helps organize code into separate files and promotes code reusability.

- create a  .py file

# math_utils.py

def add(a,b):

    return a+b

## There are two types of modules in Python:

- 1.  Built-in Modules – Modules that come pre-installed with Python, such as math, random, os, and datetime.

Examples:

- math – Mathematical operations
- random – Generate random numbers
- datetime – Work with dates and times
- os – Interact with the operating system
- sys – Access Python system-specific parameters


- 2. User-Defined Modules – Modules created by the programmer to organize and reuse code across multiple Python programs.
 
def add(a, b):

    return a + b

## Module vs Package

| Module                                 | Package                                |

| -------------------------------------- | ------------------------------------------ |

| A single `.py` file                    | A collection of modules                    |

| Contains functions, classes, variables | Contains multiple modules and sub-packages |

| Example: `math.py`                     | Example: `numpy`, `pandas`                 |

## Q: What is the difference between import module and from module import function?

- import module imports the entire module, and functions are accessed using module.function().
- from module import function imports only the specified function, allowing direct use without the module name.

### Advantages of Modules
- Code Reusability – Use the same code in multiple programs.
- Better Organization – Split large programs into smaller files.
- Easy Maintenance – Easier to update and debug.
- Namespace Management – Avoids naming conflicts.


## What is PIP in Python?

PIP is Python's package manager.

PIP (Pip Installs Packages) is the default package manager for Python. It is used to install, upgrade, update, and remove Python packages and libraries from the Python Package Index (PyPI).

PIP makes it easy to add external libraries to your Python projects without manually downloading and configuring them.

## Advantages of PIP
- Easy installation of Python packages.
- Manages package dependencies automatically.
- Allows package upgrades and removal.
- Provides access to thousands of libraries available on PyPI

Common PIP Commands

Check PIP Version

pip --version

Install a Package

pip install package_name

Example:

pip install numpy

Upgrade a Package

pip install --upgrade numpy

Uninstall a Package

pip uninstall numpy

View Installed Packages

pip list


## What is a Virtual Environment in Python?

A Virtual Environment (venv) is an isolated environment that allows you to install and manage Python packages separately for each project.

It helps avoid conflicts between package versions used in different projects.

## Why Use a Virtual Environment?
- Isolates project dependencies.
- Prevents package version conflicts.
- Keeps the global Python installation clean.
- Makes projects easier to share and deploy.

Create a Virtual Environment

python -m venv myenv

Activate the Virtual Environment

Windows:

myenv\Scripts\activate

Linux/Mac:

source myenv/bin/activate

Install Packages

pip install requests

The package will be installed only inside the virtual environment.

Deactivate the Virtual Environment

deactivate

## 24. How to Read a File?

with open("data.txt","r") as file:

    content = file.read()

print(content)


## 25. Difference between read(), readline(), readlines()
  
read()       # Entire file

readline()   # One line

readlines()  # All lines in list


## What are Generators in Python?

A Generator is a special type of function that generates values one at a time instead of returning all values at once. Generators use the yield keyword instead of return.

They are memory-efficient because they produce values only when needed.

### Why Use Generators?
- Save memory by generating values on demand.
- Memory Efficiency
- Useful for working with large datasets.
- Processing Large Files
- Improve performance for iterative operations.
- Infinite Sequences


def read_large_file(filename):

    with open(filename) as file:

        for line in file:

            yield line

This reads one line at a time instead of loading the entire file.

## How yield Works

When Python encounters yield:

- It returns the current value.
- It saves the function's state.
- The function pauses.
- On the next call, execution continues from the same point.

## Difference Between return and yield

| Feature         | `return`                                 | `yield`                                        |
| --------------- | ---------------------------------------- | ---------------------------------------------- |
| Purpose         | Ends the function and returns a value    | Pauses the function and returns a value        |
| Function Type   | Normal function                          | Generator function                             |
| Execution       | Function terminates                      | Function state is saved and can resume         |
| Multiple Values | Returns only once                        | Can produce multiple values over time          |
| Memory Usage    | Stores all results if returned as a list | Generates values one by one (memory efficient) |


def numbers():

    yield 1

    yield 2

    yield 3

for num in numbers():

    print(num)

## What is a Decorator in Python?

A Decorator is a function that adds extra functionality to another function without modifying its original code.

def my_decorator(func):

    def wrapper():

        print("Before function call")

        func()

        print("After function call")

    return wrapper

@my_decorator

def greet():

    print("Hello!")

greet()


## Real-World Use Cases
Logging, 
Authentication & Authorization, 
Performance Timing, 
Input Validation, 
Caching, 

## What is Deep Copy in Python?

A Deep Copy creates a completely independent copy of an object, including all nested objects. Any changes made to the copied object do not affect the original object.

Python provides Deep Copy through the copy.deepcopy() method.

import copy

original = [[1, 2], [3, 4]]

deep_copy = copy.deepcopy(original)

deep_copy[0][0] = 100

print("Original:", original)

print("Deep Copy:", deep_copy)

output: 
Original: [[1, 2], [3, 4]]
Deep Copy: [[100, 2], [3, 4]]


## Explanation
- deepcopy() creates a new outer list.
- It also creates new copies of all inner lists.
- Therefore, modifying deep_copy does not change original.

## When to Use Deep Copy?

- Working with nested lists, dictionaries, or objects.
- You need a completely independent copy.
- Changes in the copied object should not affect the original.

## what is Shallow Copy: 
Creates a new object, but copies the references (memory locations) of nested objects. Therefore, nested objects are shared, and changes in them affect both copies.

## Why use ?
- original and shallow are different lists.
- But their inner lists refer to the same memory locations.
- Changes to nested objects affect both.
 
import copy

original = [[1, 2], [3, 4]]

shallow = copy.copy(original)

shallow[0][0] = 100

print(original)

print(shallow)

## Comparison Table

| Feature               | Shallow Copy  | Deep Copy         |
| --------------------- | ------------- | ----------------- |
| Copies outer object   | ✅             | ✅              |
| Copies nested objects | ❌             | ✅              |
| Shared references     | Yes           | No                |
| Memory usage          | Less          | More              |
| Speed                 | Faster        | Slower            |
| Method                | `copy.copy()` | `copy.deepcopy()` |

What is the Global Interpreter Lock (GIL)?

GIL (Global Interpreter Lock) is a mechanism (lock) in Python that allows only one thread to execute Python bytecode at a time, even on a multi-core CPU.

It makes memory management thread-safe but limits true parallel execution of CPU-bound threads.

## Key Points
- Only one thread runs Python code at a time.
- Improves thread safety and memory management.
- Affects CPU-bound multithreading performance.
- I/O-bound tasks (file handling, network calls, database operations) still benefit from multithreading.
Exa

import threading

def task():

    for i in range(1000000):

        pass

t1 = threading.Thread(target=task)

t2 = threading.Thread(target=task)

t1.start()

t2.start()

Even with two threads, Python executes only one thread's bytecode at a time because of the GIL.

## What is Multithreading?

Multithreading is a technique where multiple threads run concurrently within a single process to perform multiple tasks.

## Advantages
- Improves responsiveness
- Better utilization during I/O operations
- Allows multiple tasks to run concurrently

import threading

def task():

    print("Thread is running")

t1 = threading.Thread(target=task)

t2 = threading.Thread(target=task)

t1.start()

t2.start()

## What is Multiprocessing?

Multiprocessing is the execution of multiple processes simultaneously, where each process has its own memory space and Python interpreter. It enables true parallel execution by bypassing the GIL, making it ideal for CPU-bound tasks.

## Advantages
- True parallel execution
- Bypasses the GIL
- Best for CPU-intensive tasks
- Utilizes multiple CPU cores

## Multithreading vs Multiprocessing

| Feature     | Multithreading  | Multiprocessing  |
| ----------- | --------------- | ---------------- |
| Unit        | Threads         | Processes        |
| Memory      | Shared          | Separate         |
| GIL Impact  | Yes             | No               |
| Best For    | I/O-bound tasks | CPU-bound tasks  |
| Parallelism | Limited by GIL  | True parallelism |


from multiprocessing import Process

def task():

    print("Process is running")

p1 = Process(target=task)

p2 = Process(target=task)

p1.start()

p2.start()

p1.join()

p2.join()

