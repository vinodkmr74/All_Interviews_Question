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
