# Python Data Structures and OOP

# Data Structures:

Python includes a number of data structures for storing and organizing data. The following are some of the most common ones:

## Lists:

Lists are used to store multiple items in a single variable. They can hold any type of collection of items (including other lists), and their elements can be accessed via an index. Lists are mutable, which means they can be changed by adding, removing, or changing elements. Here's an example of how to make a list and access its elements:
```
thislist = ["apple", "banana", "orange"]
print(thislist[0]) # OUTPUT apple
print(thislist[2]) # OUTPUT orange
```

## Tuples:

Tuples are similar to lists, but they are immutable, which means they cannot be **changed** once created. They are frequently used to represent fixed sets of data. Tuples can be created with or without parentheses, but they are typically used to make the code more readable. Here's an example of a tuple and how to access its elements:
```
my_tuple = (1, 2, [4, 5])
print(my_tuple[0])   # OUTPUT 1
print(my_tuple[2])   # OUTPUT "three"
print(my_tuple[3][0]) # OUTPUT 4
```

## Dictionaries:

Dictionaries are yet another versatile Python data structure that stores a collection of key-value pairs. The keys must be unique and unchangeable (strings and numbers are common), and the values can be of any type. Dictionaries can be changed by adding, removing, or changing key-value pairs. Here's an example of creating and accessing a dictionary's values:

```
my_dict = {"name": "Sourav", "project": "90DaysOfDevOps", "country": "India"}
print(my_dict["name"])   # OUTPUT "Sourav"
print(my_dict["project"])   # OUTPUT "90DaysOfDevOps"
print(my_dict["country"])  # OUTPUT "India"
```
## Sets:

Sets are used to store multiple items in a single variable. They are frequently used in mathematical operations such as union, intersection, and difference. Sets are mutable, which means they can be added or removed, but the elements themselves must be immutable and sets cannot have two items with the same value. Here's an example of how to make a set and then perform operations on it:

```
my_set = {1, 2, 3, 4, 5}
other_set = {3, 4, 5, 6, 7}
print(my_set.union(other_set))  # {1, 2, 3, 4, 5, 6, 7}
print(my_set.intersection(other_set)) # {3, 4, 5}
print(my_set.difference(other_set))  # {1, 2}
```

# Object-Oriented Programming:

I also want to talk about object-oriented programming (OOP) concepts in Python, which are used to structure code into reusable and modular components, in addition to data structures. Here are some of the most essential OOP concepts to understand:

## Class

A class is a template for creating objects. A class specifies the attributes (data) and methods (functions) that a class's objects can have. Classes are defined using the `class` keyword, and objects are created using the class constructor. Here's an example of defining a `Person` class and creating an object of that class:

```
class Person:
    def __init__(self, name, country):
        self.name = name
        self.country = country
person = Person("Sourav", "India")
print(person.name)   # OUTPUT "Sourav"
print(person.country)    # OUTPUT "India"
```

## Inheritance:

Inheritance is a technique for creating a new class from an existing one. The new class, known as a subclass, inherits the attributes and methods of the existing superclass. Subclasses can extend or override the superclass's attributes and methods to create new functionality. Here's an example of defining a `Person` subclass called `Student`:

```
class Student(Person):
    def __init__(self, name, country, major):
        super().__init__(name, country)
        self.major = major

student = Student("Sourav", "India", "Computer Science")
print(student.name)   # OUTPUT "Sourav"
print(student.country)    # OUTPUT "India"
print(student.major)  # OUTPUT "Computer Science"
```

## Polymorphism:

Polymorphism refers to the ability of objects to take on different forms or behaviors depending on their context. Polymorphism can be achieved by using inheritance, method overriding, and abstract classes and interfaces. Here's an example of a speak() method being implemented in both the Person and Student classes:

```
class Person:
    def __init__(self, name, country):
        self.name = name
        self.country = country

    def speak(self):
        print("Hello, my name is {} and I am from {}.".format(self.name, self.country))

class Student(Person):
    def __init__(self, name, country, major):
        super().__init__(name, country)
        self.major = major

    def speak(self):
        print("Hello, my name is {} and I am a {} major.".format(self.name, self.major))

person = Person("Sourav", "India")
student = Student("Sonu", "India", "Computer Science")

person.speak()   # "Hello, my name is Sourav and I am from India."
student.speak()  # "Hello, my name is Sonu and I am a Computer Science major."
```