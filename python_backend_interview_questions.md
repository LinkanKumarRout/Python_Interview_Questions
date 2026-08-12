# Python Backend Interview Questions & Answers

**Total questions:** 200

---

## Table of Contents

1. [Python Fundamentals (1–40)](#1-python-fundamentals-140)
2. [Data Structures & Algorithms (41–60)](#2-data-structures--algorithms-4160)
3. [OOP & Design Patterns (61–80)](#3-oop--design-patterns-6180)
4. [Web Frameworks — Django / Flask / FastAPI (81–110)](#4-web-frameworks--django--flask--fastapi-81110)
5. [REST APIs & HTTP (111–130)](#5-rest-apis--http-111130)
6. [Databases & ORM (131–155)](#6-databases--orm-131155)
7. [Async, Concurrency & Performance (156–170)](#7-async-concurrency--performance-156170)
8. [Testing, Debugging & Code Quality (171–180)](#8-testing-debugging--code-quality-171180)
9. [DevOps, Security & System Design Basics (181–200)](#9-devops-security--system-design-basics-181200)

---

## 1. Python Fundamentals (1–40)

## 1. What is the difference between a list and a tuple?

### Answer

A **list** is mutable, meaning we can change its contents after creating it. A **tuple** is immutable, meaning we cannot change its contents after creation.

- List → `[]`
- Tuple → `()`

### Example

```python
my_list = [10, 20, 30]
my_list.append(40)

print(my_list)
# [10, 20, 30, 40]
```

A tuple cannot be modified:

```python
my_tuple = (10, 20, 30)

# my_tuple.append(40)  # AttributeError
```

Tuples can also be used as dictionary keys if all their elements are hashable:

```python
location = (10, 20)

data = {
    location: "Point A"
}
```

### Interview Point

Use a **list** when the collection needs to change. Use a **tuple** for fixed data that should not change.

---

## 2. What is the difference between `==` and `is`?

### Answer

`==` checks whether two objects have the **same value**.

`is` checks whether two variables refer to the **exact same object**.

### Example

```python
a = [1, 2, 3]
b = [1, 2, 3]

print(a == b)
# True

print(a is b)
# False
```

Both lists contain the same values, so `==` is `True`. But they are two different list objects, so `is` is `False`.

Another common example:

```python
result = None

if result is None:
    print("No value")
```

### Interview Point

Use `==` for value comparison and `is` mainly for identity checks such as `is None`.

---

## 3. Explain mutable vs immutable types.

### Answer

A **mutable object** can be changed after it is created.

An **immutable object** cannot be changed after it is created.

### Mutable Example

```python
numbers = [1, 2, 3]
numbers[0] = 100

print(numbers)
# [100, 2, 3]
```

The same list object was modified.

### Immutable Example

```python
name = "John"

# name[0] = "B"  # TypeError
```

Instead, assigning a new string makes the variable refer to a new object:

```python
name = "John"
name = "Bob"
```

Common mutable types:

```text
list
dict
set
bytearray
```

Common immutable types:

```text
int
float
str
tuple
frozenset
bytes
```

### Interview Point

Mutability matters when multiple variables reference the same object because changes to a mutable object can be visible through all references.

---

## 4. What are `*args` and `**kwargs`?

### Answer

`*args` allows a function to accept any number of **positional arguments**.

`**kwargs` allows a function to accept any number of **keyword arguments**.

### `*args` Example

```python
def add_numbers(*args):
    return sum(args)

print(add_numbers(10, 20))
# 30

print(add_numbers(10, 20, 30, 40))
# 100
```

Inside the function, `args` is a tuple.

### `**kwargs` Example

```python
def show_user(**kwargs):
    print(kwargs)

show_user(name="John", age=25)
```

Output:

```python
{'name': 'John', 'age': 25}
```

Inside the function, `kwargs` is a dictionary.

### Interview Point

They are useful when designing flexible functions, decorators, wrappers, and APIs.

---

## 5. What is a generator? How does it differ from a list?

### Answer

A generator produces values **one at a time**, instead of storing all values in memory.

Generators commonly use `yield`.

### Example

```python
def numbers():
    for i in range(5):
        yield i

for number in numbers():
    print(number)
```

The values are generated one by one.

Compare this with:

```python
numbers = [0, 1, 2, 3, 4]
```

The list stores all five values in memory.

A generator is especially useful for large data:

```python
def read_large_file(file):
    for line in file:
        yield line
```

### Interview Point

Lists are useful when you need the complete collection and repeated access. Generators are useful for large or streaming data because they are **lazy and memory-efficient**.

---

## 6. What is the GIL?

### Answer

GIL stands for **Global Interpreter Lock**.

In traditional CPython execution, the GIL allows only one thread at a time to execute Python bytecode within a process.

This means Python threads are generally not ideal for **CPU-heavy Python code**.

### Example

```python
def calculate():
    total = 0

    for i in range(10_000_000):
        total += i
```

Using multiple Python threads may not provide the expected CPU parallelism for this kind of work.

For CPU-bound work, **multiprocessing** or other parallel approaches can be more appropriate.

For I/O-bound work such as:

```text
network requests
file operations
database calls
```

threads or asynchronous programming can still be very useful.

### Interview Point

The GIL is primarily a CPython implementation detail. Modern CPython also has optional free-threaded builds, so avoid saying that Python can *never* execute multiple threads.

---

## 7. Difference between `@staticmethod`, `@classmethod`, and instance methods?

### Answer

Python classes commonly have three types of methods.

### Instance Method

Receives `self`.

```python
class Student:
    def greet(self):
        print("Hello")
```

Use it when the method needs information from a particular object.

### Class Method

Receives `cls`.

```python
class Student:
    school = "ABC School"

    @classmethod
    def get_school(cls):
        return cls.school
```

It works with class-level data.

### Static Method

Receives neither `self` nor `cls`.

```python
class Math:
    @staticmethod
    def add(a, b):
        return a + b
```

It is essentially a normal function placed inside the class namespace because it logically belongs there.

### Easy Way to Remember

```text
self      → object
cls       → class
nothing   → static method
```

---

## 8. What are Python decorators?

### Answer

A decorator is a callable that **wraps another function or class** and adds or changes its behavior without modifying the original source code.

### Example

```python
from functools import wraps

def logger(func):
    @wraps(func)
    def wrapper(*args, **kwargs):
        print("Function started")
        result = func(*args, **kwargs)
        print("Function finished")
        return result

    return wrapper
```

Use it like this:

```python
@logger
def greet():
    print("Hello")

greet()
```

Output:

```text
Function started
Hello
Function finished
```

The syntax:

```python
@logger
def greet():
    ...
```

is essentially equivalent to:

```python
greet = logger(greet)
```

Common uses include:

```text
logging
authentication
caching
timing
validation
authorization
```

### Interview Point

In real decorators, `functools.wraps` is commonly used so metadata such as the wrapped function's name and docstring is preserved.

---

## 9. Explain list comprehension vs generator expression.

### Answer

Both provide a concise way to generate values.

### List Comprehension

```python
numbers = [x * 2 for x in range(5)]

print(numbers)
# [0, 2, 4, 6, 8]
```

The complete list is created immediately.

### Generator Expression

```python
numbers = (x * 2 for x in range(5))

print(numbers)
# generator object
```

Values are generated only when needed:

```python
for number in numbers:
    print(number)
```

### When to Use Which?

Use a **list** when you need all values immediately or need to reuse the collection.

Use a **generator** when processing potentially large data or when you only need to iterate once.

---

## 10. What is `__init__` vs `__new__`?

### Answer

`__new__` is responsible for **creating and returning an instance**.

`__init__` is responsible for **initializing that instance**.

The order is roughly:

```text
__new__()
   ↓
object created
   ↓
__init__()
   ↓
object initialized
```

### Example

```python
class Person:

    def __new__(cls, name):
        print("Creating object")
        return super().__new__(cls)

    def __init__(self, name):
        print("Initializing object")
        self.name = name
```

When we do:

```python
p = Person("John")
```

Output:

```text
Creating object
Initializing object
```

### Interview Point

You normally override `__init__`. `__new__` is mainly needed for advanced cases such as immutable types or custom object creation.

---

## 11. What are dunder/magic methods?

### Answer

Dunder means **double underscore**.

These are special methods that allow Python objects to work with built-in operations and protocols.

Examples:

```text
__init__
__str__
__repr__
__len__
__eq__
__add__
__enter__
__exit__
```

### Example

```python
class Person:
    def __init__(self, name):
        self.name = name

    def __str__(self):
        return self.name
```

Now:

```python
person = Person("John")

print(person)
```

Python effectively uses:

```python
person.__str__()
```

Similarly:

```python
len(obj)
```

can invoke:

```python
obj.__len__()
```

### Interview Point

Dunder methods allow custom classes to participate naturally in Python's protocols and operators.

---

## 12. How does Python handle memory management?

### Answer

Python manages memory automatically.

In CPython, an important mechanism is **reference counting**.

For example:

```python
a = [1, 2, 3]
b = a
```

Both `a` and `b` reference the same list.

When references are removed:

```python
del a
del b
```

the object can become unreachable and its memory can be reclaimed.

Python also has a **cyclic garbage collector** that handles reference cycles.

For example:

```python
a = []
b = []

a.append(b)
b.append(a)
```

These objects reference each other, forming a cycle.

### Interview Point

Python uses automatic memory management. CPython primarily uses reference counting plus cyclic garbage collection.

---

## 13. What is the difference between `deepcopy` and `shallow copy`?

### Answer

A **shallow copy** creates a new outer object but keeps references to nested objects.

A **deep copy** recursively copies nested objects too.

### Example

```python
import copy

original = [[1, 2], [3, 4]]

shallow = copy.copy(original)
deep = copy.deepcopy(original)
```

Now:

```python
shallow[0].append(100)

print(original)
# [[1, 2, 100], [3, 4]]
```

The nested list is shared, so the original is also affected.

But:

```python
deep[0].append(200)

print(original)
# [[1, 2, 100], [3, 4]]
```

The deep copy has its own nested objects.

### Easy Way to Remember

```text
Shallow copy:
new outer object → same nested objects

Deep copy:
new outer object → new nested objects
```

---

## 14. Explain `/` and `*` as parameter separators.

### Answer

`/` means parameters before it are **positional-only**.

`*` means parameters after it are **keyword-only**.

### Positional-Only

```python
def greet(name, /):
    print(name)

greet("John")       # valid
greet(name="John")  # TypeError
```

### Keyword-Only

```python
def greet(name, *, message):
    print(name, message)

greet("John", message="Hello")
```

But this is invalid:

```python
greet("John", "Hello")
```

because `message` must be supplied by keyword.

### Interview Point

These separators help create clear APIs and can make future parameter-name changes safer.

---

## 15. What is EAFP vs LBYL?

### Answer

EAFP means:

> Easier to Ask for Forgiveness than Permission.

Instead of checking first, you perform the operation and handle an exception if necessary.

### EAFP

```python
try:
    value = data["name"]
except KeyError:
    value = "Unknown"
```

LBYL means:

> Look Before You Leap.

You check before performing the operation.

```python
if "name" in data:
    value = data["name"]
else:
    value = "Unknown"
```

Python often favors EAFP because the operation itself can be the best test, especially when the state could change between checking and using it.

### Interview Point

Neither approach is universally better. Choose based on readability, expected failures, and the operation involved.

---

## 16. What does `if __name__ == "__main__":` do?

### Answer

Python gives every module a special variable called `__name__`.

If a file is run directly:

```bash
python app.py
```

then:

```python
__name__ == "__main__"
```

If the file is imported:

```python
import app
```

then:

```python
__name__ == "app"
```

### Example

```python
def main():
    print("Application started")


if __name__ == "__main__":
    main()
```

This means `main()` runs when the file is executed directly but not simply because another file imports it.

### Interview Point

This pattern helps keep executable code separate from reusable module code and reduces unwanted import-time side effects.

---

## 17. Difference between `range` and `xrange`?

### Answer

This is mainly a **Python 2 vs Python 3** question.

In Python 2:

```python
range(1000000)
```

created a list.

`xrange()` generated values lazily.

In Python 3, `xrange()` was removed and `range()` behaves like the old lazy `xrange()`.

```python
numbers = range(1_000_000)
```

This does not create a million-element list.

### Interview Point

In modern Python, use `range()`. There is no `xrange()`.

---

## 18. What are context managers? How do you write one?

### Answer

Context managers manage resources automatically, especially setup and cleanup.

They are commonly used with:

```python
with
```

### Example: File

```python
with open("data.txt") as file:
    content = file.read()
```

When the `with` block finishes, Python automatically closes the file.

Without a context manager, you'd need:

```python
file = open("data.txt")

try:
    content = file.read()
finally:
    file.close()
```

### Creating Your Own Context Manager

A class-based context manager implements:

```python
__enter__()
__exit__()
```

Example:

```python
class MyContext:
    def __enter__(self):
        print("Entering")
        return self

    def __exit__(self, exc_type, exc_value, traceback):
        print("Exiting")


with MyContext():
    print("Inside")
```

You can also use `contextlib.contextmanager` for simpler cases.

### Interview Point

Context managers are useful whenever something must be reliably cleaned up, such as files, locks, database transactions, or connections.

---

## 19. Explain `pass`, `continue`, and `break`.

### Answer

They have completely different purposes.

### `pass`

Does nothing.

```python
def future_function():
    pass
```

Useful as a placeholder.

### `continue`

Skips the current iteration.

```python
for i in range(5):
    if i == 2:
        continue

    print(i)
```

Output:

```text
0
1
3
4
```

### `break`

Stops the loop completely.

```python
for i in range(5):
    if i == 2:
        break

    print(i)
```

Output:

```text
0
1
```

### Easy Way to Remember

```text
pass     → do nothing
continue → skip this iteration
break    → stop the loop
```

---

## 20. What is the difference between `append()` and `extend()`?

### Answer

`append()` adds **one object** to the list.

`extend()` adds the elements of an iterable individually.

### `append()`

```python
numbers = [1, 2]

numbers.append([3, 4])

print(numbers)
# [1, 2, [3, 4]]
```

### `extend()`

```python
numbers = [1, 2]

numbers.extend([3, 4])

print(numbers)
# [1, 2, 3, 4]
```

### Easy Way to Remember

```text
append → add one item
extend → add multiple items
```

---

## 21. How do you swap two variables in Python?

### Answer

Python supports tuple unpacking, so you don't need a temporary variable.

```python
a = 10
b = 20

a, b = b, a

print(a)
# 20

print(b)
# 10
```

Python evaluates the right-hand side first and then assigns the values.

The traditional approach would be:

```python
temp = a
a = b
b = temp
```

Python's approach is cleaner and idiomatic.

---

## 22. What is a lambda function? What are its limitations?

### Answer

A lambda is a small anonymous function containing a single expression.

```python
square = lambda x: x * x

print(square(5))
# 25
```

A common use is with functions such as `sorted()`:

```python
students = [
    ("John", 25),
    ("Alice", 20),
    ("Bob", 22)
]

students.sort(key=lambda student: student[1])
```

Lambdas are designed for simple expressions, not complex multi-statement logic.

For complex logic, use `def`:

```python
def calculate_tax(amount):
    # complex logic
    ...
```

### Interview Point

Use lambda for small, simple functions. Don't force complex logic into a lambda just to make the code shorter.

---

## 23. Explain Python's LEGB rule.

### Answer

LEGB describes how Python searches for a variable name.

```text
L → Local
E → Enclosing
G → Global
B → Built-in
```

### Example

```python
x = "global"

def outer():
    x = "enclosing"

    def inner():
        x = "local"
        print(x)

    inner()

outer()
```

Output:

```text
local
```

Python first searches the local scope.

If it doesn't find the variable, it checks the enclosing scope, then global scope, then built-ins.

`nonlocal` can modify an enclosing variable, while `global` refers to a module-level variable.

---

## 24. What is `zip()`? What about unpacking?

### Answer

`zip()` combines elements from multiple iterables.

```python
names = ["John", "Alice", "Bob"]
ages = [25, 30, 22]

result = zip(names, ages)

print(list(result))
```

Output:

```python
[
    ("John", 25),
    ("Alice", 30),
    ("Bob", 22)
]
```

By default, `zip()` stops when the shortest iterable is exhausted.

### Unpacking with `zip(*)`

```python
pairs = [(1, "a"), (2, "b"), (3, "c")]

numbers, letters = zip(*pairs)

print(numbers)
# (1, 2, 3)

print(letters)
# ('a', 'b', 'c')
```

Here `*pairs` unpacks the list into separate arguments to `zip()`.

---

## 25. Difference between `remove`, `pop`, and `del` for lists?

### Answer

They all remove elements, but they work differently.

### `remove()`

Removes the first matching **value**.

```python
numbers = [10, 20, 30, 20]

numbers.remove(20)

print(numbers)
# [10, 30, 20]
```

### `pop()`

Removes an element by **index** and returns it.

```python
numbers = [10, 20, 30]

value = numbers.pop(1)

print(value)
# 20
```

### `del`

Deletes an element or slice.

```python
numbers = [10, 20, 30]

del numbers[1]

print(numbers)
# [10, 30]
```

### Easy Way to Remember

```text
remove → value
pop    → index + returns item
del    → delete by index/slice
```

---

## 26. What are f-strings? What are their advantages?

### Answer

F-strings provide a clean way to insert expressions into strings.

```python
name = "John"
age = 25

message = f"My name is {name} and I am {age} years old."

print(message)
```

Output:

```text
My name is John and I am 25 years old.
```

You can also put expressions inside them:

```python
a = 10
b = 20

print(f"Total = {a + b}")
```

Output:

```text
Total = 30
```

They also support formatting:

```python
price = 1234.5678

print(f"{price:.2f}")
# 1234.57
```

### Interview Point

F-strings are generally more readable than older `%` formatting and `.format()` for modern Python code.

---

## 27. How does exception handling work? What are `else` and `finally`?

### Answer

Python uses:

```text
try
except
else
finally
```

### Example

```python
try:
    result = 10 / 0

except ZeroDivisionError:
    print("Cannot divide by zero")

else:
    print("Calculation successful")

finally:
    print("This always runs")
```

The flow is:

```text
try
 ↓
exception?
 ├── yes → except
 └── no  → else
 ↓
finally
```

- `try` → code that might raise an exception
- `except` → handles the exception
- `else` → runs when no exception occurs
- `finally` → runs regardless of success or failure

### Interview Point

Prefer specific exceptions over a bare `except`.

For example:

```python
except ValueError:
    ...
```

is usually better than:

```python
except:
    ...
```

---

## 28. What is `None`? Is it a singleton?

### Answer

`None` represents the absence of a value.

For example:

```python
result = None
```

It does not mean zero, false, or an empty string:

```text
None ≠ 0
None ≠ False
None ≠ ""
```

There is only one `None` object, so the recommended check is:

```python
if result is None:
    print("No result")
```

Not:

```python
if result == None:
    ...
```

### Interview Point

Use `is None` because you're checking whether the object is specifically the `None` singleton.

---

## 29. Explain duck typing.

### Answer

Duck typing means Python generally cares about **what an object can do**, rather than what class it belongs to.

The idea is:

> If it behaves like a duck, we can treat it like a duck.

### Example

```python
def make_sound(animal):
    animal.sound()
```

We don't necessarily care whether `animal` is a `Dog`, `Cat`, or another class.

As long as it has:

```python
sound()
```

it can work with the function.

```python
class Dog:
    def sound(self):
        print("Woof")


class Cat:
    def sound(self):
        print("Meow")
```

Both work:

```python
make_sound(Dog())
make_sound(Cat())
```

### Interview Point

Python often uses behavior-based interfaces rather than requiring inheritance from a common base class.

---

## 30. What is the difference between modules and packages?

### Answer

A **module** is generally a Python file.

For example:

```text
calculator.py
```

A **package** is a way to organize multiple modules into a namespace.

Example:

```text
myapp/
    __init__.py
    users.py
    payments.py
    orders.py
```

Here:

```text
users.py       → module
payments.py    → module
myapp/         → package
```

You can import:

```python
from myapp import users
```

Modern Python also supports **namespace packages**, so `__init__.py` is not always required.

---

## 31. How do virtual environments work?

### Answer

A virtual environment creates an isolated Python environment for a project.

For example:

```bash
python -m venv .venv
```

You then activate it and install project dependencies.

This prevents projects from interfering with each other.

For example:

```text
Project A
Django 4.x

Project B
Django 5.x
```

Both projects can use different versions.

Without virtual environments, installing a package globally can create dependency conflicts.

### Interview Point

A virtual environment isolates project-specific Python packages and executables from the system/global environment.

---

## 32. What is `pip` vs `poetry` vs `pipenv`?

### Answer

They solve related but different parts of Python dependency management.

### `pip`

Primarily a package installer.

```bash
pip install requests
```

You can commonly manage dependencies using:

```text
requirements.txt
```

### Poetry

Provides dependency management, lockfiles, packaging, and project configuration.

```bash
poetry add requests
```

### Pipenv

Combines package management and virtual-environment management, using files such as:

```text
Pipfile
Pipfile.lock
```

### Interview Point

A simple way to answer:

> `pip` is primarily a package installer, while Poetry and Pipenv provide more complete dependency/project management workflows.

---

## 33. Explain `collections.defaultdict` and `Counter`.

### Answer

Both are available from Python's `collections` module.

### `defaultdict`

It automatically creates a default value when a key doesn't exist.

```python
from collections import defaultdict

groups = defaultdict(list)

groups["developers"].append("John")
groups["developers"].append("Alice")

print(groups)
```

Conceptually:

```python
{
    "developers": ["John", "Alice"]
}
```

Without `defaultdict`, you'd often need to check whether the key exists first.

### `Counter`

Used to count objects.

```python
from collections import Counter

letters = Counter("banana")

print(letters)
```

Conceptually:

```python
{
    "a": 3,
    "n": 2,
    "b": 1
}
```

You can also get the most common items:

```python
letters.most_common(2)
```

### Interview Point

Think:

```text
defaultdict → automatic default values
Counter     → frequency counting
```

---

## 34. What is `enumerate()`?

### Answer

`enumerate()` lets you iterate over both the **index and value** without manually maintaining a counter.

Instead of:

```python
names = ["John", "Alice", "Bob"]

i = 0

for name in names:
    print(i, name)
    i += 1
```

Use:

```python
for i, name in enumerate(names):
    print(i, name)
```

Output:

```text
0 John
1 Alice
2 Bob
```

You can also choose the starting number:

```python
for i, name in enumerate(names, start=1):
    print(i, name)
```

Output:

```text
1 John
2 Alice
3 Bob
```

### Interview Point

Use `enumerate()` when you need both the position and the value while iterating.

---

## 35. Difference between `str` and `repr`?

### Answer

Both are used to represent objects as strings, but they have different purposes.

`str()` is generally intended to be **human-friendly**.

`repr()` is generally intended to be **developer-friendly and unambiguous**.

### Example

```python
class User:
    def __init__(self, name):
        self.name = name

    def __str__(self):
        return self.name

    def __repr__(self):
        return f"User(name={self.name!r})"
```

Then:

```python
user = User("John")

print(str(user))
# John

print(repr(user))
# User(name='John')
```

### Interview Point

Think:

```text
str  → user-friendly display
repr → developer/debugging representation
```

The idea that `repr()` should be `eval()`-able is a goal for some objects, not a universal guarantee.

---

## 36. How do you read a large file efficiently?

### Answer

Don't load the entire file into memory if it is very large.

Instead, process it line by line:

```python
with open("large_file.txt") as file:
    for line in file:
        process(line)
```

Python's file iterator reads the file incrementally.

Avoid this for very large files:

```python
content = file.read()
```

because it can require a large amount of memory.

For binary or specially structured data, chunked reads can also be useful:

```python
while chunk := file.read(8192):
    process(chunk)
```

### Interview Point

For large files, streaming/iteration is usually preferable to loading everything into memory at once.

---

## 37. What are type hints? Are they enforced?

### Answer

Type hints allow us to describe what types a function expects and returns.

```python
def add(a: int, b: int) -> int:
    return a + b
```

This makes the code easier to understand and allows tools such as:

```text
mypy
Pyright
IDEs
```

to detect potential type problems.

However, Python generally **does not enforce annotations at runtime**.

For example:

```python
def add(a: int, b: int) -> int:
    return a + b

add("10", "20")
```

Python doesn't automatically reject this just because the annotations say `int`.

### Interview Point

Type hints are primarily for documentation, static analysis, tooling, and developer experience.

---

## 38. What are `dataclasses`?

### Answer

`dataclasses` make it easier to create classes that mainly store data.

Without a dataclass:

```python
class User:
    def __init__(self, name, age):
        self.name = name
        self.age = age
```

With a dataclass:

```python
from dataclasses import dataclass

@dataclass
class User:
    name: str
    age: int
```

Python can automatically provide methods such as:

```text
__init__
__repr__
__eq__
```

Example:

```python
user = User("John", 25)

print(user)
```

Output:

```text
User(name='John', age=25)
```

Dataclasses can also support:

```text
default values
frozen instances
slots
ordering
```

### Interview Point

Use dataclasses when you need a concise class primarily intended to hold structured data.

---

## 39. Explain the walrus operator `:=`.

### Answer

The walrus operator `:=` is called an **assignment expression**.

It allows you to assign a value and use that value in the same expression.

### Example

```python
while (line := file.readline()):
    print(line)
```

Here:

```python
line := file.readline()
```

does three things:

1. Reads a line.
2. Assigns it to `line`.
3. Produces the value for the `while` condition.

Another example:

```python
if (length := len("Python")) > 5:
    print(length)
```

Output:

```text
6
```

### Interview Point

The walrus operator is useful when a value needs to be calculated and immediately tested, but don't use it when it makes the code harder to read.

---

## 40. What is the difference between `async def` and normal `def`?

### Answer

A normal `def` creates a regular function that executes synchronously when called.

```python
def greet():
    return "Hello"
```

An `async def` creates a **coroutine function**.

```python
async def greet():
    return "Hello"
```

Calling an async function doesn't directly give you the final result:

```python
result = greet()
```

Instead, you normally use:

```python
result = await greet()
```

inside another async function.

### Example

```python
import asyncio

async def fetch_data():
    await asyncio.sleep(1)
    return "Data received"


async def main():
    result = await fetch_data()
    print(result)


asyncio.run(main())
```

Async programming is especially useful for many I/O-bound operations, such as:

```text
API requests
network connections
database operations
web servers
```

The important idea is that while one operation is waiting, the event loop can work on another task.

### Interview Point

`async def` doesn't automatically make code faster. It is mainly useful for handling many concurrent I/O-bound operations efficiently. Blocking synchronous code inside an async function can still block the event loop.

---

# Questions 41–60: Data Structures & Algorithms

## 41. What is the time complexity of common list operations?

### Answer

Python lists are implemented as **dynamic arrays**, so different operations have different time complexities.

| Operation | Typical Complexity |
|---|---:|
| Access by index `list[i]` | O(1) |
| Append `append()` | O(1) amortized |
| Pop from end `pop()` | O(1) |
| Insert at beginning | O(n) |
| Delete from beginning | O(n) |
| Search / membership `x in list` | O(n) |
| Sort `sort()` | O(n log n) |

### Example

```python
numbers = [10, 20, 30, 40]

print(numbers[2])  # O(1)

numbers.append(50)  # O(1) amortized
```

But inserting at the beginning is expensive:

```python
numbers.insert(0, 5)  # O(n)
```

Why? Existing elements need to be shifted to make space.

### Interview Point

Remember:

```text
indexing       → O(1)
append         → O(1) amortized
search         → O(n)
insert/delete front → O(n)
sorting        → O(n log n)
```

---

## 42. What is the time complexity of dictionary and set operations?

### Answer

Python dictionaries and sets are implemented using **hash tables**.

Typical operations have **average O(1)** complexity:

```text
get
set
delete
membership
```

### Example

```python
user = {
    "name": "John",
    "age": 25
}

print(user["name"])  # Average O(1)

user["city"] = "Delhi"  # Average O(1)

print("age" in user)  # Average O(1)
```

Similarly, sets provide fast membership checks:

```python
numbers = {10, 20, 30, 40}

print(30 in numbers)
# True
```

In unusual worst-case collision scenarios, operations can degrade toward O(n).

Dictionary and set keys/elements must be **hashable**.

For example:

```python
data = {
    (1, 2): "Point"
}
```

works because a tuple containing hashable values is hashable.

But:

```python
# data = {
#     [1, 2]: "Point"
# }
```

doesn't work because lists are unhashable.

### Interview Point

Think:

```text
dict/set lookup → average O(1)
list lookup     → O(n)
```

---

## 43. When would you use a `deque`?

### Answer

Use `collections.deque` when you need efficient insertion and removal from **both ends** of a collection.

```python
from collections import deque
```

A deque supports approximately O(1) operations at either end.

### Example

```python
from collections import deque

queue = deque()

queue.append("A")
queue.append("B")
queue.append("C")

print(queue.popleft())
# A

print(queue)
# deque(['B', 'C'])
```

With a normal list:

```python
items = ["A", "B", "C"]

items.pop(0)
```

removing from the beginning is O(n) because the remaining elements need to shift.

### Common Uses

```text
queues
BFS
sliding windows
task processing
append/pop from both ends
```

### Interview Point

Use:

```text
list  → fast access by index
deque → fast operations at both ends
```

---

## 44. How do you reverse a string or list?

### Answer

There are several ways depending on whether you need a new object or want to modify a list in place.

### Reverse a String

Strings are immutable, so slicing creates a new string:

```python
text = "Python"

reversed_text = text[::-1]

print(reversed_text)
# nohtyP
```

You can also use `reversed()`:

```python
text = "Python"

reversed_text = "".join(reversed(text))

print(reversed_text)
# nohtyP
```

### Reverse a List In Place

```python
numbers = [1, 2, 3, 4]

numbers.reverse()

print(numbers)
# [4, 3, 2, 1]
```

### Create a Reversed List

```python
numbers = [1, 2, 3, 4]

result = numbers[::-1]

print(result)
# [4, 3, 2, 1]
```

You can also use:

```python
result = list(reversed(numbers))
```

### Interview Point

Know the difference:

```text
[::-1]       → creates a reversed copy
reverse()    → modifies the list in place
reversed()   → returns a reverse iterator
```

---

## 45. Explain Big-O notation briefly.

### Answer

**Big-O notation** describes how the time or memory requirements of an algorithm grow as the input size increases.

For example, suppose we search a list:

```python
numbers = [10, 20, 30, 40, 50]
```

A linear search may have to check every element:

```python
for number in numbers:
    if number == target:
        ...
```

This is **O(n)**.

If the list doubles in size, the amount of work can roughly double.

### Common Complexities

```text
O(1)       → constant
O(log n)   → logarithmic
O(n)       → linear
O(n log n) → linearithmic
O(n²)      → quadratic
O(2ⁿ)      → exponential
```

### Example

```python
# O(1)
print(numbers[0])

# O(n)
for number in numbers:
    print(number)

# O(n²)
for a in numbers:
    for b in numbers:
        print(a, b)
```

### Interview Point

When analyzing Big-O, focus on the **dominant growth term** and usually ignore constants.

For example:

```text
O(2n + 10) → O(n)
O(n² + n)  → O(n²)
```

---

## 46. How would you find duplicates in a list?

### Answer

A simple and efficient approach is to maintain a set of values we've already seen.

### Example

```python
numbers = [1, 2, 3, 2, 4, 1, 5]

seen = set()
duplicates = set()

for number in numbers:
    if number in seen:
        duplicates.add(number)
    else:
        seen.add(number)

print(duplicates)
# {1, 2}
```

### Complexity

Average time:

```text
O(n)
```

because set membership is average O(1).

Extra space:

```text
O(n)
```

in the worst case.

### Using `Counter`

If you also need frequencies:

```python
from collections import Counter

numbers = [1, 2, 3, 2, 4, 1, 5]

counts = Counter(numbers)

duplicates = [
    number
    for number, count in counts.items()
    if count > 1
]

print(duplicates)
# [1, 2]
```

### Alternative

Sorting first and comparing adjacent values takes O(n log n), but can be useful when you want to avoid hash-based storage.

---

## 47. What is a hash collision? How does Python handle it?

### Answer

A **hash collision** happens when two different hashable objects produce the same hash value.

For example, conceptually:

```text
key A → hash → bucket X
key B → hash → bucket X
```

The hash table must distinguish between the keys even though their hashes collide.

Python's dictionary implementation handles collisions internally using its hash-table strategy, including probing.

### Important Point

A collision does **not** mean Python treats the two keys as equal.

Python uses equality as well as hashing.

Conceptually, dictionary lookup involves:

```text
1. Calculate hash(key)
2. Find a candidate location
3. Compare keys for equality when necessary
4. Resolve collisions internally
```

### Example

```python
data = {
    "name": "John",
    "age": 25
}
```

You don't normally need to handle collisions yourself.

### Interview Point

Hash collisions are expected and are handled internally. Too many collisions can degrade performance, but dictionary correctness is maintained through hash and equality checks.

---

## 48. What is the conceptual difference between an array/list and a linked list?

### Answer

An array-like structure stores elements in a way that allows efficient indexing.

A linked list stores elements as nodes connected through references.

### Array/List

Conceptually:

```text
[10][20][30][40]
```

Accessing an element by index is fast:

```python
numbers[2]
```

approximately:

```text
O(1)
```

But inserting in the middle may require shifting elements:

```text
[10][20][30][40]
      ↓ insert
[10][15][20][30][40]
```

### Linked List

Conceptually:

```text
[10 | next] → [20 | next] → [30 | next]
```

Each node points to another node.

Accessing the third element requires walking through the nodes:

```text
10 → 20 → 30
```

so access is typically O(n).

If you already have the correct node/reference, insertion or deletion can be O(1).

### Python

Python's built-in `list` is a dynamic array.

Python's `collections.deque` is implemented using a specialized linked/block structure designed for efficient operations at both ends; it is not a general-purpose linked-list replacement.

### Interview Point

```text
List/array:
fast indexing
expensive middle insertion/deletion

Linked list:
slow indexing
efficient insertion/deletion when node is known
```

---

## 49. Explain stack vs queue.

### Answer

A **stack** follows **LIFO**:

> Last In, First Out.

A **queue** follows **FIFO**:

> First In, First Out.

### Stack Example

Think of a stack of plates.

```text
Push 10
Push 20
Push 30

Pop → 30
```

Python example:

```python
stack = []

stack.append(10)
stack.append(20)
stack.append(30)

print(stack.pop())
# 30
```

### Queue Example

Think of people standing in line.

```text
A enters
B enters
C enters

A leaves first
```

Python example:

```python
from collections import deque

queue = deque()

queue.append("A")
queue.append("B")
queue.append("C")

print(queue.popleft())
# A
```

### Interview Point

```text
Stack → LIFO → list/deque
Queue → FIFO → deque
```

---

## 50. How do you implement a FIFO queue in Python?

### Answer

The preferred general-purpose choice is `collections.deque`.

### Example

```python
from collections import deque

queue = deque()

queue.append("Task 1")
queue.append("Task 2")
queue.append("Task 3")

print(queue.popleft())
# Task 1

print(queue.popleft())
# Task 2
```

Adding at the right:

```python
queue.append(item)
```

Removing from the left:

```python
queue.popleft()
```

Both ends are designed for efficient operations.

### Why Not `list.pop(0)`?

This works:

```python
queue = ["A", "B", "C"]

queue.pop(0)
```

but removing from the front of a list is O(n).

### Thread-Safe Queues

For communication between threads, use:

```python
from queue import Queue
```

`queue.Queue` provides thread-safe operations.

### Interview Point

Use:

```text
deque  → normal FIFO queue
Queue  → thread-safe queue
```

---

## 51. What is binary search? What are its requirements?

### Answer

Binary search finds an item in **sorted data** by repeatedly dividing the search range in half.

### Example

Suppose we have:

```text
[10, 20, 30, 40, 50, 60, 70]
```

To search for `60`, binary search checks the middle and decides whether to search the left or right half.

Conceptually:

```text
Search entire range
        ↓
Check middle
        ↓
Target larger?
        ↓
Search right half
        ↓
Repeat
```

The search space is cut approximately in half each time.

### Complexity

```text
Time → O(log n)
```

### Python's `bisect`

Python provides the `bisect` module for working with sorted lists.

```python
from bisect import bisect_left

numbers = [10, 20, 30, 40, 50]

index = bisect_left(numbers, 30)

print(index)
# 2
```

### Requirement

The data must be sorted for ordinary binary search.

A related use is searching a **monotonic predicate**, where once a condition becomes true (or false), it stays that way.

---

## 52. Explain recursion vs iteration.

### Answer

**Recursion** means a function calls itself.

**Iteration** means using loops such as `for` or `while`.

### Recursion Example

```python
def factorial(n):
    if n == 0:
        return 1

    return n * factorial(n - 1)

print(factorial(5))
# 120
```

The function repeatedly calls itself.

### Iterative Version

```python
def factorial(n):
    result = 1

    for i in range(1, n + 1):
        result *= i

    return result
```

### Recursion Is Useful For

```text
trees
graphs
divide-and-conquer
backtracking
recursive data structures
```

### Iteration Is Often Better When

```text
a simple loop is enough
deep recursion is possible
memory efficiency matters
```

Python does not perform general tail-call optimization, so deep recursion can hit the recursion limit.

### Interview Point

Recursion can make tree and divide-and-conquer algorithms easier to express, but iteration often avoids function-call overhead and recursion-depth limitations.

---

## 53. What is a heap? When would you use `heapq`?

### Answer

A **heap** is a tree-based data structure that maintains a priority relationship.

Python's `heapq` module provides a **min-heap**.

The smallest element is available at the root.

### Example

```python
import heapq

numbers = [5, 2, 8, 1, 3]

heapq.heapify(numbers)

print(numbers[0])
# 1
```

You can add an item:

```python
heapq.heappush(numbers, 0)
```

And remove the smallest:

```python
smallest = heapq.heappop(numbers)
```

### Common Uses

```text
priority queues
top-k problems
merging sorted streams
scheduling
Dijkstra's algorithm
```

### Max-Heap

Traditionally, a max-heap can be simulated by storing negative values:

```python
heap = []

heapq.heappush(heap, -10)
heapq.heappush(heap, -30)

largest = -heapq.heappop(heap)

print(largest)
# 30
```

### Interview Point

If you need repeated access to the smallest/highest-priority item without fully sorting everything, think **heap**.

---

## 54. How do you merge two sorted lists?

### Answer

Use the **two-pointer technique**.

Suppose:

```python
a = [1, 4, 7]
b = [2, 3, 8]
```

Compare the first unused element from each list and append the smaller one.

### Example

```python
def merge_sorted(a, b):
    i = 0
    j = 0
    result = []

    while i < len(a) and j < len(b):
        if a[i] <= b[j]:
            result.append(a[i])
            i += 1
        else:
            result.append(b[j])
            j += 1

    result.extend(a[i:])
    result.extend(b[j:])

    return result


print(merge_sorted([1, 4, 7], [2, 3, 8]))
# [1, 2, 3, 4, 7, 8]
```

### Complexity

If the lists contain `n` and `m` elements:

```text
Time  → O(n + m)
Space → O(n + m) for the output
```

Python also provides:

```python
import heapq

result = heapq.merge(a, b)
```

`heapq.merge()` returns an iterator and can lazily merge multiple sorted iterables.

### Interview Point

For two sorted lists, the two-pointer approach is usually the simplest and most efficient solution.

---

## 55. What is memoization?

### Answer

**Memoization** means caching the result of a function so that repeated calls with the same inputs don't repeat the same expensive computation.

A classic example is Fibonacci.

### Without Memoization

```python
def fib(n):
    if n <= 1:
        return n

    return fib(n - 1) + fib(n - 2)
```

This repeats many calculations.

### With `lru_cache`

```python
from functools import lru_cache

@lru_cache(maxsize=None)
def fib(n):
    if n <= 1:
        return n

    return fib(n - 1) + fib(n - 2)
```

Now previously calculated results are cached.

### Example

```python
print(fib(50))
```

The cached version is dramatically more efficient than the naive recursive version.

### Interview Point

Memoization is especially useful in:

```text
dynamic programming
recursive algorithms
Fibonacci-like problems
overlapping subproblems
```

Think:

```text
same input + same result
        ↓
cache it
```

---

## 56. Explain the sliding window pattern.

### Answer

The **sliding window** technique maintains a range of elements and moves that range through a sequence.

It is useful when a problem asks about a contiguous section of an array or string.

### Example: Maximum Sum of `k` Consecutive Elements

Suppose:

```python
numbers = [2, 1, 5, 1, 3, 2]
k = 3
```

A simple brute-force approach might calculate every group of three separately.

Instead, use a sliding window.

```python
def max_sum(numbers, k):
    window_sum = sum(numbers[:k])
    best = window_sum

    for i in range(k, len(numbers)):
        window_sum += numbers[i]
        window_sum -= numbers[i - k]

        best = max(best, window_sum)

    return best


print(max_sum([2, 1, 5, 1, 3, 2], 3))
# 9
```

The first window is:

```text
2 + 1 + 5 = 8
```

Move one position:

```text
1 + 5 + 1 = 7
```

Instead of recalculating the whole window, remove the outgoing value and add the incoming value.

### Complexity

Usually:

```text
O(n)
```

instead of repeatedly processing windows, which can lead to O(n × k).

### Common Uses

```text
maximum/minimum sum of a fixed window
longest substring
shortest substring satisfying a condition
frequency-based substring problems
```

### Interview Point

When you see **contiguous subarray/substring + optimize something**, consider the sliding-window pattern.

---

## 57. How do you detect a cycle in a linked list?

### Answer

A common solution is **Floyd's Cycle Detection Algorithm**, also called the **tortoise and hare algorithm**.

Use two pointers:

```text
slow → moves one step
fast → moves two steps
```

If there is a cycle, eventually they will meet.

### Example

```python
def has_cycle(head):
    slow = head
    fast = head

    while fast and fast.next:
        slow = slow.next
        fast = fast.next.next

        if slow is fast:
            return True

    return False
```

### Why Does It Work?

Without a cycle:

```text
1 → 2 → 3 → None
```

The fast pointer eventually reaches `None`.

With a cycle:

```text
1 → 2 → 3
    ↑     ↓
    ←  ←  4
```

The fast pointer eventually catches the slow pointer.

### Complexity

```text
Time  → O(n)
Space → O(1)
```

An alternative is storing visited nodes in a set, which uses O(n) extra space.

### Interview Point

For linked-list cycle detection, remember:

```text
slow = 1 step
fast = 2 steps
meet → cycle
```

---

## 58. What is the difference between BFS and DFS?

### Answer

Both are graph/tree traversal techniques.

### BFS — Breadth-First Search

BFS explores nodes **level by level**.

It commonly uses a queue.

```text
       A
      / \
     B   C
    / \
   D   E
```

BFS order:

```text
A → B → C → D → E
```

### Example

```python
from collections import deque

def bfs(graph, start):
    queue = deque([start])
    visited = {start}

    while queue:
        node = queue.popleft()
        print(node)

        for neighbor in graph[node]:
            if neighbor not in visited:
                visited.add(neighbor)
                queue.append(neighbor)
```

### DFS — Depth-First Search

DFS explores as deeply as possible before backtracking.

It can use recursion or an explicit stack.

```python
def dfs(graph, node, visited=None):
    if visited is None:
        visited = set()

    if node in visited:
        return

    visited.add(node)
    print(node)

    for neighbor in graph[node]:
        dfs(graph, neighbor, visited)
```

### When to Use

BFS is useful for:

```text
shortest path in an unweighted graph
level-order traversal
minimum number of steps
```

DFS is useful for:

```text
connectivity
cycle detection
backtracking
topological sorting
path existence
```

### Interview Point

Remember:

```text
BFS → Queue → Level by level
DFS → Stack/Recursion → Go deep first
```

For shortest paths, BFS gives the shortest number of edges in an **unweighted** graph.

---

## 59. What is a trie used for?

### Answer

A **trie**, or prefix tree, is a tree-like data structure designed for storing strings by their prefixes.

For example:

```text
car
cat
can
```

can share the prefix:

```text
ca
```

Conceptually:

```text
        root
         |
         c
         |
         a
       / | \
      r  t  n
```

### Common Uses

Tries are useful for:

```text
autocomplete
prefix search
dictionary lookup
spell checking
IP routing prefixes
word games
```

### Example Use Case

Suppose a user types:

```text
ca
```

An autocomplete system can quickly find words beginning with `ca`:

```text
car
cat
can
```

A hash set is excellent for exact lookup:

```text
"cat" exists?
```

But a trie is particularly useful for:

```text
"Give me all words starting with ca"
```

### Trade-off

Tries can use more memory than hash-based structures because they store many nodes and links.

### Interview Point

Think:

```text
Hash set → exact lookup
Trie     → prefix lookup
```

---

## 60. How would you find the k-th largest element?

### Answer

There are several approaches depending on the constraints.

Suppose:

```python
numbers = [7, 2, 9, 4, 1, 8]
k = 2
```

The sorted list is:

```text
[1, 2, 4, 7, 8, 9]
```

The 2nd largest value is:

```text
8
```

### Approach 1: Sorting

```python
numbers = [7, 2, 9, 4, 1, 8]
k = 2

numbers.sort(reverse=True)

print(numbers[k - 1])
# 8
```

Complexity:

```text
O(n log n)
```

This is simple and often perfectly acceptable.

### Approach 2: Min-Heap of Size `k`

If `k` is much smaller than `n`, maintain only the largest `k` elements.

```python
import heapq

numbers = [7, 2, 9, 4, 1, 8]
k = 2

heap = []

for number in numbers:
    heapq.heappush(heap, number)

    if len(heap) > k:
        heapq.heappop(heap)

print(heap[0])
# 8
```

Complexity:

```text
O(n log k)
```

This can be better when `k` is small compared with `n`.

### Approach 3: Quickselect

Quickselect can find the k-th element without fully sorting the data.

Its average time complexity is:

```text
O(n)
```

but its worst-case complexity can be O(n²) depending on pivot choices.

### Python Convenience

For simple code:

```python
import heapq

numbers = [7, 2, 9, 4, 1, 8]

result = heapq.nlargest(2, numbers)[-1]

print(result)
# 8
```

### Interview Point

Choose based on the problem:

```text
Need simple solution     → sort
k is small               → min-heap of size k
Need average O(n)        → Quickselect
```

---

# Quick Revision: Questions 41–60

| # | Topic | Remember |
|---|---|---|


---

## 3. OOP & Design Patterns (61–80)

### 61. What are the four pillars of OOP?

**Answer:** Encapsulation, Abstraction, Inheritance, Polymorphism. Python supports all; encapsulation is convention-based (`_protected`, `__name_mangling`).

#### Example

```python
class Animal:
    def speak(self):
        raise NotImplementedError

class Dog(Animal):
    def speak(self):
        return "Woof"

class Cat(Animal):
    def speak(self):
        return "Meow"

# Encapsulation: keep internal state behind methods/properties
# Abstraction: expose only what callers need
# Inheritance: Dog/Cat derive from Animal
# Polymorphism: both implement speak() differently
```

#### Better Understanding

Remember: **Encapsulation hides implementation, Abstraction hides complexity, Inheritance reuses a hierarchy, and Polymorphism lets one interface have multiple implementations.**

### 62. Difference between inheritance and composition?

**Answer:** Inheritance: “is-a” via subclassing. Composition: “has-a” via containing objects. Prefer composition for flexibility and looser coupling.

#### Example

```python
class Engine:
    def start(self):
        print("Engine started")

class Car:
    def __init__(self):
        self.engine = Engine()  # Car "has an" Engine

    def start(self):
        self.engine.start()

# Composition is often easier to change than a deep inheritance tree.
```

#### Better Understanding

Use inheritance for a genuine **is-a** relationship; use composition for a **has-a** relationship. Composition is usually more flexible.

### 63. What is MRO? How does Python resolve it?

**Answer:** Method Resolution Order — the order Python searches for attributes in multiple inheritance. C3 linearization; inspect with `Class.__mro__` or `help(Class)`.

#### Example

```python
class A:
    def value(self):
        return "A"

class B(A):
    def value(self):
        return "B"

class C(A):
    def value(self):
        return "C"

class D(B, C):
    pass

print(D.__mro__)
# Python uses C3 linearization to determine the lookup order.
```

#### Better Understanding

When multiple inheritance appears, inspect `Class.__mro__` to see exactly where Python looks for a method.

### 64. What is an abstract base class (ABC)?

**Answer:** `abc.ABC` + `@abstractmethod` define interfaces that subclasses must implement. Instantiating an incomplete ABC raises `TypeError`.

#### Example

```python
from abc import ABC, abstractmethod

class Payment(ABC):
    @abstractmethod
    def pay(self, amount):
        pass

class CardPayment(Payment):
    def pay(self, amount):
        return f"Paid {amount} by card"

# Payment() would raise TypeError because pay() is not implemented.
```

#### Better Understanding

ABCs are useful when you want to explicitly define a contract that subclasses must satisfy.

### 65. Explain polymorphism with an example.

**Answer:** Same interface, different behavior: `len()` works on str/list/dict via `__len__`. Or subclasses overriding `draw()` with different shapes.

#### Example

```python
class Dog:
    def speak(self):
        return "Woof"

class Cat:
    def speak(self):
        return "Meow"

def make_sound(animal):
    print(animal.speak())

make_sound(Dog())
make_sound(Cat())

# Same operation, different behavior.
```

#### Better Understanding

Polymorphism means callers can use the same interface without caring which concrete implementation they received.

### 66. What is the Singleton pattern? Concerns?

**Answer:** Ensure one instance. In Python: module-level object, metaclass, or `__new__`. Can hurt testability and hide dependencies; prefer DI when possible.

#### Example

```python
# In Python, a module itself is often the simplest singleton-like mechanism.
# config.py
settings = {"debug": False}

# Every import of config refers to the same module object.
```

#### Better Understanding

Singletons can make dependencies hidden and tests harder. Prefer ordinary objects passed through dependency injection unless a single shared instance is truly required.

### 67. What is the Factory pattern?

**Answer:** A function/class that creates objects without exposing construction logic. Useful when concrete type depends on config/runtime input.

#### Example

```python
class EmailSender:
    def send(self, message):
        return f"Email: {message}"

class SMSSender:
    def send(self, message):
        return f"SMS: {message}"

def create_sender(channel):
    if channel == "email":
        return EmailSender()
    if channel == "sms":
        return SMSSender()
    raise ValueError("Unsupported channel")

sender = create_sender("email")
```

#### Better Understanding

A factory centralizes object-creation decisions so the rest of the application does not need to know concrete classes.

### 68. What is Dependency Injection?

**Answer:** Pass dependencies into a class/function rather than creating them inside. Improves testability and decoupling (mock DB/repo in tests).

#### Example

```python
class UserService:
    def __init__(self, repository):
        self.repository = repository

    def get_user(self, user_id):
        return self.repository.get_by_id(user_id)

# Production:
service = UserService(real_repository)

# Test:
service = UserService(fake_repository)
```

#### Better Understanding

Dependency injection makes code easier to test because real databases, APIs, or services can be replaced with fakes or mocks.

### 69. Explain Repository pattern in backends.

**Answer:** Abstracts data access behind an interface (`UserRepository.get_by_id`). Services depend on the repo, not ORM details — cleaner layers and easier mocking.

#### Example

```python
class UserRepository:
    def get_by_id(self, user_id):
        # ORM/SQL details stay here
        ...

class UserService:
    def __init__(self, repo):
        self.repo = repo

    def profile(self, user_id):
        return self.repo.get_by_id(user_id)
```

#### Better Understanding

Keep business logic independent from database-specific code. This makes persistence easier to replace and tests easier to isolate.

### 70. What is the Strategy pattern?

**Answer:** Encapsulate interchangeable algorithms behind a common interface (e.g., payment processors, sort strategies). Swap at runtime without if/else sprawl.

#### Example

```python
class CardPayment:
    def pay(self, amount):
        return f"Card payment: {amount}"

class PayPalPayment:
    def pay(self, amount):
        return f"PayPal payment: {amount}"

class Checkout:
    def __init__(self, strategy):
        self.strategy = strategy

    def pay(self, amount):
        return self.strategy.pay(amount)

checkout = Checkout(CardPayment())
print(checkout.pay(100))
```

#### Better Understanding

Strategy is useful when several algorithms solve the same problem and you want to choose one at runtime instead of building a large conditional chain.

### 71. What is SOLID? Name each letter.

**Answer:** Single Responsibility, Open/Closed, Liskov Substitution, Interface Segregation, Dependency Inversion. Guides maintainable OOP design.

#### Example

```python
# SOLID
# S = Single Responsibility
# O = Open/Closed
# L = Liskov Substitution
# I = Interface Segregation
# D = Dependency Inversion
```

#### Better Understanding

SOLID is a set of design guidelines, not five rigid rules. Use them to reduce coupling and make change safer.

### 72. What is tight vs loose coupling?

**Answer:** Tight: components hardwired together; hard to change/test. Loose: interact via interfaces/events; easier to swap implementations.

#### Example

```python
# Tight coupling
class OrderService:
    def __init__(self):
        self.db = PostgreSQLDatabase()

# Looser coupling
class OrderService:
    def __init__(self, db):
        self.db = db
```

#### Better Understanding

Loose coupling makes it easier to replace implementations, test components independently, and change one layer without rewriting others.

### 73. Difference between composition and aggregation?

**Answer:** Both are “has-a”. Composition: owned lifecycle (part dies with whole). Aggregation: shared/independent lifecycle. Conceptual UML distinction.

#### Example

```python
class Engine:
    pass

class Car:
    def __init__(self):
        self.engine = Engine()  # composition: owned by Car

class Driver:
    def __init__(self, car):
        self.car = car  # aggregation-like relationship: Driver can exist independently
```

#### Better Understanding

The key idea is lifecycle ownership: in composition the part is conceptually owned by the whole; in aggregation the contained object can exist independently.

### 74. What are mixins?

**Answer:** Classes providing reusable methods via multiple inheritance without being standalone base types (e.g., `JsonSerializableMixin`). Keep them focused.

#### Example

```python
class JsonMixin:
    def to_json(self):
        import json
        return json.dumps(self.__dict__)

class User(JsonMixin):
    def __init__(self, name):
        self.name = name

print(User("Ana").to_json())
```

#### Better Understanding

Mixins should provide a small, focused capability rather than becoming large base classes with lots of unrelated behavior.

### 75. How does encapsulation work in Python?

**Answer:** No true private members. Convention: `_internal`, `__mangled`. Properties (`@property`) control access. Trust the developer culture.

#### Example

```python
class User:
    def __init__(self, password):
        self._password = password

    @property
    def password_length(self):
        return len(self._password)

# _password means "internal" by convention.
# __password would trigger name mangling.
```

#### Better Understanding

Python relies mostly on conventions rather than enforced private fields. Use `_name` for internal APIs and `__name` when name mangling is useful.

### 76. What is a property in Python?

**Answer:** `@property` turns a method into attribute-like access with getter/setter/deleter — validation without changing call sites to methods.

#### Example

```python
class User:
    def __init__(self, age):
        self._age = age

    @property
    def age(self):
        return self._age

    @age.setter
    def age(self, value):
        if value < 0:
            raise ValueError("Age cannot be negative")
        self._age = value

user = User(20)
user.age = 21
```

#### Better Understanding

Properties let you add validation or computed behavior while keeping a clean attribute-style API such as `user.age`.

### 77. Explain the Observer pattern.

**Answer:** Subject notifies registered observers on state change (events, pub/sub). Django signals and many event buses follow this idea.

#### Example

```python
class Subject:
    def __init__(self):
        self.observers = []

    def subscribe(self, callback):
        self.observers.append(callback)

    def notify(self, message):
        for callback in self.observers:
            callback(message)

subject = Subject()
subject.subscribe(print)
subject.notify("Order shipped")
```

#### Better Understanding

Observer is useful for event-driven systems, but too many hidden observers can make control flow difficult to understand and debug.

### 78. What is DRY, KISS, YAGNI?

**Answer:** Don’t Repeat Yourself; Keep It Simple Stupid; You Aren’t Gonna Need It. Avoid premature abstraction and unused features.

#### Example

```python
# DRY  -> don't duplicate the same logic
# KISS -> prefer a simple solution
# YAGNI -> don't build a feature before it is needed

# Good:
def calculate_total(price, tax):
    return price + tax

# Avoid copying the same calculation into five places.
```

#### Better Understanding

These principles complement each other: remove harmful duplication, keep solutions simple, and avoid speculative complexity.

### 79. When is inheritance a bad idea?

**Answer:** Deep hierarchies, fragile base classes, forcing “is-a” that isn’t true, sharing code that isn’t a true subtype. Prefer composition/mixins carefully.

#### Example

```python
# Avoid this when the relationship is not a true subtype:
class ReportExporter(FileStorage):
    pass

# Prefer composition:
class ReportExporter:
    def __init__(self, storage):
        self.storage = storage
```

#### Better Understanding

Inheritance becomes risky with deep hierarchies, fragile base classes, and classes that only inherit code for reuse. Composition is often safer.

### 80. What is an interface in Python terms?

**Answer:** No formal `interface` keyword. Use ABCs, Protocols (`typing.Protocol` — structural subtyping), or duck typing documentation.

---

## 4. Web Frameworks — Django / Flask / FastAPI (81–110)

#### Example

```python
from typing import Protocol

class Notifier(Protocol):
    def send(self, message: str) -> None:
        ...

class EmailNotifier:
    def send(self, message: str) -> None:
        print(message)

def notify(n: Notifier):
    n.send("Hello")

notify(EmailNotifier())
```

#### Better Understanding

Python interfaces are commonly expressed with ABCs, `Protocol`, or duck typing. `Protocol` is especially useful for structural typing with static type checkers.

---


## 4. Web Frameworks — Django / Flask / FastAPI (81–110)

### 81. Django vs Flask vs FastAPI — when to use each?

**Answer:** Django: batteries-included monoliths (ORM, admin, auth). Flask: minimal, flexible microservices/APIs. FastAPI: modern async APIs with automatic OpenAPI and type-hint validation; great for high-concurrency I/O services.

#### Example

```python
# Django: full-stack application
# Flask: minimal and flexible
# FastAPI: typed API framework with strong async support

# Example decision:
# Admin/auth/ORM-heavy app -> Django
# Small custom service      -> Flask
# Typed high-concurrency API -> FastAPI
```

#### Better Understanding

Choose based on team needs and architecture, not benchmark claims alone. All three can build production APIs.

### 82. What is WSGI vs ASGI?

**Answer:** WSGI is the sync Python web standard (Django classic, Flask). ASGI supports async and WebSockets (FastAPI, Django ASGI, Starlette). Uvicorn/Hypercorn are ASGI servers; Gunicorn often WSGI (or with Uvicorn workers).

#### Example

```python
# WSGI: synchronous application interface
# ASGI: supports async applications and protocols such as WebSockets

# FastAPI example deployment:
# uvicorn app:app

# Traditional Flask deployment:
# gunicorn app:app
```

#### Better Understanding

WSGI is mainly synchronous; ASGI supports asynchronous applications and long-lived connections. The server and framework must use compatible interfaces.

### 83. Explain Django MVT.

**Answer:** Model (data), View (request logic), Template (presentation). Similar to MVC; Django’s “view” is closer to a controller.

#### Example

```python
# models.py
class Product:
    ...

# views.py
def product_detail(request, product_id):
    ...

# template:
# <h1>{{ product.name }}</h1>
```

#### Better Understanding

Django's MVT is similar to MVC, but Django calls the request-handling/controller-like layer a **view**.

### 84. What are Django migrations?

**Answer:** Versioned schema changes generated from model changes (`makemigrations` / `migrate`). Applied in order; keep them in VCS. Avoid editing applied migrations casually.

#### Example

```python
# After changing a Django model:
python manage.py makemigrations
python manage.py migrate

# Migration files are committed to version control.
```

#### Better Understanding

Migrations are version-controlled database schema changes. Treat them like code and test them before production deployment.

### 85. Difference between Django `ForeignKey`, `OneToOne`, `ManyToMany`?

**Answer:** FK: many-to-one. OneToOne: unique FK both ways. M2M: through table (implicit or explicit). Choose based on cardinality.

#### Example

```python
class Profile(models.Model):
    user = models.OneToOneField(User, on_delete=models.CASCADE)

class Order(models.Model):
    user = models.ForeignKey(User, on_delete=models.CASCADE)

class User(models.Model):
    groups = models.ManyToManyField(Group)
```

#### Better Understanding

Choose by cardinality: many orders can belong to one user (**ForeignKey**), one profile belongs to one user (**OneToOne**), and users/groups can have many-to-many relationships.

### 86. What is `select_related` vs `prefetch_related`?

**Answer:** `select_related`: SQL JOINs for FK/OneToOne (single query). `prefetch_related`: separate query + Python join for M2M/reverse FK. Prevents N+1 queries.

#### Example

```python
# FK / OneToOne
orders = Order.objects.select_related("user")

# M2M / reverse FK
users = User.objects.prefetch_related("groups")
```

#### Better Understanding

Use `select_related` for single-valued relationships that can be joined in SQL; use `prefetch_related` for collections and many-to-many relationships.

### 87. What causes the N+1 query problem?

**Answer:** Looping over objects and hitting related fields lazily, one query per row. Fix with `select_related`/`prefetch_related`, eager loading, or batch queries.

#### Example

```python
# Bad pattern
users = User.objects.all()
for user in users:
    print(user.profile.name)  # may issue another query per user

# Better
users = User.objects.select_related("profile")
```

#### Better Understanding

N+1 means one query loads the parent collection and then additional queries are executed repeatedly for related objects. Detect it with query logging/profilers.

### 88. Flask: application factory pattern — why?

**Answer:** `create_app()` builds the app with config/extensions. Enables multiple configs, testing, and avoids circular imports from global app objects.

#### Example

```python
def create_app(config=None):
    app = Flask(__name__)
    app.config.from_mapping(config or {})
    # register extensions/routes
    return app

app = create_app({"TESTING": True})
```

#### Better Understanding

The factory pattern supports different configurations for testing, development, and production and reduces global initialization problems.

### 89. What are Flask blueprints?

**Answer:** Modular route groups with their own templates/static. Register on the app — scales larger Flask projects.

#### Example

```python
from flask import Blueprint

users = Blueprint("users", __name__, url_prefix="/users")

@users.get("/<int:user_id>")
def detail(user_id):
    return {"id": user_id}

# app.register_blueprint(users)
```

#### Better Understanding

Blueprints split a large Flask application into reusable route modules with clearer ownership.

### 90. FastAPI: what does Pydantic do?

**Answer:** Validates and serializes request/response data from type hints. Gives clear 422 errors and OpenAPI schemas automatically.

#### Example

```python
from pydantic import BaseModel

class User(BaseModel):
    name: str
    age: int

user = User(name="Ana", age="25")
print(user.age)  # parsed/validated according to Pydantic rules
```

#### Better Understanding

Pydantic turns type annotations into runtime validation/serialization rules and contributes schemas to FastAPI's OpenAPI documentation.

### 91. FastAPI dependency injection — purpose?

**Answer:** `Depends()` injects shared logic (DB sessions, auth, pagination). Reusable, testable, composable request plumbing.

#### Example

```python
from fastapi import Depends, FastAPI

app = FastAPI()

def get_db():
    db = make_db()
    try:
        yield db
    finally:
        db.close()

@app.get("/users")
def users(db=Depends(get_db)):
    return db.list_users()
```

#### Better Understanding

`Depends()` keeps shared concerns such as authentication, database sessions, and common parameters reusable and testable.

### 92. How do you handle CORS?

**Answer:** Configure allowed origins/methods/headers via middleware (`CORSMiddleware` in FastAPI/Starlette, `django-cors-headers`, Flask-CORS). Never use `*` with credentials in production.

#### Example

```python
from fastapi.middleware.cors import CORSMiddleware

app.add_middleware(
    CORSMiddleware,
    allow_origins=["https://example.com"],
    allow_methods=["GET", "POST"],
    allow_headers=["Authorization", "Content-Type"],
)
```

#### Better Understanding

Allow only the origins, methods, and headers your frontend actually needs. Be especially careful when credentials/cookies are enabled.

### 93. What is middleware?

**Answer:** Components that process requests/responses globally (auth, logging, CORS, GZip). In Django: middleware stack; in FastAPI/Starlette: ASGI middleware.

#### Example

```python
# Conceptually:
request
  -> middleware
  -> route/view
  -> response
  -> middleware
  -> client

# Logging, authentication, CORS and compression are common middleware concerns.
```

#### Better Understanding

Middleware is best for cross-cutting behavior that should apply broadly, rather than business logic specific to one endpoint.

### 94. Explain Django signals briefly.

**Answer:** Decoupled notifications (`pre_save`, `post_save`, etc.). Useful for side effects; overuse hides control flow — prefer explicit service calls when clarity matters.

#### Example

```python
from django.db.models.signals import post_save
from django.dispatch import receiver

@receiver(post_save, sender=User)
def user_saved(sender, instance, created, **kwargs):
    if created:
        print("New user:", instance.id)
```

#### Better Understanding

Signals are useful for decoupled side effects, but explicit service calls are often easier to follow when the business operation is important.

### 95. What is Django REST Framework (DRF)?

**Answer:** Toolkit for building REST APIs on Django: serializers, viewsets, routers, permissions, authentication, browsable API.

#### Example

```python
from rest_framework import serializers, viewsets

class UserSerializer(serializers.ModelSerializer):
    class Meta:
        model = User
        fields = ["id", "name"]

class UserViewSet(viewsets.ModelViewSet):
    queryset = User.objects.all()
    serializer_class = UserSerializer
```

#### Better Understanding

DRF provides the pieces commonly needed for REST APIs: serialization, authentication, permissions, routing, pagination, and API views/viewsets.

### 96. Serializer vs ModelSerializer in DRF?

**Answer:** Serializer: manual field definitions. ModelSerializer: auto fields from a model + create/update helpers. Customize validation as needed.

#### Example

```python
class UserSerializer(serializers.Serializer):
    name = serializers.CharField()
    age = serializers.IntegerField()

class UserModelSerializer(serializers.ModelSerializer):
    class Meta:
        model = User
        fields = ["id", "name", "age"]
```

#### Better Understanding

Use `Serializer` for full manual control; use `ModelSerializer` when the API closely maps to a Django model.

### 97. What are Django class-based views vs function-based?

**Answer:** FBVs: simple and explicit. CBVs: reuse via inheritance/mixins (ListView, APIView). Prefer clarity; CBVs help for standard CRUD patterns.

#### Example

```python
# Function-based view
def hello(request):
    return JsonResponse({"message": "hi"})

# Class-based view
class UserListView(ListView):
    model = User
```

#### Better Understanding

FBVs are often easiest for small/custom behavior. CBVs become useful when you can reuse generic behavior or mixins without making the code harder to follow.

### 98. How does FastAPI background tasks work?

**Answer:** `BackgroundTasks` runs functions after the response is sent — fine for light work (email send). For heavy/reliable jobs use Celery/RQ/arq.

#### Example

```python
from fastapi import BackgroundTasks

@app.post("/signup")
def signup(email: str, background_tasks: BackgroundTasks):
    background_tasks.add_task(send_welcome_email, email)
    return {"status": "created"}
```

#### Better Understanding

FastAPI background tasks are convenient for lightweight work after the response. Use a durable queue such as Celery/RQ for heavy, retryable, or long-running jobs.

### 99. What is Uvicorn?

**Answer:** Lightning-fast ASGI server built on uvloop/httptools. Common production choice behind nginx for FastAPI/Starlette apps.

#### Example

```python
# Run a FastAPI application:
# uvicorn main:app --host 0.0.0.0 --port 8000

# Uvicorn is an ASGI server; FastAPI is the framework.
```

#### Better Understanding

Do not confuse the framework with the server: FastAPI defines the application, while Uvicorn runs it using ASGI.

### 100. How do you structure a mid-size FastAPI project?

**Answer:** Separate routers, schemas (Pydantic), models, services/use-cases, repositories, dependencies, and config. Keep routers thin; business logic in services.

#### Example

```python
app/
  main.py
  routers/
  schemas/
  models/
  services/
  repositories/
  dependencies/
  config.py
```

#### Better Understanding

Keep route handlers thin. Put business rules in services/use-cases and data access behind repositories when that abstraction actually helps the project.

### 101. Django `settings.py` — environment-specific config?

**Answer:** Use env vars (`django-environ`, `pydantic-settings`), split settings modules, or 12-factor config. Never commit secrets.

#### Example

```python
# settings.py
import os

DEBUG = os.getenv("DEBUG", "false").lower() == "true"
SECRET_KEY = os.environ["SECRET_KEY"]
```

#### Better Understanding

Environment-specific settings should come from configuration/environment rather than hard-coded secrets. Split settings modules when the project benefits from it.

### 102. What is Flask’s `g` object?

**Answer:** Request-scoped temporary storage for data during a request (e.g., current user, DB connection). Cleared after the request.

#### Example

```python
from flask import g

@app.before_request
def load_user():
    g.user = get_current_user()

@app.get("/me")
def me():
    return {"id": g.user.id}
```

#### Better Understanding

`g` is request-scoped. It is not a global cache and its values should not be expected to survive across requests.

### 103. Explain CSRF protection.

**Answer:** Cross-Site Request Forgery: browser sends cookies on malicious sites’ requests. Django forms/middleware use CSRF tokens. APIs often use tokens/headers instead of cookie sessions alone.

#### Example

```python
# A cookie-authenticated form includes a CSRF token:
<form method="post">
    {% csrf_token %}
    ...
</form>
```

#### Better Understanding

CSRF matters when browsers automatically attach credentials such as cookies. The defense is to require an unpredictable token tied to the user's session/context.

### 104. How do sessions work in Django?

**Answer:** Server stores session data (DB/cache/file); client gets a session cookie id. Configurable backends. Prefer cache/DB for multi-instance deploys.

#### Example

```python
# Django can store sessions in the database, cache, files, or signed cookies
# Typical request flow:
# browser -> session cookie -> Django -> session backend
```

#### Better Understanding

A session cookie usually identifies the session; the server-side session backend can then hold the associated state. Configure a shared backend for multi-instance deployments.

### 105. What is Jinja2?

**Answer:** Popular templating engine (Flask default, Django-inspired syntax). Used for HTML/email templates with inheritance and filters.

#### Example

```python
from flask import render_template

@app.get("/hello/<name>")
def hello(name):
    return render_template("hello.html", name=name)

# hello.html:
# <h1>Hello {{ name }}</h1>
```

#### Better Understanding

Jinja templates support variables, filters, conditionals, loops, and template inheritance while keeping presentation separate from Python code.

### 106. FastAPI `response_model` — why use it?

**Answer:** Filters/validates outgoing data, documents schema, and prevents leaking sensitive fields accidentally.

#### Example

```python
from pydantic import BaseModel

class UserOut(BaseModel):
    id: int
    name: str

@app.get("/user", response_model=UserOut)
def user():
    return {"id": 1, "name": "Ana", "password_hash": "secret"}
```

#### Better Understanding

`response_model` validates and shapes the response, helping prevent accidental exposure of fields that are not part of the public API.

### 107. How do you version APIs in these frameworks?

**Answer:** URL prefix (`/api/v1`), headers, or Accept versioning. Mount versioned routers. Keep backward compatibility until clients migrate.

#### Example

```python
# Common approach:
GET /api/v1/users
GET /api/v2/users

# Keep v1 available during a documented migration period.
```

#### Better Understanding

Versioning is a compatibility strategy. Define what changes require a new version and communicate deprecation timelines to consumers.

### 108. What is Django Admin good for?

**Answer:** Rapid internal CRUD UI for models. Customize list displays, filters, actions. Not a public-facing product UI.

#### Example

```python
# admin.py
@admin.register(Product)
class ProductAdmin(admin.ModelAdmin):
    list_display = ["id", "name", "price"]
    search_fields = ["name"]
```

#### Better Understanding

Django Admin is excellent for internal operational CRUD and staff workflows. It is not automatically a replacement for a polished customer-facing UI.

### 109. Explain request lifecycle briefly (Django).

**Answer:** Request → middleware → URL resolve → view → (ORM/service) → response → middleware → client. Exceptions handled by handlers/middleware.

#### Example

```python
request
  -> middleware
  -> URL resolver
  -> view
  -> ORM/service
  -> response
  -> middleware
  -> client
```

#### Better Understanding

When debugging a Django request, knowing this lifecycle helps identify whether the problem is routing, middleware, business logic, database access, or response processing.

### 110. How do you serve static files in production?

**Answer:** Collect static (`collectstatic`), serve via CDN/nginx/S3 — not the app server. Whitenoise can serve from the app for simpler setups.

---

## 5. REST APIs & HTTP (111–130)

#### Example

```python
python manage.py collectstatic

# Production options:
# CDN + object storage
# nginx
# WhiteNoise for simpler deployments
```

#### Better Understanding

Do not rely on Django's development static-file server in production. Collect and serve assets through infrastructure designed for static content.

---


## 5. REST APIs & HTTP (111–130)

### 111. What is REST?

**Answer:** Architectural style: resources identified by URIs, manipulated via HTTP methods, stateless requests, representations (JSON/XML). Not a strict protocol — conventions vary.

#### Example

```python
GET /users/42
POST /users
PATCH /users/42
DELETE /users/42
```

#### Better Understanding

REST is an architectural style rather than a strict wire protocol. Good REST APIs use meaningful resources, standard HTTP semantics, and stateless requests.

### 112. Common HTTP methods and idempotency?

**Answer:** GET (read, idempotent, safe), POST (create/action, not idempotent), PUT (replace, idempotent), PATCH (partial update), DELETE (idempotent ideally). Idempotent: same effect if repeated.

#### Example

```python
# GET /users/42       -> read
# POST /orders         -> create
# PUT /users/42        -> replace
# PATCH /users/42      -> partial update
# DELETE /users/42     -> remove
```

#### Better Understanding

Idempotent means repeating the same request has the same intended effect as making it once. PUT and DELETE are defined as idempotent; POST generally is not.

### 113. What are common HTTP status codes you use?

**Answer:** 200 OK, 201 Created, 204 No Content, 400 Bad Request, 401 Unauthorized, 403 Forbidden, 404 Not Found, 409 Conflict, 422 Unprocessable, 429 Too Many Requests, 500 Internal Server Error.

#### Example

```python
# 200 OK
# 201 Created
# 204 No Content
# 400 Bad Request
# 401 Unauthorized
# 403 Forbidden
# 404 Not Found
# 409 Conflict
# 422 Unprocessable Content
# 429 Too Many Requests
# 500 Internal Server Error
```

#### Better Understanding

Choose status codes based on the meaning of the response, and keep the API consistent. Do not use 200 for every error.

### 114. 401 vs 403?

**Answer:** 401: not authenticated (missing/invalid credentials). 403: authenticated but not allowed. Some APIs blur them; be consistent.

#### Example

```python
# 401
GET /profile
Authorization: missing/invalid

# 403
Authorization: valid
# but user lacks permission
```

#### Better Understanding

A useful mental model is: **401 = who are you?** and **403 = you are known, but not allowed.**

### 115. What is idempotency key used for?

**Answer:** Client sends a unique key with POST so retries don’t create duplicates (payments, orders). Server stores key → result mapping.

#### Example

```python
POST /payments
Idempotency-Key: 8f2c...

# Server:
# first request -> create payment and store result for key
# retry -> return the stored result instead of charging again
```

#### Better Understanding

Idempotency keys are especially important for retryable operations such as payments and order creation.

### 116. REST vs GraphQL vs gRPC?

**Answer:** REST: resource URLs, simple caching/HTTP. GraphQL: client-shaped queries, one endpoint, over/under-fetching control. gRPC: binary Protobuf, strong contracts, great for service-to-service; less browser-native.

#### Example

```python
# REST
GET /users/1

# GraphQL
query { user(id: 1) { name orders { id } } }

# gRPC
rpc GetUser(GetUserRequest) returns (User);
```

#### Better Understanding

REST is broadly interoperable, GraphQL gives clients flexible query shapes, and gRPC is strong for internal service-to-service communication with typed contracts.

### 117. What is HATEOAS?

**Answer:** Hypermedia as the Engine of Application State — responses include links to related actions. Rarely fully adopted; “REST maturity” concept.

#### Example

```python
{
  "id": 42,
  "name": "Ana",
  "_links": {
    "self": "/users/42",
    "orders": "/users/42/orders"
  }
}
```

#### Better Understanding

HATEOAS lets clients discover related actions through links in representations. It is conceptually important but not required by every practical REST API.

### 118. How do you design pagination?

**Answer:** Offset/limit (simple, can skip inconsistently) or cursor-based (stable for infinite scroll). Return `next`/`prev` links and totals when useful.

#### Example

```python
# Offset pagination
GET /products?limit=20&offset=40

# Cursor pagination
GET /products?limit=20&cursor=eyJpZCI6MTAwfQ==
```

#### Better Understanding

Offset is simple and works well for many admin screens. Cursor pagination is usually more stable and efficient for large, changing datasets and infinite scrolling.

### 119. What is content negotiation?

**Answer:** Client and server agree on representation via `Accept` / `Content-Type` headers (JSON vs XML, etc.).

#### Example

```python
GET /report
Accept: application/json

# Server responds with a representation matching what it supports.
```

#### Better Understanding

`Accept` describes what the client wants back; `Content-Type` describes the representation being sent in a request or response body.

### 120. Explain JWT structure and risks.

**Answer:** Header.Payload.Signature (Base64URL). Stateless auth claims. Risks: long-lived tokens, secret leak, no easy revoke — use short TTL + refresh tokens + denylist if needed. Don’t put secrets in payload (it’s readable).

#### Example

```python
# JWT shape:
# header.payload.signature

# Example conceptual payload:
{
    "sub": "user-123",
    "exp": 1780000000
}
```

#### Better Understanding

JWT payloads are encoded, not secret. Never put passwords or sensitive secrets in them. Use short-lived access tokens and an appropriate refresh/revocation strategy.

### 121. Cookie-based vs token-based auth?

**Answer:** Cookies: browser auto-sends; CSRF concerns; good for first-party web. Bearer tokens: explicit Authorization header; common for SPAs/mobile/APIs; store carefully (prefer httpOnly cookies for web XSS mitigation).

#### Example

```python
# Cookie session
Cookie: session_id=...

# Bearer token
Authorization: Bearer eyJ...
```

#### Better Understanding

Cookies are convenient for browser sessions but require CSRF defenses. Bearer tokens are explicitly attached by the client and are common for APIs/mobile clients.

### 122. What is OAuth2 vs OpenID Connect?

**Answer:** OAuth2: authorization (delegated access). OIDC: identity layer on OAuth2 (who the user is — ID token). “Login with Google” is typically OIDC.

#### Example

```python
# OAuth2: allow an application to access a resource
# OIDC: adds user identity/authentication information

# Typical login:
# Browser -> Identity Provider -> authorization code
# App -> token exchange -> ID/access tokens
```

#### Better Understanding

OAuth2 answers **what can this client access?** OIDC adds **who is the user?**

### 123. How do you version and deprecate APIs?

**Answer:** Version in path/header; announce deprecation; monitor usage; keep overlap period; document migration; eventually remove with notice.

#### Example

```python
# Example:
# /api/v1/orders -> deprecated
# /api/v2/orders -> current

# Publish a migration guide and monitor v1 usage before removal.
```

#### Better Understanding

Good deprecation is a process: announce, document, measure usage, give consumers time to migrate, then remove the old contract.

### 124. What makes a good error response body?

**Answer:** Consistent shape: `code`, `message`, optional `details`/`fields`. Don’t leak stack traces in production. Map domain errors to HTTP statuses.

#### Example

```python
{
  "code": "VALIDATION_ERROR",
  "message": "Invalid request",
  "details": {
    "email": "Invalid email address"
  }
}
```

#### Better Understanding

Keep error formats stable and machine-readable. Avoid returning internal stack traces, SQL errors, or secrets to clients.

### 125. What is rate limiting? Where enforce it?

**Answer:** Cap requests per client/IP/API key. Enforce at gateway/nginx/API middleware/Redis counters. Return 429 + `Retry-After`.

#### Example

```python
# Example policy:
# 100 requests/minute per API key

# Response when exceeded:
# HTTP 429
# Retry-After: 30
```

#### Better Understanding

Rate limiting protects availability and fairness. Enforce it as close to the edge as practical and use shared state such as Redis when multiple instances are involved.

### 126. PUT vs PATCH?

**Answer:** PUT replaces the whole resource (client sends complete state). PATCH applies partial updates. Prefer PATCH for sparse updates.

#### Example

```python
# PUT: send the desired complete representation
PUT /users/42
{"name": "Ana", "email": "ana@example.com"}

# PATCH: send only fields to change
PATCH /users/42
{"email": "new@example.com"}
```

#### Better Understanding

Use PUT when the request represents replacement semantics; use PATCH when the client is making a partial change.

### 127. What is CORS and when do you need it?

**Answer:** Browser security: cross-origin XHR/fetch restricted unless server allows via CORS headers. Needed for SPAs on different origins calling your API.

#### Example

```python
# Frontend:
https://app.example.com

# API:
https://api.example.com

# Browser requires the API to explicitly allow the frontend origin.
```

#### Better Understanding

CORS is enforced by browsers. It is not a replacement for authentication or authorization and does not prevent non-browser clients from calling an API.

### 128. Safe vs unsafe HTTP methods?

**Answer:** Safe methods (GET, HEAD, OPTIONS) shouldn’t change server state. Unsafe (POST, PUT, PATCH, DELETE) may. Caching proxies rely on this.

#### Example

```python
# Safe:
GET /products/42

# Unsafe:
POST /orders
DELETE /users/42
```

#### Better Understanding

Safe methods are intended not to change server state. This distinction affects browser behavior, caching, and automated tooling.

### 129. How do you secure an API? Checklist.

**Answer:** HTTPS, authn/authz, input validation, rate limits, least privilege DB users, secrets in vault/env, logging without PII, dependency updates, CORS lockdown, security headers.

#### Example

```python
# API security checklist
# HTTPS
# Authentication + authorization
# Input validation
# Rate limiting
# Least-privilege DB account
# Secret management
# Secure CORS
# Dependency patching
# Safe logging
```

#### Better Understanding

Security is layered. No single mechanism replaces proper authentication, authorization, validation, secure transport, monitoring, and dependency management.

### 130. What is OpenAPI/Swagger?

**Answer:** Spec for describing HTTP APIs. FastAPI generates it from code. Used for docs, client generation, contract testing.

---

## 6. Databases & ORM (131–155)

#### Example

```python
# OpenAPI describes endpoints, schemas, parameters, responses and auth.

# FastAPI:
# http://localhost:8000/docs
# automatically exposes interactive Swagger UI.
```

#### Better Understanding

OpenAPI can drive documentation, client generation, contract testing, and collaboration between frontend/backend teams.

---


## 6. Databases & ORM (131–155)

### 131. SQL vs NoSQL — when each?

**Answer:** SQL: structured data, strong consistency, complex joins, transactions. NoSQL (document/key-value): flexible schemas, horizontal scale, simple access patterns. Choose by query patterns and consistency needs.

#### Example

```python
# SQL: orders(user_id, total, created_at)
# Query:
SELECT user_id, SUM(total)
FROM orders
GROUP BY user_id;

# NoSQL document example:
{"user_id": 1, "orders": [{"total": 20}]}
```

#### Better Understanding

Choose the database based on access patterns, relationships, consistency requirements, and operational constraints—not simply because one technology is fashionable.

### 132. What is ACID?

**Answer:** Atomicity, Consistency, Isolation, Durability — properties of reliable transactions in relational DBs.

#### Example

```python
BEGIN;

UPDATE accounts
SET balance = balance - 100
WHERE id = 1;

UPDATE accounts
SET balance = balance + 100
WHERE id = 2;

COMMIT;
```

#### Better Understanding

ACID means **Atomicity, Consistency, Isolation, Durability**. Transactions use these properties to make state changes reliable under failures and concurrency.

### 133. Explain database indexes. Tradeoffs?

**Answer:** Structures (usually B-trees) that speed lookups/filters/sorts. Tradeoffs: slower writes, extra storage. Index columns used in WHERE/JOIN/ORDER BY carefully; avoid over-indexing.

#### Example

```python
CREATE INDEX idx_orders_user_id
ON orders(user_id);

SELECT *
FROM orders
WHERE user_id = 42;
```

#### Better Understanding

Indexes speed reads by providing a structure for locating rows, but they consume storage and make inserts/updates/deletes more expensive.

### 134. What is a primary key vs unique vs foreign key?

**Answer:** PK uniquely identifies a row (often surrogate id). UNIQUE constrains uniqueness. FK enforces referential integrity to another table’s key.

#### Example

```python
CREATE TABLE orders (
    id BIGINT PRIMARY KEY,
    order_number TEXT UNIQUE,
    user_id BIGINT REFERENCES users(id)
);
```

#### Better Understanding

PK identifies a row, UNIQUE enforces uniqueness for a column/set of columns, and FK links rows while enforcing referential integrity.

### 135. INNER JOIN vs LEFT JOIN?

**Answer:** INNER: only matching rows both sides. LEFT: all left rows + matches from right (NULLs if none). RIGHT/FULL less common in app SQL.

#### Example

```python
-- Only users with orders
SELECT users.id, orders.id
FROM users
INNER JOIN orders ON orders.user_id = users.id;

-- All users, even those without orders
SELECT users.id, orders.id
FROM users
LEFT JOIN orders ON orders.user_id = users.id;
```

#### Better Understanding

Ask: **Do I want unmatched rows?** If no, INNER JOIN. If all rows from the left side must remain, LEFT JOIN.

### 136. What is normalization? Denormalization?

**Answer:** Normalization reduces redundancy (1NF–3NF typical). Denormalization adds redundancy for read performance. Balance consistency vs speed.

#### Example

```python
-- Normalized:
users(id, name)
orders(id, user_id, total)

-- Denormalized:
orders(id, user_id, user_name, total)
```

#### Better Understanding

Normalization improves consistency and reduces duplication. Denormalization can improve read performance when the extra redundancy is intentional and maintained correctly.

### 137. What is a transaction isolation level?

**Answer:** Controls visibility of concurrent transactions: Read Uncommitted, Read Committed, Repeatable Read, Serializable. Higher = fewer anomalies, more locking/contention.

#### Example

```python
# Conceptual:
# Read Committed:
# a query sees committed data at its isolation boundary
#
# Serializable:
# strongest isolation; concurrent transactions behave as if serialized
```

#### Better Understanding

Higher isolation reduces anomalies but can increase contention and reduce concurrency. Pick the weakest level that safely satisfies the business requirement.

### 138. Explain optimistic vs pessimistic locking.

**Answer:** Optimistic: assume rare conflicts; version column; fail on stale update. Pessimistic: lock rows (`SELECT FOR UPDATE`) during transaction. Choose based on contention.

#### Example

```python
# Optimistic:
UPDATE products
SET stock = 9, version = version + 1
WHERE id = 1 AND version = 3;

# Pessimistic:
SELECT *
FROM products
WHERE id = 1
FOR UPDATE;
```

#### Better Understanding

Use optimistic locking when conflicts are relatively rare; use pessimistic locking when conflicting updates are common and correctness requires holding a lock.

### 139. What is connection pooling? Why needed?

**Answer:** Reuse DB connections instead of opening per request. Creating connections is expensive. Tools: SQLAlchemy pool, PgBouncer, Django CONN_MAX_AGE.

#### Example

```python
# Pool:
# request 1 -> reuse connection A
# request 2 -> reuse connection B
# request 3 -> reuse connection A
```

#### Better Understanding

Connection pooling avoids repeatedly paying the cost of creating database connections and protects the database from excessive connection churn.

### 140. How do you prevent SQL injection?

**Answer:** Always parameterized queries / ORM bindings. Never concatenate user input into SQL. Validate/sanitize inputs as defense in depth.

#### Example

```python
# Safe
cursor.execute(
    "SELECT * FROM users WHERE id = %s",
    [user_id]
)

# Unsafe
# query = f"SELECT * FROM users WHERE id = {user_id}"
```

#### Better Understanding

Never build SQL by concatenating untrusted input. Use parameter binding or a properly configured ORM/query builder.

### 141. ORM vs raw SQL — when raw?

**Answer:** ORM for CRUD and maintainability. Raw/SQLAlchemy Core for complex reports, window functions, performance-critical queries, DB-specific features. Measure with EXPLAIN.

#### Example

```python
# ORM for common CRUD
users = User.objects.filter(active=True)

# Raw SQL for a specialized report:
cursor.execute("SELECT ... complex window function ...")
```

#### Better Understanding

Start with the ORM for maintainability, then use SQL when the query is genuinely complex, database-specific, or proven to be a performance bottleneck.

### 142. What is Alembic / Django migrations role?

**Answer:** Schema migration tools that version DB changes with application code. Essential for team deploys and rollbacks strategy.

#### Example

```python
# Django
python manage.py makemigrations
python manage.py migrate

# Alembic
alembic revision --autogenerate -m "add status"
alembic upgrade head
```

#### Better Understanding

Migration tools keep application schema changes reproducible across developers, CI, staging, and production.

### 143. Explain eventual consistency.

**Answer:** System may temporarily show stale data but converges. Common in distributed/NoSQL/replicas. OK for feeds/caches; careful for balances/inventory.

#### Example

```python
# Service A writes a profile.
# Service B/replica may temporarily return the old profile.
# Later replication completes and both show the new value.
```

#### Better Understanding

Eventual consistency is acceptable when temporary stale reads are safe. It is dangerous when a stale value could cause financial, inventory, or authorization errors.

### 144. What is Redis used for in backends?

**Answer:** Cache, session store, rate limiting, pub/sub, leaderboards, job queues (with RQ/Celery broker). In-memory, very fast; persistence optional.

#### Example

```python
import redis

r = redis.Redis()

r.setex("user:42", 60, '{"name":"Ana"}')
print(r.get("user:42"))
```

#### Better Understanding

Redis is commonly used for low-latency cache/session data, rate limiting, counters, queues, and pub/sub. Design carefully around eviction and persistence guarantees.

### 145. Cache strategies: cache-aside vs write-through?

**Answer:** Cache-aside: app reads cache → miss → DB → populate cache. Write-through: write DB and cache together. Also write-behind, TTL eviction, stampede protection.

#### Example

```python
# Cache-aside
value = cache.get(key)
if value is None:
    value = db.load(key)
    cache.set(key, value, ttl=60)

# Write-through concept:
# write DB + cache as part of the write path.
```

#### Better Understanding

Cache-aside is simple and common. Write-through can keep cache contents fresher but couples writes to cache behavior.

### 146. What is the thundering herd / cache stampede?

**Answer:** Many requests miss same hot key simultaneously and slam the DB. Mitigate with locking, soft TTL, probabilistic early refresh, or singleflight.

#### Example

```python
# Many requests:
# cache.get("popular-product") -> miss
# all requests query the DB at once
#
# Mitigations:
# lock one refresh
# use soft TTL
# pre-warm hot keys
```

#### Better Understanding

A cache stampede is a concurrency problem around an expired/missing hot key. Protect the origin database rather than simply increasing its capacity.

### 147. Explain database migrations zero-downtime tips.

**Answer:** Expand-contract: add columns nullable → deploy code → backfill → enforce constraints → remove old. Avoid destructive renames in one step. Feature flags help.

#### Example

```python
# Expand:
ALTER TABLE users ADD COLUMN new_name TEXT;

# Deploy code that can read/write both old and new fields.
# Backfill.
# Switch reads.
# Later remove old field.
```

#### Better Understanding

Expand-contract keeps old and new application versions compatible during rolling deployments, reducing downtime and rollback risk.

### 148. What is EXPLAIN / EXPLAIN ANALYZE?

**Answer:** Shows query plan (and actual timings with ANALYZE). Use to find sequential scans, bad joins, missing indexes.

#### Example

```python
EXPLAIN ANALYZE
SELECT *
FROM orders
WHERE user_id = 42;
```

#### Better Understanding

Look at actual execution time, row estimates, scans, joins, and index usage. Optimize based on evidence rather than guessing.

### 149. Difference between MongoDB and PostgreSQL?

**Answer:** Postgres: relational, SQL, strong transactions, rich types/JSON too. Mongo: document store, flexible schema, horizontal sharding focus. Postgres often enough with JSONB.

#### Example

```python
# PostgreSQL
CREATE TABLE users (
    id BIGSERIAL PRIMARY KEY,
    profile JSONB
);

# MongoDB
# {
#   "_id": "...",
#   "profile": {"name": "Ana"}
# }
```

#### Better Understanding

PostgreSQL is relational and supports powerful SQL, transactions, and JSONB. MongoDB is document-oriented. Either can be appropriate depending on access patterns.

### 150. What is JSONB in PostgreSQL?

**Answer:** Binary JSON storage with indexing (GIN) and querying. Good for semi-structured attributes without a separate document DB.

#### Example

```python
CREATE TABLE products (
    id BIGSERIAL PRIMARY KEY,
    attributes JSONB
);

CREATE INDEX idx_products_attributes
ON products USING GIN (attributes);
```

#### Better Understanding

JSONB is useful for semi-structured data while keeping it inside PostgreSQL. Don't use it as an excuse to abandon relational modeling when relationships and constraints matter.

### 151. How do you handle soft deletes?

**Answer:** `deleted_at` timestamp instead of DELETE. Filter in queries/default managers. Tradeoffs: unique constraints, storage, accidental inclusion — document carefully.

#### Example

```python
class User(models.Model):
    deleted_at = models.DateTimeField(null=True, blank=True)

# Instead of DELETE:
user.deleted_at = timezone.now()
user.save(update_fields=["deleted_at"])
```

#### Better Understanding

Soft deletion preserves historical data, but every relevant query must consistently exclude deleted rows and uniqueness rules need careful design.

### 152. What is a database migration rollback strategy?

**Answer:** Prefer forward-fix migrations. Keep backups. Test down migrations in staging. For production, restore from backup or reverse expand-contract if needed.

#### Example

```python
# Safer production strategy:
# 1. Take/verify backups
# 2. Prefer forward-compatible migration
# 3. Test rollback/recovery
# 4. Use expand-contract for risky changes
# 5. Restore or forward-fix if a deployment fails
```

#### Better Understanding

Production rollback is not always the same as reversing a schema migration. For destructive changes, backups and forward-fix plans are critical.

### 153. SQLAlchemy Session vs Engine?

**Answer:** Engine: connection pool + dialect. Session: unit of work / identity map for ORM objects. Commit/rollback at session boundaries.

#### Example

```python
engine = create_engine(DB_URL)

with Session(engine) as session:
    user = session.get(User, 1)
    user.name = "Ana"
    session.commit()
```

#### Better Understanding

The Engine manages database connectivity/pooling. A SQLAlchemy ORM Session manages a unit of work and tracks ORM objects.

### 154. What is `CASCADE` on foreign keys?

**Answer:** Deleting/updating parent auto-deletes/updates children. Convenient but dangerous — accidental mass deletes. Prefer explicit application deletes when unsure.

#### Example

```python
CREATE TABLE orders (
    id BIGINT PRIMARY KEY,
    user_id BIGINT REFERENCES users(id)
        ON DELETE CASCADE
);
```

#### Better Understanding

CASCADE can be convenient for dependent records, but it can also delete many rows unexpectedly. Use it only when the lifecycle relationship is truly intended.

### 155. How do you choose between UUID and auto-increment IDs?

**Answer:** Auto-increment: simple, compact, sequential. UUID: safer for distributed generation, harder to guess, larger indexes. UUIDv7 improves sortability.

---

## 7. Async, Concurrency & Performance (156–170)

#### Example

```python
# Auto-increment:
1, 2, 3, 4

# UUID:
550e8400-e29b-41d4-a716-446655440000
```

#### Better Understanding

Auto-increment IDs are compact and index-friendly. UUIDs can be generated independently across services and are harder to guess. UUIDv7 is useful when ordered IDs are desirable.

---


## 7. Async, Concurrency & Performance (156–170)

### 156. Threading vs multiprocessing vs asyncio?

**Answer:** Threading: good for I/O; limited by GIL for CPU. Multiprocessing: true parallelism for CPU-bound. Asyncio: single-thread cooperative concurrency for many I/O connections with less overhead.

#### Example

```python
# Threading -> many waiting I/O operations
# multiprocessing -> CPU work on multiple processes
# asyncio -> many cooperative I/O tasks

# Example:
# asyncio.gather(fetch_a(), fetch_b(), fetch_c())
```

#### Better Understanding

Pick the concurrency model from the workload: **CPU-bound → processes/native parallelism; I/O-bound → threads or async; many async-compatible connections → asyncio.**

### 157. What is an event loop?

**Answer:** Core of asyncio: schedules and runs coroutines, callbacks, and I/O ready events. Only one coroutine runs at a time until it awaits.

#### Example

```python
import asyncio

async def task(name):
    await asyncio.sleep(1)
    return name

async def main():
    results = await asyncio.gather(
        task("A"),
        task("B"),
    )
    print(results)

asyncio.run(main())
```

#### Better Understanding

The event loop repeatedly runs ready tasks and pauses a coroutine when it awaits an incomplete I/O operation, allowing other tasks to run.

### 158. `asyncio.gather` vs `create_task`?

**Answer:** `gather` runs awaitables concurrently and waits for all. `create_task` schedules a coroutine on the loop immediately; you can await later. Fire-and-forget tasks need careful exception handling.

#### Example

```python
async def main():
    task = asyncio.create_task(fetch_user())

    # Do other work here...
    user = await task

    # Or:
    users = await asyncio.gather(fetch_a(), fetch_b())
```

#### Better Understanding

Use `create_task()` when you want a scheduled task you can await later. Use `gather()` when you want to await several operations as a group.

### 159. When should you not use async?

**Answer:** CPU-heavy work, libraries that are blocking-only without thread offload, simple CRUD with low concurrency. Async shines with many waiting connections.

#### Example

```python
# Bad reason to use async:
# a CPU-heavy image processing loop

# Better:
# async endpoint -> queue job -> worker process

# Async shines when the endpoint spends most of its time waiting on I/O.
```

#### Better Understanding

Async is not automatically faster. It helps when concurrency is limited by waiting, not when the bottleneck is CPU computation.

### 160. How do you run blocking code in async apps?

**Answer:** `asyncio.to_thread()` or run in an executor. Don’t call blocking DB/HTTP drivers on the event loop.

#### Example

```python
import asyncio

def blocking_call():
    # slow synchronous library
    return requests.get("https://example.com").status_code

async def main():
    status = await asyncio.to_thread(blocking_call)
    print(status)
```

#### Better Understanding

Never block the event loop with long synchronous database, HTTP, file, or CPU operations. Offload compatible blocking work to a thread/executor or a worker process.

### 161. What is Celery? Typical use cases?

**Answer:** Distributed task queue: background jobs, emails, image processing, scheduled tasks. Broker (Redis/RabbitMQ) + workers + optional result backend.

#### Example

```python
# Producer:
celery_app.send_task("send_email", args=["a@example.com"])

# Worker:
@celery_app.task
def send_email(email):
    ...
```

#### Better Understanding

Celery is useful when work should happen outside the request lifecycle and needs retries, scheduling, multiple workers, or durable queueing.

### 162. At-least-once vs exactly-once delivery?

**Answer:** Most queues are at-least-once → design idempotent consumers. Exactly-once is hard; often exactly-once processing via idempotency keys + dedupe store.

#### Example

```python
# At-least-once:
# message may be delivered twice
#
# Consumer:
if already_processed(message.id):
    return

process(message)
mark_processed(message.id)
```

#### Better Understanding

Design consumers to tolerate retries. Idempotency keys, unique constraints, and deduplication records are common tools.

### 163. How do you profile a slow Python API?

**Answer:** Measure: APM (Datadog/New Relic), `cProfile`, Django Debug Toolbar, `py-spy`, slow query logs, EXPLAIN. Fix N+1, add indexes, cache, reduce payloads.

#### Example

```python
# Typical workflow:
# 1. Check APM/error rate
# 2. Inspect traces
# 3. Check DB slow-query logs
# 4. Profile Python if needed
# 5. EXPLAIN slow SQL
# 6. Fix and measure again
```

#### Better Understanding

Profile before optimizing. A slow API may be caused by Python CPU, N+1 queries, database scans, network calls, serialization, or external dependencies.

### 164. What is horizontal vs vertical scaling?

**Answer:** Vertical: bigger machine. Horizontal: more instances behind a load balancer. Horizontal needs stateless apps + shared store (DB/Redis).

#### Example

```python
# Vertical:
# 1 server -> 16 CPU / 64 GB RAM
#
# Horizontal:
# load balancer
#   -> app 1
#   -> app 2
#   -> app 3
```

#### Better Understanding

Horizontal scaling increases instance count. It usually requires stateless application processes and shared durable state such as a database/cache.

### 165. How does Gunicorn worker model work?

**Answer:** Prefork workers handle requests. Sync workers: one request per worker. Use gevent/uvicorn workers for concurrency. Tune workers ≈ 2–4 × CPU for sync CPU-light apps (rule of thumb).

#### Example

```python
# Gunicorn concept:
# master process
#   -> worker 1
#   -> worker 2
#   -> worker 3

# Workers accept requests independently.
```

#### Better Understanding

Worker count is workload- and memory-dependent. Treat formulas such as `2–4 × CPU` as starting heuristics, then benchmark and monitor.

### 166. What is backpressure?

**Answer:** Slowing producers when consumers can’t keep up (queue limits, 429s, buffering). Prevents unbounded memory growth and cascading failure.

#### Example

```python
# Producer -> bounded queue -> consumer
#
# If queue is full:
# slow/reject producers rather than allocating unlimited memory.
```

#### Better Understanding

Backpressure protects a system when downstream capacity is lower than incoming demand. Without it, queues and memory can grow until the service fails.

### 167. Explain circuit breaker pattern.

**Answer:** Stop calling a failing dependency temporarily; fail fast; retry after cooldown. Protects your service from cascading outages.

#### Example

```python
# States:
# CLOSED -> normal
# OPEN -> fail fast
# HALF_OPEN -> test recovery
#
# If the dependency repeatedly fails:
# stop sending requests temporarily.
```

#### Better Understanding

Circuit breakers prevent one failing dependency from causing request pileups and cascading failures across the rest of the system.

### 168. What is `async with` used for?

**Answer:** Asynchronous context managers (`__aenter__`/`__aexit__`) — e.g., async DB sessions, HTTP clients (`httpx.AsyncClient`).

#### Example

```python
async with httpx.AsyncClient() as client:
    response = await client.get("https://example.com")
    print(response.status_code)
```

#### Better Understanding

`async with` guarantees asynchronous setup/cleanup around resources such as HTTP clients, database sessions, locks, and streams.

### 169. Difference between CPU-bound and I/O-bound?

**Answer:** CPU-bound: computation (use multiprocessing/C extensions). I/O-bound: waiting on network/disk (threads/async help). Know which before optimizing.

#### Example

```python
# CPU-bound
result = expensive_matrix_calculation()

# I/O-bound
response = await client.get(url)

# CPU work often needs processes/native code;
# I/O work benefits from concurrency.
```

#### Better Understanding

Measure what the program is waiting on. CPU-bound and I/O-bound workloads benefit from different optimization strategies.

### 170. How do you prevent memory leaks in long-running workers?

**Answer:** Avoid global caches without bounds, close connections, watch reference cycles, recycle workers (Gunicorn `max_requests`), profile with tracemalloc/`objgraph`.

---

## 8. Testing, Debugging & Code Quality (171–180)

#### Example

```python
import tracemalloc

tracemalloc.start()

# run workload
snapshot = tracemalloc.take_snapshot()
for stat in snapshot.statistics("lineno")[:10]:
    print(stat)
```

#### Better Understanding

Long-running workers should bound caches, close resources, avoid accumulating references, and be profiled periodically. Worker recycling can be a pragmatic safety valve.

---


## 8. Testing, Debugging & Code Quality (171–180)

### 171. Unit vs integration vs e2e tests?

**Answer:** Unit: isolated functions/classes (mocks). Integration: real DB/cache/HTTP boundaries. E2E: full user flows. Pyramid: many unit, fewer e2e.

#### Example

```python
# Unit:
assert add(2, 3) == 5

# Integration:
# test API + real test database

# E2E:
# browser -> login -> checkout -> confirmation
```

#### Better Understanding

A healthy test suite usually has many fast unit tests, a useful layer of integration tests, and fewer slower end-to-end tests.

### 172. What is pytest and why prefer it?

**Answer:** Popular test runner: fixtures, parametrize, plugins, clear assert introspection. De facto standard over unittest for many teams.

#### Example

```python
def test_add():
    assert 2 + 3 == 5

# pytest discovers test_*.py / *_test.py by convention.
# Run:
# pytest
```

#### Better Understanding

pytest is popular because fixtures, parametrization, plugins, and assertion reporting make tests concise and expressive.

### 173. What are pytest fixtures?

**Answer:** Reusable setup/teardown injected into tests by name. Scopes: function/class/module/session. Compose fixtures for DB sessions, clients, users.

#### Example

```python
import pytest

@pytest.fixture
def user():
    return {"name": "Ana"}

def test_user(user):
    assert user["name"] == "Ana"
```

#### Better Understanding

Fixtures centralize reusable setup and cleanup. Choose the smallest practical scope to avoid unnecessary shared state.

### 174. How do you test FastAPI/Django APIs?

**Answer:** FastAPI: `TestClient`/`httpx.ASGITransport`. Django: `APIClient`/`Client`. Prefer DB transactions rolled back per test; factory_boy/faker for data.

#### Example

```python
from fastapi.testclient import TestClient

client = TestClient(app)

def test_users():
    response = client.get("/users")
    assert response.status_code == 200
```

#### Better Understanding

API tests should verify status codes, response schemas, important business behavior, authentication/authorization, and database side effects—not just that the endpoint returns 200.

### 175. What is mocking? When is it wrong?

**Answer:** Replace dependencies with fakes (`unittest.mock`, `respx`). Over-mocking tests implementation details and misses integration bugs — mock at boundaries.

#### Example

```python
from unittest.mock import Mock

payment_gateway = Mock()
payment_gateway.charge.return_value = {"id": "pay_123"}

# Mock the external boundary rather than internal implementation details.
```

#### Better Understanding

Mock unstable or expensive external boundaries when appropriate, but keep enough integration tests to catch wiring and contract problems.

### 176. What is TDD?

**Answer:** Red-Green-Refactor: write failing test → implement → clean up. Improves design and regression safety when practiced pragmatically.

#### Example

```python
# 1. Red: write a failing test
# 2. Green: implement the smallest solution
# 3. Refactor: improve design while keeping tests green
```

#### Better Understanding

TDD is a feedback loop, not a requirement to test every trivial line before writing any code. Use it where it improves design and confidence.

### 177. How do you debug production issues?

**Answer:** Structured logs + correlation IDs, metrics/traces, reproduce with same inputs, feature flags, careful hotfixes, postmortems. Don’t debug only via SSH print statements.

#### Example

```python
# Production debugging:
# request ID -> logs -> trace -> deployment diff
#                         |
#                         +-> database/external dependency
#
# Reproduce, patch, test, deploy, monitor.
```

#### Better Understanding

Start with evidence: error tracker, logs, traces, metrics, and recent changes. Preserve a clear timeline and avoid risky ad-hoc production edits.

### 178. What is linting/formatting stack?

**Answer:** `ruff`/`flake8`, `black`/`ruff format`, `isort`, `mypy`/`pyright`. Enforce in CI/pre-commit for consistent quality.

#### Example

```python
# pyproject.toml can configure:
# Ruff
# Black/ruff format
# mypy or pyright
#
# CI:
# lint -> type check -> test
```

#### Better Understanding

Automated formatting and linting reduce review noise; type checking catches a different class of problems. Run them consistently in CI.

### 179. What is coverage? Is 100% the goal?

**Answer:** Measures which lines ran in tests. High coverage helps but doesn’t guarantee correctness. Prefer meaningful assertions over chasing 100%.

#### Example

```python
# If 80 of 100 executable lines run:
# line coverage = 80%

# But this test:
# assert result is not None
# may cover code without checking correctness.
```

#### Better Understanding

Coverage is a signal, not a quality score. Focus on important behavior, edge cases, failure paths, and meaningful assertions.

### 180. How do you write a good bug report / ticket?

**Answer:** Expected vs actual, steps to reproduce, environment, logs/IDs, impact/severity, screenshots. Clear titles help triage.

---

## 9. DevOps, Security & System Design Basics (181–200)

#### Example

```python
# Good bug ticket:
# Title: Checkout returns 500 when coupon is expired
# Steps: ...
# Expected: 400 with validation error
# Actual: 500
# Environment: production
# Request ID: ...
# Impact: ...
```

#### Better Understanding

A good ticket lets another engineer reproduce the issue without a meeting. Include exact inputs, expected/actual behavior, environment, and impact.

---


## 9. DevOps, Security & System Design Basics (181–200)

### 181. What is CI/CD?

**Answer:** Continuous Integration: auto build/test on every push. Continuous Delivery/Deployment: auto promote to staging/prod. Catch bugs early; ship smaller changes.

#### Example

```python
# CI pipeline:
# push -> install -> lint -> test -> build image
#
# CD:
# deploy -> smoke test -> staging/prod
```

#### Better Understanding

CI gives fast feedback on changes. Continuous delivery/deployment automates the path toward release while keeping quality gates in place.

### 182. What is Docker? Why use it for Python apps?

**Answer:** Containers package app + runtime + deps. Same behavior across machines. Dockerfile defines image; Compose for local multi-service (app/db/redis).

#### Example

```python
# Dockerfile
FROM python:3.12-slim
WORKDIR /app
COPY requirements.txt .
RUN pip install -r requirements.txt
COPY . .
CMD ["python", "app.py"]
```

#### Better Understanding

Containers package the application environment so it behaves consistently across developer machines, CI, and deployment platforms.

### 183. Difference between image and container?

**Answer:** Image: immutable template. Container: running instance of an image. Like class vs object.

#### Example

```python
# Image = template
# Container = running instance

# docker build -> image
# docker run  -> container
```

#### Better Understanding

Think of an image as a packaged filesystem/configuration and a container as a process created from that image.

### 184. What is Kubernetes at a high level?

**Answer:** Orchestrates containers: scheduling, scaling, health checks, rolling updates, service discovery. Useful at scale; overkill for tiny apps.

#### Example

```python
# Kubernetes:
# Deployment -> desired replicas
# Service -> stable network endpoint
# Pod -> one or more containers
# Probe -> health/readiness checks
```

#### Better Understanding

Kubernetes automates container scheduling and operations, but its complexity should be justified by scale and operational requirements.

### 185. 12-factor app principles (name a few)?

**Answer:** Codebase in VCS, explicit deps, config in env, backing services as attached resources, build/release/run stages, stateless processes, port binding, logs as event streams.

#### Example

```python
# Example 12-factor ideas:
# config -> environment
# dependencies -> explicit lock/manifest
# logs -> stdout/stderr
# process -> stateless
# backing DB/Redis -> external service
```

#### Better Understanding

The goal is repeatable, portable deployments with clear separation between code, configuration, dependencies, and infrastructure.

### 186. How do you manage secrets?

**Answer:** Env vars for simple cases; Vault/AWS Secrets Manager/GCP Secret Manager for production. Never commit secrets; rotate regularly; least privilege IAM.

#### Example

```python
# Local/simple:
DATABASE_URL = os.environ["DATABASE_URL"]

# Production:
# use a managed secret store and grant only required access.
```

#### Better Understanding

Never hard-code production credentials or commit them to Git. Rotate secrets and give services the minimum permissions they need.

### 187. What is HTTPS/TLS doing?

**Answer:** Encrypts traffic and authenticates the server (via certificates). Prevents eavesdropping/tampering. Terminate TLS at load balancer or app.

#### Example

```python
# Client
#   | encrypted TLS connection
#   v
# Server certificate + private key
#
# TLS provides confidentiality and server authentication.
```

#### Better Understanding

HTTPS protects data in transit from eavesdropping and tampering and lets the client verify the server's identity through certificates.

### 188. OWASP Top risks relevant to APIs?

**Answer:** Broken auth, injection, SSRF, security misconfig, vulnerable components, excessive data exposure, lack of rate limiting, improper asset management. Validate inputs; patch deps.

#### Example

```python
# Common API risks:
# broken authorization
# injection
# SSRF
# insecure configuration
# vulnerable dependencies
# excessive data exposure
# weak rate limiting
```

#### Better Understanding

Security should be threat-model driven. Validate inputs, enforce authorization server-side, patch dependencies, restrict network access, and log security-relevant events safely.

### 189. How would you design a URL shortener (high level)?

**Answer:** API to create/redirect; store `code → long_url`; generate unique codes (hash/base62 id); cache hot redirects in Redis; analytics async; DB for durability.

#### Example

```python
# Create:
POST /urls -> generate code -> DB(code, long_url)

# Redirect:
GET /abc123 -> Redis/DB lookup -> HTTP 302/301

# Cache popular codes in Redis.
```

#### Better Understanding

For a URL shortener, think about unique ID generation, redirect latency, hot-key caching, durability, abuse controls, and analytics volume.

### 190. How would you design a notification system?

**Answer:** API enqueues events → workers fan out to email/SMS/push providers; templates; user preferences; retries with backoff; idempotency; dead-letter queue for failures.

#### Example

```python
# API -> event queue
#       -> email worker
#       -> SMS worker
#       -> push worker
#
# Each worker:
# retry -> backoff -> dead-letter on repeated failure
```

#### Better Understanding

Separate notification generation from delivery. User preferences, idempotency, provider failures, retries, and observability are key design concerns.

### 191. Explain load balancer basics.

**Answer:** Distributes traffic across instances (round-robin, least connections). Health checks remove bad nodes. Often terminates TLS and handles sticky sessions if needed.

#### Example

```python
# Internet
#   |
# Load Balancer
#   |---- app-1
#   |---- app-2
#   |---- app-3
#
# Health checks remove unhealthy instances.
```

#### Better Understanding

A load balancer improves availability and distributes traffic. It can also terminate TLS, perform routing, and enforce some edge policies.

### 192. What is a reverse proxy (nginx)?

**Answer:** Sits in front of app servers: TLS, static files, rate limit, buffering, routing. Clients talk to nginx; nginx talks to Gunicorn/Uvicorn.

#### Example

```python
# Client -> nginx -> Gunicorn/Uvicorn -> Python app
#
# nginx can handle:
# TLS
# static files
# buffering
# routing
# rate limits
```

#### Better Understanding

A reverse proxy hides backend instances from clients and centralizes useful edge concerns such as TLS termination and static content.

### 193. CAP theorem in one sentence?

**Answer:** In a partition, a distributed system must choose Consistency or Availability (Partition tolerance assumed). Practical systems tune this tradeoff.

#### Example

```python
# During a network partition:
# choose stronger consistency
# OR
# choose higher availability
#
# Partition tolerance is assumed in a distributed system.
```

#### Better Understanding

CAP applies when a network partition occurs. It is not simply saying that a system can only ever have two of the three properties.

### 194. How do you make a Python service observable?

**Answer:** Structured JSON logs, metrics (latency/error/QPS), distributed tracing (OpenTelemetry), health/readiness endpoints, alerting on SLOs.

#### Example

```python
# Observability:
# logs -> what happened
# metrics -> how much/how often
# traces -> where time went
# alerts -> when action is needed
#
# /health/live
# /health/ready
```

#### Better Understanding

Good observability connects a request across logs, metrics, and traces and lets the team detect problems through meaningful SLOs rather than noisy alerts.

### 195. Blue-green vs rolling vs canary deploys?

**Answer:** Blue-green: switch traffic between two environments. Rolling: gradually replace instances. Canary: small % traffic to new version first. Canary reduces blast radius.

#### Example

```python
# Blue-green:
# blue = old
# green = new
# switch traffic

# Rolling:
# replace instances gradually

# Canary:
# send a small percentage to new version first
```

#### Better Understanding

Canary releases reduce blast radius. Blue-green makes rollback simple but requires two environments. Rolling deployments use resources more gradually.

### 196. What is idempotent consumer design for queues?

**Answer:** Store processed message IDs; use unique business keys; upsert instead of insert; safe retries. Prevents duplicate side effects under at-least-once delivery.

#### Example

```python
def process(message):
    if db.exists_processed_id(message.id):
        return

    db.insert_processed_id(message.id)
    perform_side_effects(message)
```

#### Better Understanding

In real systems, make the business operation and deduplication as atomic as practical. Unique constraints are often safer than relying only on an application-level check.

### 197. How do you handle file uploads safely?

**Answer:** Limit size/type, scan/validate content, store outside web root/S3 with random keys, virus scan if needed, never trust filenames, serve via signed URLs.

#### Example

```python
# Safe upload flow:
# validate size -> inspect content/type -> random storage key
# -> malware scan if required -> private object storage
# -> signed URL for download
```

#### Better Understanding

Never trust a client-provided filename or MIME type. Treat uploaded files as untrusted input and keep them out of executable/public paths unless intentionally served.

### 198. Difference between authentication and authorization?

**Answer:** Authentication: who you are. Authorization: what you’re allowed to do. Implement both (JWT/session + roles/permissions/policies).

#### Example

```python
# Authentication:
# "Is this request from user 42?"

# Authorization:
# "Can user 42 delete order 123?"
```

#### Better Understanding

Authentication establishes identity. Authorization checks permissions for a specific action/resource. Both must be enforced server-side.

### 199. How would you approach designing a rate-limited public API?

**Answer:** API keys, Redis sliding window/token bucket per key, gateway enforcement, clear 429s, tiers/quotas, monitoring abuse, WAF for volumetric attacks.

#### Example

```python
# Example:
# API key A -> 100 req/min
# API key B -> 1000 req/min
#
# Redis token bucket/sliding window
# + gateway enforcement
# + 429 Retry-After
# + monitoring/abuse detection
```

#### Better Understanding

A production rate limiter needs a clear identity key, algorithm, distributed state if required, quotas/tiers, correct 429 responses, and monitoring for abuse.

### 200. Walk through debugging a 500 error in production.

**Answer:** Check error tracker (Sentry) for stack + request id → correlate logs/traces → identify recent deploys → reproduce in staging → fix with test → deploy hotfix → verify metrics/error rate drops → write postmortem if needed.

#### Example

```python
# 500-debug workflow:
# 1. Find error in Sentry/error tracker
# 2. Get request/correlation ID
# 3. Inspect logs + trace
# 4. Check recent deploy/config changes
# 5. Reproduce safely
# 6. Add regression test
# 7. Deploy fix
# 8. Verify error rate/latency
```

#### Better Understanding

Do not stop after fixing the exception. Verify the metric recovered, check for related failures, and document the root cause and prevention when the incident warrants it.

---

## Quick Revision: Questions 1–200
# Quick Interview Revision 1-60

| # | Topic | Remember |
|---|---|---|
| 1 | List vs Tuple | Mutable vs immutable |
| 2 | `==` vs `is` | Value vs identity |
| 3 | Mutable vs Immutable | Can change vs cannot change |
| 4 | `*args`, `**kwargs` | Positional tuple, keyword dict |
| 5 | Generator | Lazy, one-at-a-time |
| 6 | GIL | CPython thread execution limitation |
| 7 | Method Types | `self`, `cls`, neither |
| 8 | Decorator | Wrap/modify behavior |
| 9 | Comprehension | List now vs generator later |
| 10 | `__new__` vs `__init__` | Create vs initialize |
| 11 | Dunder Methods | Python object protocols |
| 12 | Memory | Reference counting + GC in CPython |
| 13 | Copy | Shared nested objects vs recursive copy |
| 14 | `/` and `*` | Positional-only vs keyword-only |
| 15 | EAFP/LBYL | Try first vs check first |
| 16 | `__main__` | Run directly vs imported |
| 17 | `range` | Python 3 replacement for `xrange` |
| 18 | Context Manager | Setup + guaranteed cleanup |
| 19 | `pass/continue/break` | Do nothing / skip / stop |
| 20 | `append/extend` | One item / many items |
| 21 | Swap | `a, b = b, a` |
| 22 | Lambda | Small anonymous function |
| 23 | LEGB | Local → Enclosing → Global → Built-in |
| 24 | `zip` | Combine/unpack iterables |
| 25 | `remove/pop/del` | Value / index+return / delete |
| 26 | F-string | Easy string formatting |
| 27 | Exceptions | `try/except/else/finally` |
| 28 | `None` | Absence of value |
| 29 | Duck Typing | Behavior over type |
| 30 | Module/Package | File vs organized namespace |
| 31 | Virtual Environment | Isolated dependencies |
| 32 | pip/Poetry/Pipenv | Package vs project management |
| 33 | `defaultdict/Counter` | Defaults / counting |
| 34 | `enumerate` | Index + value |
| 35 | `str/repr` | User-friendly / developer-friendly |
| 36 | Large Files | Stream instead of loading all |
| 37 | Type Hints | Documentation + static analysis |
| 38 | Dataclass | Less boilerplate for data classes |
| 39 | `:=` | Assign + use in expression |
| 40 | `async def` | Coroutines + async I/O |
| 41 | List Complexity | Index O(1), search O(n), sort O(n log n) |
| 42 | Dict/Set Complexity | Average O(1) |
| 43 | `deque` | Fast operations at both ends |
| 44 | Reverse | `[::-1]`, `reverse()`, `reversed()` |
| 45 | Big-O | Growth rate as input increases |
| 46 | Find Duplicates | `set` / `Counter` |
| 47 | Hash Collision | Same hash, equality still matters |
| 48 | Array vs Linked List | Fast index vs node-based access |
| 49 | Stack vs Queue | LIFO vs FIFO |
| 50 | FIFO Queue | `deque.popleft()` |
| 51 | Binary Search | Sorted data, O(log n) |
| 52 | Recursion vs Iteration | Self-calls vs loops |
| 53 | Heap | Priority queue / top-k |
| 54 | Merge Sorted Lists | Two pointers, O(n + m) |
| 55 | Memoization | Cache repeated results |
| 56 | Sliding Window | Efficient contiguous range processing |
| 57 | Cycle Detection | Slow + fast pointers |
| 58 | BFS vs DFS | Queue vs stack/recursion |
| 59 | Trie | Prefix-based lookup |
| 60 | K-th Largest | Sort / heap / Quickselect |

### OOP & Design
- **61:** OOP pillars → Encapsulation, Abstraction, Inheritance, Polymorphism
- **62:** Inheritance = is-a; Composition = has-a
- **63:** MRO → Python's method lookup order
- **64:** ABC → explicit abstract contract
- **65:** Polymorphism → same interface, different behavior
- **66:** Singleton → one shared instance; use cautiously
- **67:** Factory → centralize object creation
- **68:** Dependency Injection → pass dependencies in
- **69:** Repository → isolate data-access details
- **70:** Strategy → interchangeable algorithms
- **71:** SOLID → five maintainability principles
- **72:** Loose coupling → easier change/testing
- **73:** Composition vs aggregation → lifecycle ownership
- **74:** Mixin → focused reusable behavior
- **75:** Encapsulation → conventions/properties/name mangling
- **76:** Property → attribute-style controlled access
- **77:** Observer → notify subscribers of events
- **78:** DRY/KISS/YAGNI → avoid duplication and unnecessary complexity
- **79:** Bad inheritance → deep/fragile/non-is-a hierarchies
- **80:** Interface → ABC, Protocol, or duck typing

### Web Frameworks
- **81:** Django vs Flask vs FastAPI → choose by project needs
- **82:** WSGI vs ASGI → sync interface vs async-capable interface
- **83:** Django MVT → Model, View, Template
- **84:** Migrations → version-controlled schema changes
- **85:** Relationships → FK, OneToOne, ManyToMany
- **86:** `select_related` vs `prefetch_related` → avoid N+1
- **87:** N+1 → repeated related-object queries
- **88:** Flask factory → configurable/testable app creation
- **89:** Blueprint → modular Flask routes
- **90:** Pydantic → validation/serialization
- **91:** `Depends()` → FastAPI dependency injection
- **92:** CORS → browser cross-origin policy
- **93:** Middleware → cross-cutting request/response logic
- **94:** Signals → decoupled notifications
- **95:** DRF → Django REST API toolkit
- **96:** Serializer vs ModelSerializer → manual vs model-derived fields
- **97:** FBV vs CBV → explicit functions vs reusable class behavior
- **98:** Background tasks → lightweight post-response work
- **99:** Uvicorn → ASGI server
- **100:** FastAPI structure → thin routers, services, data layer
- **101:** Settings → environment-specific configuration
- **102:** Flask `g` → request-scoped storage
- **103:** CSRF → protect cookie-authenticated browser requests
- **104:** Django sessions → client identifier + session backend
- **105:** Jinja2 → templating engine
- **106:** `response_model` → validate/filter API output
- **107:** API versioning → compatibility management
- **108:** Django Admin → internal CRUD
- **109:** Request lifecycle → middleware → routing → view → response
- **110:** Static files → CDN/nginx/object storage in production

### REST & HTTP
- **111:** REST → resource-oriented HTTP architecture
- **112:** Methods/idempotency → understand HTTP semantics
- **113:** Status codes → communicate outcome clearly
- **114:** 401 vs 403 → authentication vs permission
- **115:** Idempotency key → safe retries
- **116:** REST vs GraphQL vs gRPC → different API trade-offs
- **117:** HATEOAS → links/actions in responses
- **118:** Pagination → offset or cursor
- **119:** Content negotiation → `Accept` / `Content-Type`
- **120:** JWT → header.payload.signature; readable payload
- **121:** Cookies vs bearer tokens → different browser/security trade-offs
- **122:** OAuth2 vs OIDC → authorization vs identity
- **123:** Deprecation → communicate, migrate, then remove
- **124:** Error body → consistent machine-readable shape
- **125:** Rate limiting → protect availability/fairness
- **126:** PUT vs PATCH → replacement vs partial update
- **127:** CORS → browser cross-origin control
- **128:** Safe vs unsafe methods → read-only intent vs state change
- **129:** API security → layered controls
- **130:** OpenAPI → API contract/documentation

### Databases
- **131:** SQL vs NoSQL → query/consistency/data-model trade-offs
- **132:** ACID → reliable transactions
- **133:** Indexes → faster reads, slower writes/storage cost
- **134:** PK/UNIQUE/FK → identity, uniqueness, relationships
- **135:** INNER vs LEFT JOIN → matched rows vs all left rows
- **136:** Normalization → reduce redundancy; denormalization → deliberate redundancy
- **137:** Isolation → control concurrent transaction visibility
- **138:** Locking → optimistic vs pessimistic
- **139:** Connection pool → reuse DB connections
- **140:** SQL injection → parameterized queries
- **141:** ORM vs SQL → use the simplest suitable abstraction
- **142:** Migrations → reproducible schema evolution
- **143:** Eventual consistency → temporary staleness then convergence
- **144:** Redis → cache/session/rate-limit/queue use cases
- **145:** Cache strategies → cache-aside/write-through
- **146:** Cache stampede → protect hot keys/origin
- **147:** Zero-downtime migrations → expand-contract
- **148:** EXPLAIN → inspect query execution plans
- **149:** MongoDB vs PostgreSQL → document vs relational strengths
- **150:** JSONB → semi-structured PostgreSQL data
- **151:** Soft deletes → preserve rows with deletion marker
- **152:** Rollback → backups + forward-fix/expand-contract
- **153:** SQLAlchemy Engine vs Session → connectivity vs unit of work
- **154:** CASCADE → automatic child changes; use carefully
- **155:** UUID vs auto-increment → distributed generation vs compact sequential IDs

### Async, Testing, DevOps & System Design
- **156:** Threading/processes/asyncio → choose by workload
- **157:** Event loop → schedules cooperative async work
- **158:** `gather`/`create_task` → group waiting vs scheduling
- **159:** Don't use async blindly → CPU/blocking workloads may need other models
- **160:** Blocking in async → `to_thread`/executor/worker
- **161:** Celery → distributed background jobs
- **162:** At-least-once → idempotent consumers
- **163:** Profiling → measure API, Python, DB, dependencies
- **164:** Scaling → vertical vs horizontal
- **165:** Gunicorn → master + worker process model
- **166:** Backpressure → slow/reject producers when consumers are overloaded
- **167:** Circuit breaker → fail fast around unhealthy dependencies
- **168:** `async with` → async resource lifecycle
- **169:** CPU-bound vs I/O-bound → different optimization strategies
- **170:** Memory leaks → bound caches, close resources, profile/recycle
- **171:** Test types → unit, integration, e2e
- **172:** pytest → fixtures, parametrization, plugins
- **173:** Fixtures → reusable test setup/teardown
- **174:** API testing → verify behavior, auth, schemas, side effects
- **175:** Mocking → isolate external boundaries without over-mocking
- **176:** TDD → Red, Green, Refactor
- **177:** Production debugging → logs, traces, metrics, deploy history
- **178:** Quality stack → lint, format, type-check, test
- **179:** Coverage → signal, not correctness guarantee
- **180:** Bug reports → reproduce, expected/actual, impact, evidence
- **181:** CI/CD → automate build/test/release
- **182:** Docker → package runtime and dependencies
- **183:** Image vs container → template vs running instance
- **184:** Kubernetes → container orchestration
- **185:** 12-factor → portable, configurable services
- **186:** Secrets → secret stores, rotation, least privilege
- **187:** TLS → encryption + server authentication
- **188:** OWASP/API risks → validate, authorize, patch, monitor
- **189:** URL shortener → code mapping + cache + analytics
- **190:** Notifications → queue + workers + retries
- **191:** Load balancer → distribute traffic and remove unhealthy nodes
- **192:** Reverse proxy → edge routing/TLS/static handling
- **193:** CAP → consistency vs availability during partitions
- **194:** Observability → logs + metrics + traces
- **195:** Deployments → blue-green, rolling, canary
- **196:** Idempotent consumers → dedupe and safe retries
- **197:** File uploads → validate, scan, isolate, signed URLs
- **198:** Authentication vs authorization → identity vs permission
- **199:** Rate-limited API → keys + distributed limiter + monitoring
- **200:** 500 debugging → evidence → reproduce → fix → verify

---

## Quick Study Tips (2 YOE)

- Be ready to **write code** on lists/dicts, SQL joins, and a small FastAPI/Django endpoint.
- Explain **tradeoffs** (sync vs async, SQL vs cache, ORM vs raw) more than buzzwords.
- Know **your stack deeply**: one framework, one DB, Redis, and how you deploy.
- Prepare **2–3 project stories**: bottleneck you fixed, bug you hunted, design choice you owned.

---

*Good luck with your interviews.*
