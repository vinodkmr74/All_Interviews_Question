What is OOP in Python?

Ans:- OOP (Object-Oriented Programming) is a programming approach that organizes code using classes and objects. It helps make programs more modular, reusable, and easier to maintain.

## Features of OOP (Object-Oriented Programming)

- Class
- Object
- Encapsulation
- Inheritance
- Polymorphism
- Abstraction

## what is class???
A Class is a blueprint or template for creating objects. It defines the attributes (data) and methods (functions) that the objects will have.

class Student:

    name = "Vinod"

    def display(self):

        print(self.name)

- Student is a class.
- name attribute 
- display() method.

## What is an Object in Python?

An object is an instance of a class. It is a real entity created using a class and web can access the attributes and methods defined in that class.

class Car:

    color = "Red"

car1 = Car()   # Object

- Car → Class
- car1 → Object (instance of the Car class)

## What is Encapsulation in Python?

Encapsulation is the process of wrapping data (variables) and methods (functions) into a single unit is called Encapsulation . and it is  restricting direct access to data., to provide security.

## Encapsulation - Key Points (Interview)
- It helps in data hiding.
- It provides data security.
- It restricts direct access to data using private variables (__variable).
- Data is accessed through public methods (getters/setters).
- It improves code maintainability and data protection.

- data hiding is achieved using private variables (__variable).

class Encap:

    def __init__(self):

        self.__name = "Vinod"   # Private variable

obj = Encap()

   print(obj.__name) ❌ Error not allow direct access  and hidding private variable

-  Here, __name is hidden from direct access outside the class.

- Yahan __name ko directly access nahi kar sakte, kyunki ye private variable hai.

- Data ko access karne ke liye method use karna padega:

class Encap:

    def __init__(self):

        self.__name = "Vinod"

    def get_name(self):

        return self.__name

obj = Encap()

print(obj.get_name())   # ✅ Vinod


## What is Inheritance in Python?

Inheritance is the process of inheriting the properties and methods of a parent class into a child class.
is calld inheritance 

## Key Points:
- Promotes Code Reusability.
- Reduces code duplication.
- Represents an "is-a" relationship.

class Parent:

    def display(self):

        print("I am Parent Class")

class Child(Parent):

    pass

obj = Child()

obj.display()

## Python supports five types of inheritance:

1. Single Inheritance
2. Multiple Inheritance
3. Multilevel Inheritance
4. Hierarchical Inheritance
5. Hybrid Inheritance

## 1. Single Inheritance

One child class inherits properties and methods from one parent class.

class Parent:

    pass

class Child(Parent):

    pass

## 2.  Multiple Inheritance

One child class inherits properties and methods from multiple parent classes.

class Father:

    pass

class Mother:

    pass

class Child(Father, Mother):

    pass

## 3. Multilevel Inheritance

A class inherits from a class that is already inherited from another class.

class GrandParent:

    pass

class Parent(GrandParent):

    pass

class Child(Parent):

    pass


## 4. Hierarchical Inheritance

Multiple child classes inherit from the same parent class.

class Parent:

    pass

class Child1(Parent):

    pass

class Child2(Parent):

    pass

## 5. Hybrid Inheritance

Combination of two or more types of inheritance.

Combination of Multiple + Multilevel Inheritance


## What is Polymorphism in Python?

Polymorphism means "many forms". It allows the same object (method or function) to  different behave depending on the object.

## Key Points

- ✅ Same method name
- ✅ Different behavior
- ✅ Increases flexibility and reusability
- ✅ Achieved through Method Overriding in Python

class Dog:

    def sound(self):

        print("Bark")

class Cat:

    def sound(self):

        print("Meow")

for animal in (Dog(), Cat()):

    animal.sound()

## There are two types of polymorphism:

- 1. Compile-Time Polymorphism (Method Overloading)  Python does not support true method overloading directly.
- 2. Run-Time Polymorphism (Method Overriding)


1. Compile-Time Polymorphism (Method Overloading)
- Same method name with different parameters.
- Python does not support true method overloading directly.

class Demo:

    def add(self, a, b=0):

        return a + b

obj = Demo()

print(obj.add(10))

print(obj.add(10, 20))

## Python Overloading ko kaise achieve karta hai?
Ans :  
- 1. Default Arguments ke dowara
- 2. Variable Length Arguments (*args) ke dowara

## 1. Default Arguments
class Demo:

    def add(self, a, b=0):

        return a + b

obj = Demo()

print(obj.add(10))      # 10

print(obj.add(10, 20))  # 30


## Variable Length Arguments (*args)
class Demo:

    def add(self, *args):

        return sum(args)

obj = Demo()

print(obj.add(10))

print(obj.add(10, 20))

print(obj.add(10, 20, 30))

## 2. Run-Time Polymorphism (Method Overriding)

Child class provides its own implementation of a method already defined in the parent class.

class Parent:

    def show(self):

        print("Parent Class")

class Child(Parent):

    def show(self):

        print("Child Class")

obj = Child()

obj.show()

## What is Abstraction in Python?

Abstraction is the process of hiding the complexcity or  internal implementation details and showing or given only the necessary functionality to the user.

Key Points

- ✅ Hides implementation details
- ✅ Shows only essential features
- ✅ Improves security
- ✅ Reduces complexity
- ✅ Achieved using Abstract Classes (ABC) and Abstract Methods

- 1. ABC (Abstract Base Class): Used to create abstract classes.
- 2. @abstractmethod: Used to declare abstract methods that must be implemented by child classes.

@abstractmethod ek decorator hai jo method ko abstract bana deta hai.

Abstract method ka sirf declaration hota hai, implementation nahi hoti.

Child Class Must Implement It

from abc import ABC, abstractmethod


class Vehicle(ABC):

    @abstractmethod

    def start(self):        // Yahan start() ek abstract method hai.

        pass

class Car(Vehicle):

    def start(self):

        print("Car Started")

obj = Car()

obj.start()


## Important Interview Point

Agar child class abstract method ko implement nahi karegi, to object create nahi hoga.

class Car(Vehicle):

    pass

obj = Car()   # ❌ Error

## What is a Constructor in Python?

A Constructor is a special method that is automatically called when an object of a class is created. It is used to initialize the object's attributes.

In Python, the constructor is:

  __init__()

class Student:

    def __init__(self, name):

        self.name = name

obj = Student("Vinod")

print(obj.name)

Here, __init__() is automatically called when obj is created.

## Key Points

- ✅ Special method
- ✅ Automatically called when object is created
- ✅ Used to initialize object data
- ✅ Constructor name in Python is __init__()

## There are two types of constructors in Python:

## 1. Default Constructor
A constructor that does not accept any parameters and  except self.
Used to initialize objects with default values.

class Student:

    def __init__(self):

        print("Default Constructor")

obj = Student()

## 2. Parameterized Constructor

A constructor that accepts parameters along with self.
Used to initialize objects with specific values.

class Student:

    def __init__(self, name):

        self.name = name

obj = Student("Vinod")

print(obj.name)