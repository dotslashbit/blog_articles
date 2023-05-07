---
title: "Quick Python Primer: Master the Basics in 20 Minutes"
seoTitle: "Quick Python Primer: Master the Basics in 20 Minutes"
seoDescription: "Learn Python basics in 20 mins: variables, data types, strings, structures, functions, conditionals, loops, modules, classes. Ideal for beginners & sk..."
datePublished: Sun May 07 2023 03:30:42 GMT+0000 (Coordinated Universal Time)
cuid: clhcuwghz04uzm0nvc9otdzs6
slug: quick-python-primer-master-the-basics-in-20-minutes
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1683380969649/b7dcd03b-e56e-41be-bd98-dc5ee7831417.png
tags: programming-blogs, programming, python, python3, python-beginner

---

Discover the essentials of Python programming in this comprehensive review and guide, designed to help you master the basics. Learn about variables, data types, string formatting, data structures, functions, conditionals, loops, modules, and classes in Python, and unlock the power of this versatile and powerful language. Whether you're a beginner or looking to brush up on your skills, this article will provide you with a solid foundation for Python development.

I've previously discussed installing Python and setting up Visual Studio Code for Python development, so I won't explain that in this article.

## Variable

In Python, a variable is a named placeholder that can store a value. Variables are created using the assignment operator (`=`). For example:

```python
my_variable = 10
```

Here, `my_variable` is a variable that holds the value `10`.

Python has several data types that can be assigned to variables. Some common data types in Python include:

1. Numeric data types:
    
    * Integer (`int`) - represents whole numbers, such as `42` or `-7`.
        
    * Float (`float`) - represents decimal numbers, such as `3.14` or `-0.5`.
        
    * Complex (`complex`) - represents numbers with both a real and imaginary component, such as `1 + 2j`.
        
2. Boolean data type:
    
    * Boolean (`bool`) - represents a value of either `True` or `False`.
        
3. Sequence data types:
    
    * String (`str`) - represents a sequence of characters, such as `"Hello, World!"`.
        
    * List (`list`) - represents an ordered collection of items, such as `[1, 2, 3]`.
        
    * Tuple (`tuple`) - similar to a list, but immutable (cannot be changed), such as `(1, 2, 3)`.
        
4. Mapping data type:
    
    * Dictionary (`dict`) - represents a collection of key-value pairs, such as `{"name": "John", "age": 30}`.
        
5. Set data type:
    
    * Set (`set`) - represents an unordered collection of unique items, such as `{1, 2, 3}`.
        

Python is a dynamically typed language, which means that the data type of a variable is inferred at runtime based on the value it holds. For example, if you assign an integer value to a variable, the variable will have an `int` data type. If you later assign a string value to the same variable, the variable will now have a `str` data type.

## String Formatting

In Python, string formatting is the process of creating a string by inserting values into a string template. There are several ways to do string formatting in Python, including:

1. Concatenation: You can concatenate strings and variables using the `+` operator. For example:
    
    ```python
    name = "John"
    age = 30
    message = "My name is " + name + " and I am " + str(age) + " years old."
    ```
    
    Here, the `str()` function is used to convert the integer `age` to a string so that it can be concatenated with the other strings.
    
2. `%` operator: You can use the `%` operator to substitute values into a string template. For example:
    
    ```python
    name = "John"
    age = 30
    message = "My name is %s and I am %d years old." % (name, age)
    ```
    
    Here, `%s` is a placeholder for a string value, and `%d` is a placeholder for a decimal (integer) value. The values to be substituted are provided in a tuple `(name, age)`.
    
3. `str.format()`: You can use the `str.format()` method to insert values into a string template. For example:
    
    ```python
    name = "John"
    age = 30
    message = "My name is {} and I am {} years old.".format(name, age)
    ```
    
    Here, the `{}` placeholders are used to indicate where the values should be inserted. The values to be substituted are provided in the `format()` method.
    
4. f-strings (formatted string literals): This is the most recent and widely used way to format strings in Python. You can use an f-string to substitute values into a string template using curly braces `{}`. For example:
    
    ```python
    name = "John"
    age = 30
    message = f"My name is {name} and I am {age} years old."
    ```
    
    Here, the variables `name` and `age` are enclosed in curly braces within the string literal, and the values will be interpolated into the string.
    

In addition to string formatting, Python also provides several built-in string methods that can be used to manipulate strings. Some commonly used string methods in Python include:

1. `str.upper()`: Converts all characters in a string to uppercase.
    
2. `str.lower()`: Converts all characters in a string to lowercase.
    
3. `str.strip()`: Removes whitespace (spaces, tabs, and newlines) from the beginning and end of a string.
    
4. `str.split()`: Splits a string into a list of substrings based on a specified separator.
    
5. `str.join()`: Joins a list of strings into a single string, using a specified separator.
    
6. `str.replace()`: Replaces all occurrences of a specified substring in a string with another substring.
    
7. `str.startswith()`: Returns `True` if a string starts with a specified substring, otherwise `False`.
    
8. `str.endswith()`: Returns `True` if a string ends with a specified substring, otherwise `False`.
    

These are just a few of the many string methods available in Python. You can find more information on string methods in the Python documentation.

## Data Structures

### List

In Python, a list is a collection of items, which can be of any data type, that are ordered and mutable (changeable). Lists are created by enclosing a comma-separated sequence of items within square brackets `[]`. For example:

```python
my_list = [1, 2, 3, "apple", "banana", "cherry"]
```

Here, `my_list` is a list that contains three integers and three strings.

You can access individual items in a list by their index, which starts at 0 for the first item in the list. For example:

```python
print(my_list[0])  # prints 1
print(my_list[3])  # prints "apple"
```

You can also use negative indexing to access items from the end of the list. For example:

```python
print(my_list[-1])  # prints "cherry"
print(my_list[-3])  # prints "apple"
```

Lists in Python support several built-in methods for adding, removing, and manipulating items. Some commonly used list methods include:

1. `list.append(item)`: Adds an item to the end of the list.
    
2. `list.insert(index, item)`: Inserts an item at a specified position in the list.
    
3. `list.remove(item)`: Removes the first occurrence of an item from the list.
    
4. `list.pop(index)`: Removes and returns the item at a specified position in the list.
    
5. `list.sort()`: Sorts the items in the list in ascending order.
    
6. `list.reverse()`: Reverses the order of the items in the list.
    
7. `len(list)`: Returns the number of items in the list.
    

You can also use slicing to extract a subsequence of a list. Slicing uses the colon `:` operator to specify a start index (inclusive) and end index (exclusive) for the subsequence. For example:

```python
my_list = [1, 2, 3, 4, 5]
sub_list = my_list[1:4]  # returns [2, 3, 4]
```

Lists in Python are versatile and widely used in many applications. They can be used to store collections of data, implement algorithms, and represent complex structures.

### Tuple

In Python, a tuple is an ordered, immutable (unchangeable) collection of elements. Tuples are similar to lists, but they cannot be modified once created. Tuples are created by enclosing a comma-separated sequence of values within parentheses `()`. For example:

```python
my_tuple = (1, 2, 3, "apple", "banana", "cherry")
```

Here, `my_tuple` is a tuple that contains three integers and three strings.

You can access individual elements in a tuple by their index, just like in a list. For example:

```python
print(my_tuple[0])  # prints 1
print(my_tuple[3])  # prints "apple"
```

However, because tuples are immutable, you cannot modify their elements once they have been created. For example, the following code will raise a `TypeError`:

```python
my_tuple[0] = 4  # raises TypeError: 'tuple' object does not support item assignment
```

Tuples in Python support several built-in methods for manipulating and querying elements. Some commonly used tuple methods include:

1. `tuple.count(value)`: Returns the number of times a specified value appears in the tuple.
    
2. `tuple.index(value)`: Returns the index of the first occurrence of a specified value in the tuple.
    
3. `len(tuple)`: Returns the number of elements in the tuple.
    

Because tuples are immutable, they are often used to represent fixed collections of data that should not be modified, such as the coordinates of a point in 2D space or the RGB values of a color. Tuples are also commonly used to return multiple values from a function, where the values cannot be modified separately. For example:

```python
def get_name_and_age():
    name = "John"
    age = 30
    return name, age

result = get_name_and_age()
print(result)  # prints ("John", 30)
```

Here, the `get_name_and_age()` function returns a tuple containing two values: the name and age of a person. The tuple is unpacked into the variables `result`, which contains the two values as separate variables.

### Set

In Python, a set is an unordered collection of unique elements. Sets are created by enclosing a comma-separated sequence of values within curly braces `{}` or by using the `set()` constructor function. For example:

```python
my_set = {1, 2, 3, 4, 4, 5}
```

Here, `my_set` is a set that contains five unique integers.

Sets in Python support several built-in methods for adding, removing, and manipulating elements. Some commonly used set methods include:

1. `set.add(element)`: Adds an element to the set.
    
2. `set.remove(element)`: Removes an element from the set. Raises a `KeyError` if the element is not in the set.
    
3. `set.discard(element)`: Removes an element from the set if it is present. Does not raise an error if the element is not in the set.
    
4. `set.pop()`: Removes and returns an arbitrary element from the set.
    
5. `set.clear()`: Removes all elements from the set.
    
6. `set.union(other_set)`: Returns a new set that contains all elements from both sets.
    
7. `set.intersection(other_set)`: Returns a new set that contains only the elements that are common to both sets.
    
8. `set.difference(other_set)`: Returns a new set that contains only the elements that are in the first set but not in the second set.
    
9. `set.symmetric_difference(other_set)`: Returns a new set that contains only the elements that are in either the first or the second set, but not both.
    
10. `len(set)`: Returns the number of elements in the set.
    

Sets in Python are often used to perform mathematical set operations such as union, intersection, and difference. They are also useful for removing duplicates from a list or other sequence. For example:

```python
my_list = [1, 2, 3, 4, 4, 5]
my_set = set(my_list)
print(my_set)  # prints {1, 2, 3, 4, 5}
```

Here, the `set()` constructor is used to create a set from the `my_list` list, which contains duplicate elements. The resulting set `my_set` contains only the unique elements from `my_list`.

### Dictionary

In Python, a dictionary is an unordered collection of key-value pairs. Dictionaries are created by enclosing a comma-separated sequence of key-value pairs within curly braces `{}` or by using the `dict()` constructor function. For example:

```python
my_dict = {"apple": 2, "banana": 3, "cherry": 5}
```

Here, `my_dict` is a dictionary that maps the keys "apple", "banana", and "cherry" to the values 2, 3, and 5, respectively.

You can access individual values in a dictionary by their key, like this:

```python
print(my_dict["apple"])  # prints 2
```

You can also add new key-value pairs to a dictionary, like this:

```python
my_dict["orange"] = 4
```

You can modify the value associated with a key in a dictionary, like this:

```python
my_dict["banana"] = 6
```

And you can remove a key-value pair from a dictionary, like this:

```python
del my_dict["cherry"]
```

Dictionaries in Python support several built-in methods for manipulating and querying keys and values. Some commonly used dictionary methods include:

1. `dict.keys()`: Returns a view of the keys in the dictionary.
    
2. `dict.values()`: Returns a view of the values in the dictionary.
    
3. `dict.items()`: Returns a view of the key-value pairs in the dictionary.
    
4. `dict.get(key, default=None)`: Returns the value associated with a key in the dictionary, or a default value if the key is not present.
    
5. `dict.pop(key, default=None)`: Removes and returns the value associated with a key in the dictionary, or a default value if the key is not present.
    
6. `dict.update(other_dict)`: Adds all key-value pairs from `other_dict` to the dictionary, overwriting values for keys that already exist in the dictionary.
    
7. `len(dict)`: Returns the number of key-value pairs in the dictionary.
    

Dictionaries in Python are often used to represent collections of related data where each element is identified by a unique key. They are also useful for counting the occurrences of elements in a sequence, and for performing lookups based on keys rather than indices.

## Function

In Python, a function is a block of reusable code that performs a specific task. Functions are defined using the `def` keyword, followed by the function name, parentheses `()`, and a colon `:`. The body of the function is indented below the function definition. For example:

```python
def greet(name):
    print("Hello, " + name + "!")
```

Here, `greet` is a function that takes a parameter `name` and prints a greeting message.

You can call a function by using its name followed by parentheses, like this:

```python
greet("Alice")  # prints "Hello, Alice!"
```

Functions can have multiple parameters, and you can provide default values for some or all of the parameters. For example:

```python
def calculate_sum(a, b=0):
    return a + b
```

Here, `calculate_sum` is a function that takes two parameters, `a` and `b`, with a default value of 0 for `b`. The function returns the sum of `a` and `b`.

You can call a function with default parameter values by omitting the corresponding arguments, like this:

```python
print(calculate_sum(5))  # prints 5
print(calculate_sum(5, 10))  # prints 15
```

Functions can also return values using the `return` keyword. For example:

```python
def calculate_product(a, b):
    return a * b
```

Here, `calculate_product` is a function that takes two parameters, `a` and `b`, and returns their product.

You can call a function that returns a value and use its return value in an expression, like this:

```python
result = calculate_product(3, 4)
print(result)  # prints 12
```

Functions in Python can be used to break down complex problems into smaller, more manageable parts, and to organize code for better readability and maintainability. They are a fundamental building block of Python programming and are used extensively in Python applications.

## Conditionals

Conditionals in Python allow you to execute different blocks of code depending on whether certain conditions are true or false. The most commonly used conditional statement in Python is the `if` statement.

Here is an example of an `if` statement in Python:

```python
x = 5
if x > 0:
    print("x is positive")
```

In this example, the `if` statement checks whether the value of `x` is greater than zero. If the condition is true, the `print` statement is executed, and "x is positive" is printed to the console.

You can also use an `else` statement to execute a different block of code when the condition is false. For example:

```python
x = -3
if x > 0:
    print("x is positive")
else:
    print("x is non-positive")
```

In this example, since `x` is negative, the `if` condition is false, and the `else` block is executed instead. "x is non-positive" is printed to the console.

You can also use an `elif` (short for "else if") statement to test additional conditions after the initial `if` statement. For example:

```python
x = 0
if x > 0:
    print("x is positive")
elif x < 0:
    print("x is negative")
else:
    print("x is zero")
```

In this example, since `x` is zero, the first `if` condition is false, and the `elif` condition is tested instead. Since `x` is not negative either, the `else` block is executed instead. "x is zero" is printed to the console.

Conditionals in Python can also use logical operators such as `and`, `or`, and `not` to combine multiple conditions. For example:

```python
x = 10
if x > 0 and x < 100:
    print("x is a positive two-digit number")
```

In this example, the `if` condition checks whether `x` is both greater than zero and less than 100. If the condition is true, the `print` statement is executed.

Conditionals in Python are a powerful tool for controlling program flow and making decisions based on different situations. They are used extensively in Python programs to implement logic and make decisions based on user input, data values, and other factors.

## Loops

In Python, loops allow you to execute a block of code multiple times. There are two types of loops in Python: `for` loops and `while` loops.

A `for` loop is used to iterate over a sequence of values, such as a list or a string. Here is an example of a `for` loop in Python:

```python
fruits = ["apple", "banana", "cherry"]
for fruit in fruits:
    print(fruit)
```

In this example, the `for` loop iterates over the list of fruits and prints each one to the console.

A `while` loop is used to execute a block of code repeatedly as long as a certain condition is true. Here is an example of a `while` loop in Python:

```python
i = 0
while i < 5:
    print(i)
    i += 1
```

In this example, the `while` loop prints the value of `i` to the console and increments it by 1 each time, until `i` is no longer less than 5.

You can also use the `break` and `continue` statements to control the flow of a loop. The `break` statement allows you to exit a loop prematurely, while the `continue` statement allows you to skip over certain iterations of a loop. For example:

```python
for i in range(10):
    if i == 5:
        break
    elif i % 2 == 0:
        continue
    print(i)
```

In this example, the `for` loop prints the values of `i` from 0 to 9, but it uses the `break` statement to exit the loop prematurely when `i` is equal to 5. It also uses the `continue` statement to skip over even values of `i`.

Loops in Python are a powerful tool for iterating over sequences of values, executing code repeatedly, and controlling program flow. They are used extensively in Python programs to implement logic and perform tasks such as data processing, file I/O, and user interaction.

## Module

In Python, a module is a file containing Python code that can be imported into other Python scripts or modules. Modules provide a way to organize code into reusable units and avoid name collisions between different parts of a program.

To use a module in Python, you simply import it using the `import` statement. Here is an example of how to import the `math` module, which provides mathematical functions such as trigonometric and logarithmic functions:

```python
import math

print(math.sqrt(25))  # prints 5.0
print(math.sin(math.pi / 2))  # prints 1.0
```

In this example, we import the `math` module and use its `sqrt` and `sin` functions to calculate the square root of 25 and the sine of pi/2, respectively.

You can also import specific functions or variables from a module using the `from` keyword. For example:

```python
from math import sqrt, pi

print(sqrt(25))  # prints 5.0
print(pi)  # prints 3.141592653589793
```

In this example, we import only the `sqrt` and `pi` functions from the `math` module, which allows us to use them directly without having to prefix them with `math.`.

Python also comes with a large standard library of modules that provide a wide range of functionality, such as file I/O, network communication, and GUI programming. In addition, there are many third-party modules available from the Python Package Index (PyPI) that can be installed using the `pip` package manager.

Modules in Python are a powerful tool for organizing and reusing code, and they provide a convenient way to extend the functionality of the language. By importing modules, you can leverage existing code and focus on solving your specific programming problems.

## Classes and Objects

In Python, a class is a blueprint or template for creating objects, which are instances of the class. A class defines a set of attributes and methods that describe the behavior of objects created from that class.

Here is an example of a simple class in Python:

```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def say_hello(self):
        print(f"Hello, my name is {self.name} and I am {self.age} years old.")
```

In this example, we define a `Person` class with two attributes (`name` and `age`) and one method (`say_hello`). The `__init__` method is a special method that is called when an object of the class is created. It initializes the `name` and `age` attributes with the values passed as arguments.

To create an object from the `Person` class, we can use the following syntax:

```python
person1 = Person("Alice", 25)
person2 = Person("Bob", 30)
```

In this example, we create two objects (`person1` and `person2`) from the `Person` class with different values for the `name` and `age` attributes.

We can call the `say_hello` method on each object to display a greeting:

```python
person1.say_hello()  # prints "Hello, my name is Alice and I am 25 years old."
person2.say_hello()  # prints "Hello, my name is Bob and I am 30 years old."
```

In this example, we call the `say_hello` method on each object to display a personalized greeting.

Classes and objects are a fundamental concept in object-oriented programming (OOP) and are used extensively in Python programs to organize code and implement complex systems. By defining classes, you can create reusable code that can be easily modified and extended, and by creating objects, you can model real-world entities and manipulate them in your program.

## Conclusion

In conclusion, Python is a versatile and powerful programming language with a wide range of features and applications. By mastering the basics, such as variables, data types, string formatting, data structures, functions, conditionals, loops, modules, and classes, you can unlock the full potential of Python and become a proficient developer. Whether you are a beginner or looking to enhance your skills, understanding these fundamental concepts will provide a strong foundation for your Python development journey.

In this series, you'll be learning Python in-depth starting from variables to Object Oriented Programming. At the end of this series, you'll be a proficient Python programmer, who'll know how to write optimized code.