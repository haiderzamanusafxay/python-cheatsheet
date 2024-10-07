# Python Cheatsheet: Beginner to Advanced (with Explanations)

## Beginner Level

### Variables and Data Types
```python
# Variable assignment
x = 5  # Integer
y = 3.14  # Float
name = "Python"  # String
is_true = True  # Boolean

# Multiple assignment
a, b, c = 1, 2, 3

# Data types
my_list = [1, 2, 3]  # List (mutable)
my_tuple = (1, 2, 3)  # Tuple (immutable)
my_dict = {"key": "value"}  # Dictionary
my_set = {1, 2, 3}  # Set (unique elements)
```
Explanation: Python uses dynamic typing, meaning you don't need to declare variable types. Lists are mutable (can be changed), while tuples are immutable. Dictionaries store key-value pairs, and sets store unique elements.

### Basic Operators
```python
# Arithmetic operators
sum = 5 + 3
difference = 10 - 4
product = 6 * 7
quotient = 20 / 4  # Returns float
integer_quotient = 20 // 4  # Floor division
remainder = 15 % 4
power = 2 ** 3

# Comparison operators
equal = (5 == 5)
not_equal = (5 != 6)
greater_than = (10 > 5)
less_than_or_equal = (5 <= 5)

# Logical operators
and_result = True and False
or_result = True or False
not_result = not True
```
Explanation: Python provides standard arithmetic operators, including floor division (//) and power (**). Comparison operators return boolean values. Logical operators (and, or, not) are used for combining conditions.

### Control Structures
```python
# If-elif-else statement
x = 10
if x > 10:
    print("x is greater than 10")
elif x < 10:
    print("x is less than 10")
else:
    print("x is equal to 10")

# For loop
for i in range(5):
    print(i)  # Prints 0 to 4

# While loop
count = 0
while count < 5:
    print(count)
    count += 1

# List comprehension
squares = [x**2 for x in range(5)]  # [0, 1, 4, 9, 16]
```
Explanation: Python uses indentation to define code blocks. The `range()` function generates a sequence of numbers. List comprehensions provide a concise way to create lists based on existing lists or other iterable objects.

### Functions
```python
def greet(name):
    """This function greets the person passed in as a parameter"""
    return f"Hello, {name}!"

# Function call
message = greet("Alice")
print(message)  # "Hello, Alice!"

# Default parameters
def power(base, exponent=2):
    return base ** exponent

print(power(3))  # 9 (3^2)
print(power(3, 3))  # 27 (3^3)

# *args and **kwargs
def print_args(*args, **kwargs):
    for arg in args:
        print(arg)
    for key, value in kwargs.items():
        print(f"{key}: {value}")

print_args(1, 2, 3, name="Alice", age=30)
```
Explanation: Functions are defined using the `def` keyword. The docstring ("""...""") provides a description of the function. Default parameters allow functions to be called with fewer arguments. `*args` allows a variable number of positional arguments, while `**kwargs` allows a variable number of keyword arguments.

## Intermediate Level

### List, Dictionary, and Set Operations
```python
# List operations
my_list = [1, 2, 3, 4, 5]
my_list.append(6)  # Add to end
my_list.insert(0, 0)  # Insert at index
popped = my_list.pop()  # Remove and return last item
my_list.remove(3)  # Remove first occurrence of 3

# List slicing
sliced = my_list[1:4]  # Elements from index 1 to 3
reversed_list = my_list[::-1]  # Reverse the list

# Dictionary operations
my_dict = {"a": 1, "b": 2}
my_dict["c"] = 3  # Add new key-value pair
value = my_dict.get("a", 0)  # Get value (0 is default if key not found)
keys = my_dict.keys()  # Get all keys
items = my_dict.items()  # Get all key-value pairs as tuples

# Set operations
set1 = {1, 2, 3}
set2 = {3, 4, 5}
union = set1 | set2  # {1, 2, 3, 4, 5}
intersection = set1 & set2  # {3}
difference = set1 - set2  # {1, 2}
```
Explanation: Lists, dictionaries, and sets have various built-in methods for manipulation. List slicing allows you to extract portions of a list. Dictionaries use keys to access values. Sets are useful for mathematical set operations and removing duplicates from sequences.

### File I/O
```python
# Writing to a file
with open("example.txt", "w") as file:
    file.write("Hello, World!")

# Reading from a file
with open("example.txt", "r") as file:
    content = file.read()
    print(content)

# Appending to a file
with open("example.txt", "a") as file:
    file.write("\nAppended line")

# Reading lines
with open("example.txt", "r") as file:
    lines = file.readlines()
    for line in lines:
        print(line.strip())
```
Explanation: The `with` statement ensures proper handling of file resources. Different modes ("w" for write, "r" for read, "a" for append) determine how the file is opened. `read()` reads the entire file, while `readlines()` returns a list of lines.

### Exception Handling
```python
try:
    x = 1 / 0
except ZeroDivisionError:
    print("Cannot divide by zero!")
except Exception as e:
    print(f"An error occurred: {e}")
else:
    print("No exception occurred")
finally:
    print("This always executes")

# Custom exception
class CustomError(Exception):
    pass

try:
    raise CustomError("This is a custom error")
except CustomError as e:
    print(e)
```
Explanation: Exception handling allows you to gracefully handle errors. The `try` block contains code that might raise an exception. `except` blocks catch specific exceptions. `else` runs if no exception occurs, and `finally` always executes. You can create custom exceptions by inheriting from `Exception`.

## Advanced Level

### Decorators
```python
def decorator_function(original_function):
    def wrapper_function(*args, **kwargs):
        print(f"Before {original_function.__name__}")
        result = original_function(*args, **kwargs)
        print(f"After {original_function.__name__}")
        return result
    return wrapper_function

@decorator_function
def display_info(name, age):
    print(f"display_info ran with arguments ({name}, {age})")

display_info("John", 25)
```
Explanation: Decorators allow you to modify or enhance functions without changing their source code. They are denoted by the `@` symbol followed by the decorator function name. Decorators are often used for logging, timing functions, or adding authentication.

### Generators
```python
def fibonacci_generator():
    a, b = 0, 1
    while True:
        yield a
        a, b = b, a + b

fib = fibonacci_generator()
for _ in range(10):
    print(next(fib))  # Print first 10 Fibonacci numbers
```
Explanation: Generators are functions that use `yield` instead of `return`. They generate values on-the-fly and can be iterated over, which is memory-efficient for large sequences. The state of the generator function is saved between calls.

### Context Managers
```python
class CustomContextManager:
    def __enter__(self):
        print("Entering the context")
        return self

    def __exit__(self, exc_type, exc_value, traceback):
        print("Exiting the context")
        if exc_type is not None:
            print(f"An exception occurred: {exc_value}")
        return False  # Propagate exceptions

with CustomContextManager() as cm:
    print("Inside the context")
    # raise Exception("Test exception")
```
Explanation: Context managers define the behavior for entering and exiting a context (like with file I/O). They are implemented using the `__enter__` and `__exit__` methods. This is useful for resource management, such as automatically closing files or database connections.

### Metaclasses
```python
class Meta(type):
    def __new__(cls, name, bases, attrs):
        # Add a new attribute to the class
        attrs['added_by_metaclass'] = 42
        return super().__new__(cls, name, bases, attrs)

class MyClass(metaclass=Meta):
    pass

print(MyClass.added_by_metaclass)  # 42
```
Explanation: Metaclasses are classes for classes. They allow you to customize class creation. The `__new__` method of a metaclass is called when a new class using this metaclass is created, allowing you to modify the class before it's created.

### Async IO
```python
import asyncio

async def fetch_data():
    print("start fetching")
    await asyncio.sleep(2)  # Simulate I/O operation
    print("done fetching")
    return {'data': 1}

async def print_numbers():
    for i in range(10):
        print(i)
        await asyncio.sleep(0.25)

async def main():
    task1 = asyncio.create_task(fetch_data())
    task2 = asyncio.create_task(print_numbers())
    
    value = await task1
    print(value)
    await task2

asyncio.run(main())
```
Explanation: Async IO allows you to write concurrent code using the `async` and `await` syntax. It's useful for I/O-bound and high-level structured network code. The `asyncio` module provides tools for writing concurrent code. This example demonstrates running multiple coroutines concurrently.

This cheatsheet covers a wide range of Python concepts from beginner to advanced levels. Remember that mastering these concepts requires practice and application in real projects. Happy coding!
