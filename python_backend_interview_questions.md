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

---

## 2. Data Structures & Algorithms (41–60)

### 41. Time complexity of common list operations?

**Answer:** Indexing/append amortized O(1). Insert/delete at start O(n). Membership O(n). Sorting O(n log n).

### 42. Time complexity of dict/set operations?

**Answer:** Average O(1) for get/set/delete/membership (hash table). Worst case O(n) with pathological collisions. Keys must be hashable.

### 43. When would you use a deque?

**Answer:** `collections.deque` for O(1) append/pop from both ends — queues, sliding windows, BFS. Lists are O(n) at the left end.

### 44. How do you reverse a string/list?

**Answer:** Slicing: `s[::-1]` or `list.reverse()` / `reversed()`. For interviews, also know two-pointer in-place reverse for lists.

### 45. Explain Big-O briefly.

**Answer:** Asymptotic upper bound on growth of time/space as input size grows. Focus on dominant term: O(1), O(log n), O(n), O(n log n), O(n²), O(2ⁿ).

### 46. How would you find duplicates in a list?

**Answer:** Use a `set` while iterating; if seen again, it’s a duplicate. Or `Counter` for frequencies. Sorting + adjacent compare is O(n log n) without extra hash memory tradeoffs.

### 47. What is a hash collision? How does Python handle it?

**Answer:** Two keys map to the same hash bucket. CPython dicts use open addressing with probing. Collisions degrade performance but are handled correctly for correctness.

### 48. Difference between array (list) and linked list conceptually?

**Answer:** Arrays: contiguous, O(1) index, costly mid insert. Linked lists: O(1) insert/delete given node, O(n) access. Python `list` is dynamic array; linked lists via custom nodes or `deque` internals.

### 49. Explain stack vs queue.

**Answer:** Stack: LIFO (push/pop same end). Queue: FIFO (enqueue one end, dequeue other). Use list/`deque` accordingly.

### 50. How do you implement a FIFO queue in Python?

**Answer:** Prefer `collections.deque` with `append`/`popleft`. `queue.Queue` for thread-safe use. Avoid `list.pop(0)` for performance.

### 51. What is binary search? Requirements?

**Answer:** Search sorted data by repeatedly halving the range — O(log n). Data must be sorted (or searchable via monotonic predicate). `bisect` module helps.

### 52. Explain recursion vs iteration.

**Answer:** Recursion: function calls itself; elegant for trees/divide-conquer; risk of stack overflow. Iteration: loops; usually more memory-efficient. Tail recursion isn’t optimized in CPython.

### 53. What is a heap? When use `heapq`?

**Answer:** Binary heap for priority queues. `heapq` provides min-heap. Use for top-k, merge sorted streams, Dijkstra. Max-heap via negated values.

### 54. How do you merge two sorted lists?

**Answer:** Two-pointer merge: compare heads, append smaller, advance — O(n+m). Or `heapq.merge` for multiple iterables lazily.

### 55. What is memoization?

**Answer:** Caching function results for given inputs to avoid recomputation. `@functools.lru_cache` or manual dict. Classic for Fibonacci/DP.

### 56. Explain sliding window pattern.

**Answer:** Maintain a window over a sequence that expands/contracts to satisfy a condition (max sum of size k, longest substring without repeat). Often O(n) vs O(n²) nested loops.

### 57. How do you detect a cycle in a linked list?

**Answer:** Floyd’s tortoise and hare: slow/fast pointers; if they meet, cycle exists. Or track visited node ids in a set.

### 58. Difference between BFS and DFS?

**Answer:** BFS (queue): level-order, shortest path in unweighted graphs. DFS (stack/recursion): explores deep paths first; good for connectivity, topological sort, path existence.

### 59. What is a trie used for?

**Answer:** Prefix tree for strings — autocomplete, dictionary lookup, IP routing prefixes. Fast prefix queries; memory heavier than hash sets.

### 60. How would you find the k-th largest element?

**Answer:** Sort O(n log n), or min-heap of size k O(n log k), or Quickselect average O(n). `heapq.nlargest(k, iterable)[-1]`.

---

## 3. OOP & Design Patterns (61–80)

### 61. What are the four pillars of OOP?

**Answer:** Encapsulation, Abstraction, Inheritance, Polymorphism. Python supports all; encapsulation is convention-based (`_protected`, `__name_mangling`).

### 62. Difference between inheritance and composition?

**Answer:** Inheritance: “is-a” via subclassing. Composition: “has-a” via containing objects. Prefer composition for flexibility and looser coupling.

### 63. What is MRO? How does Python resolve it?

**Answer:** Method Resolution Order — the order Python searches for attributes in multiple inheritance. C3 linearization; inspect with `Class.__mro__` or `help(Class)`.

### 64. What is an abstract base class (ABC)?

**Answer:** `abc.ABC` + `@abstractmethod` define interfaces that subclasses must implement. Instantiating an incomplete ABC raises `TypeError`.

### 65. Explain polymorphism with an example.

**Answer:** Same interface, different behavior: `len()` works on str/list/dict via `__len__`. Or subclasses overriding `draw()` with different shapes.

### 66. What is the Singleton pattern? Concerns?

**Answer:** Ensure one instance. In Python: module-level object, metaclass, or `__new__`. Can hurt testability and hide dependencies; prefer DI when possible.

### 67. What is the Factory pattern?

**Answer:** A function/class that creates objects without exposing construction logic. Useful when concrete type depends on config/runtime input.

### 68. What is Dependency Injection?

**Answer:** Pass dependencies into a class/function rather than creating them inside. Improves testability and decoupling (mock DB/repo in tests).

### 69. Explain Repository pattern in backends.

**Answer:** Abstracts data access behind an interface (`UserRepository.get_by_id`). Services depend on the repo, not ORM details — cleaner layers and easier mocking.

### 70. What is the Strategy pattern?

**Answer:** Encapsulate interchangeable algorithms behind a common interface (e.g., payment processors, sort strategies). Swap at runtime without if/else sprawl.

### 71. What is SOLID? Name each letter.

**Answer:** Single Responsibility, Open/Closed, Liskov Substitution, Interface Segregation, Dependency Inversion. Guides maintainable OOP design.

### 72. What is tight vs loose coupling?

**Answer:** Tight: components hardwired together; hard to change/test. Loose: interact via interfaces/events; easier to swap implementations.

### 73. Difference between composition and aggregation?

**Answer:** Both are “has-a”. Composition: owned lifecycle (part dies with whole). Aggregation: shared/independent lifecycle. Conceptual UML distinction.

### 74. What are mixins?

**Answer:** Classes providing reusable methods via multiple inheritance without being standalone base types (e.g., `JsonSerializableMixin`). Keep them focused.

### 75. How does encapsulation work in Python?

**Answer:** No true private members. Convention: `_internal`, `__mangled`. Properties (`@property`) control access. Trust the developer culture.

### 76. What is a property in Python?

**Answer:** `@property` turns a method into attribute-like access with getter/setter/deleter — validation without changing call sites to methods.

### 77. Explain the Observer pattern.

**Answer:** Subject notifies registered observers on state change (events, pub/sub). Django signals and many event buses follow this idea.

### 78. What is DRY, KISS, YAGNI?

**Answer:** Don’t Repeat Yourself; Keep It Simple Stupid; You Aren’t Gonna Need It. Avoid premature abstraction and unused features.

### 79. When is inheritance a bad idea?

**Answer:** Deep hierarchies, fragile base classes, forcing “is-a” that isn’t true, sharing code that isn’t a true subtype. Prefer composition/mixins carefully.

### 80. What is an interface in Python terms?

**Answer:** No formal `interface` keyword. Use ABCs, Protocols (`typing.Protocol` — structural subtyping), or duck typing documentation.

---

## 4. Web Frameworks — Django / Flask / FastAPI (81–110)

### 81. Django vs Flask vs FastAPI — when to use each?

**Answer:** Django: batteries-included monoliths (ORM, admin, auth). Flask: minimal, flexible microservices/APIs. FastAPI: modern async APIs with automatic OpenAPI and type-hint validation; great for high-concurrency I/O services.

### 82. What is WSGI vs ASGI?

**Answer:** WSGI is the sync Python web standard (Django classic, Flask). ASGI supports async and WebSockets (FastAPI, Django ASGI, Starlette). Uvicorn/Hypercorn are ASGI servers; Gunicorn often WSGI (or with Uvicorn workers).

### 83. Explain Django MVT.

**Answer:** Model (data), View (request logic), Template (presentation). Similar to MVC; Django’s “view” is closer to a controller.

### 84. What are Django migrations?

**Answer:** Versioned schema changes generated from model changes (`makemigrations` / `migrate`). Applied in order; keep them in VCS. Avoid editing applied migrations casually.

### 85. Difference between Django `ForeignKey`, `OneToOne`, `ManyToMany`?

**Answer:** FK: many-to-one. OneToOne: unique FK both ways. M2M: through table (implicit or explicit). Choose based on cardinality.

### 86. What is `select_related` vs `prefetch_related`?

**Answer:** `select_related`: SQL JOINs for FK/OneToOne (single query). `prefetch_related`: separate query + Python join for M2M/reverse FK. Prevents N+1 queries.

### 87. What causes the N+1 query problem?

**Answer:** Looping over objects and hitting related fields lazily, one query per row. Fix with `select_related`/`prefetch_related`, eager loading, or batch queries.

### 88. Flask: application factory pattern — why?

**Answer:** `create_app()` builds the app with config/extensions. Enables multiple configs, testing, and avoids circular imports from global app objects.

### 89. What are Flask blueprints?

**Answer:** Modular route groups with their own templates/static. Register on the app — scales larger Flask projects.

### 90. FastAPI: what does Pydantic do?

**Answer:** Validates and serializes request/response data from type hints. Gives clear 422 errors and OpenAPI schemas automatically.

### 91. FastAPI dependency injection — purpose?

**Answer:** `Depends()` injects shared logic (DB sessions, auth, pagination). Reusable, testable, composable request plumbing.

### 92. How do you handle CORS?

**Answer:** Configure allowed origins/methods/headers via middleware (`CORSMiddleware` in FastAPI/Starlette, `django-cors-headers`, Flask-CORS). Never use `*` with credentials in production.

### 93. What is middleware?

**Answer:** Components that process requests/responses globally (auth, logging, CORS, GZip). In Django: middleware stack; in FastAPI/Starlette: ASGI middleware.

### 94. Explain Django signals briefly.

**Answer:** Decoupled notifications (`pre_save`, `post_save`, etc.). Useful for side effects; overuse hides control flow — prefer explicit service calls when clarity matters.

### 95. What is Django REST Framework (DRF)?

**Answer:** Toolkit for building REST APIs on Django: serializers, viewsets, routers, permissions, authentication, browsable API.

### 96. Serializer vs ModelSerializer in DRF?

**Answer:** Serializer: manual field definitions. ModelSerializer: auto fields from a model + create/update helpers. Customize validation as needed.

### 97. What are Django class-based views vs function-based?

**Answer:** FBVs: simple and explicit. CBVs: reuse via inheritance/mixins (ListView, APIView). Prefer clarity; CBVs help for standard CRUD patterns.

### 98. How does FastAPI background tasks work?

**Answer:** `BackgroundTasks` runs functions after the response is sent — fine for light work (email send). For heavy/reliable jobs use Celery/RQ/arq.

### 99. What is Uvicorn?

**Answer:** Lightning-fast ASGI server built on uvloop/httptools. Common production choice behind nginx for FastAPI/Starlette apps.

### 100. How do you structure a mid-size FastAPI project?

**Answer:** Separate routers, schemas (Pydantic), models, services/use-cases, repositories, dependencies, and config. Keep routers thin; business logic in services.

### 101. Django `settings.py` — environment-specific config?

**Answer:** Use env vars (`django-environ`, `pydantic-settings`), split settings modules, or 12-factor config. Never commit secrets.

### 102. What is Flask’s `g` object?

**Answer:** Request-scoped temporary storage for data during a request (e.g., current user, DB connection). Cleared after the request.

### 103. Explain CSRF protection.

**Answer:** Cross-Site Request Forgery: browser sends cookies on malicious sites’ requests. Django forms/middleware use CSRF tokens. APIs often use tokens/headers instead of cookie sessions alone.

### 104. How do sessions work in Django?

**Answer:** Server stores session data (DB/cache/file); client gets a session cookie id. Configurable backends. Prefer cache/DB for multi-instance deploys.

### 105. What is Jinja2?

**Answer:** Popular templating engine (Flask default, Django-inspired syntax). Used for HTML/email templates with inheritance and filters.

### 106. FastAPI `response_model` — why use it?

**Answer:** Filters/validates outgoing data, documents schema, and prevents leaking sensitive fields accidentally.

### 107. How do you version APIs in these frameworks?

**Answer:** URL prefix (`/api/v1`), headers, or Accept versioning. Mount versioned routers. Keep backward compatibility until clients migrate.

### 108. What is Django Admin good for?

**Answer:** Rapid internal CRUD UI for models. Customize list displays, filters, actions. Not a public-facing product UI.

### 109. Explain request lifecycle briefly (Django).

**Answer:** Request → middleware → URL resolve → view → (ORM/service) → response → middleware → client. Exceptions handled by handlers/middleware.

### 110. How do you serve static files in production?

**Answer:** Collect static (`collectstatic`), serve via CDN/nginx/S3 — not the app server. Whitenoise can serve from the app for simpler setups.

---

## 5. REST APIs & HTTP (111–130)

### 111. What is REST?

**Answer:** Architectural style: resources identified by URIs, manipulated via HTTP methods, stateless requests, representations (JSON/XML). Not a strict protocol — conventions vary.

### 112. Common HTTP methods and idempotency?

**Answer:** GET (read, idempotent, safe), POST (create/action, not idempotent), PUT (replace, idempotent), PATCH (partial update), DELETE (idempotent ideally). Idempotent: same effect if repeated.

### 113. What are common HTTP status codes you use?

**Answer:** 200 OK, 201 Created, 204 No Content, 400 Bad Request, 401 Unauthorized, 403 Forbidden, 404 Not Found, 409 Conflict, 422 Unprocessable, 429 Too Many Requests, 500 Internal Server Error.

### 114. 401 vs 403?

**Answer:** 401: not authenticated (missing/invalid credentials). 403: authenticated but not allowed. Some APIs blur them; be consistent.

### 115. What is idempotency key used for?

**Answer:** Client sends a unique key with POST so retries don’t create duplicates (payments, orders). Server stores key → result mapping.

### 116. REST vs GraphQL vs gRPC?

**Answer:** REST: resource URLs, simple caching/HTTP. GraphQL: client-shaped queries, one endpoint, over/under-fetching control. gRPC: binary Protobuf, strong contracts, great for service-to-service; less browser-native.

### 117. What is HATEOAS?

**Answer:** Hypermedia as the Engine of Application State — responses include links to related actions. Rarely fully adopted; “REST maturity” concept.

### 118. How do you design pagination?

**Answer:** Offset/limit (simple, can skip inconsistently) or cursor-based (stable for infinite scroll). Return `next`/`prev` links and totals when useful.

### 119. What is content negotiation?

**Answer:** Client and server agree on representation via `Accept` / `Content-Type` headers (JSON vs XML, etc.).

### 120. Explain JWT structure and risks.

**Answer:** Header.Payload.Signature (Base64URL). Stateless auth claims. Risks: long-lived tokens, secret leak, no easy revoke — use short TTL + refresh tokens + denylist if needed. Don’t put secrets in payload (it’s readable).

### 121. Cookie-based vs token-based auth?

**Answer:** Cookies: browser auto-sends; CSRF concerns; good for first-party web. Bearer tokens: explicit Authorization header; common for SPAs/mobile/APIs; store carefully (prefer httpOnly cookies for web XSS mitigation).

### 122. What is OAuth2 vs OpenID Connect?

**Answer:** OAuth2: authorization (delegated access). OIDC: identity layer on OAuth2 (who the user is — ID token). “Login with Google” is typically OIDC.

### 123. How do you version and deprecate APIs?

**Answer:** Version in path/header; announce deprecation; monitor usage; keep overlap period; document migration; eventually remove with notice.

### 124. What makes a good error response body?

**Answer:** Consistent shape: `code`, `message`, optional `details`/`fields`. Don’t leak stack traces in production. Map domain errors to HTTP statuses.

### 125. What is rate limiting? Where enforce it?

**Answer:** Cap requests per client/IP/API key. Enforce at gateway/nginx/API middleware/Redis counters. Return 429 + `Retry-After`.

### 126. PUT vs PATCH?

**Answer:** PUT replaces the whole resource (client sends complete state). PATCH applies partial updates. Prefer PATCH for sparse updates.

### 127. What is CORS and when do you need it?

**Answer:** Browser security: cross-origin XHR/fetch restricted unless server allows via CORS headers. Needed for SPAs on different origins calling your API.

### 128. Safe vs unsafe HTTP methods?

**Answer:** Safe methods (GET, HEAD, OPTIONS) shouldn’t change server state. Unsafe (POST, PUT, PATCH, DELETE) may. Caching proxies rely on this.

### 129. How do you secure an API? Checklist.

**Answer:** HTTPS, authn/authz, input validation, rate limits, least privilege DB users, secrets in vault/env, logging without PII, dependency updates, CORS lockdown, security headers.

### 130. What is OpenAPI/Swagger?

**Answer:** Spec for describing HTTP APIs. FastAPI generates it from code. Used for docs, client generation, contract testing.

---

## 6. Databases & ORM (131–155)

### 131. SQL vs NoSQL — when each?

**Answer:** SQL: structured data, strong consistency, complex joins, transactions. NoSQL (document/key-value): flexible schemas, horizontal scale, simple access patterns. Choose by query patterns and consistency needs.

### 132. What is ACID?

**Answer:** Atomicity, Consistency, Isolation, Durability — properties of reliable transactions in relational DBs.

### 133. Explain database indexes. Tradeoffs?

**Answer:** Structures (usually B-trees) that speed lookups/filters/sorts. Tradeoffs: slower writes, extra storage. Index columns used in WHERE/JOIN/ORDER BY carefully; avoid over-indexing.

### 134. What is a primary key vs unique vs foreign key?

**Answer:** PK uniquely identifies a row (often surrogate id). UNIQUE constrains uniqueness. FK enforces referential integrity to another table’s key.

### 135. INNER JOIN vs LEFT JOIN?

**Answer:** INNER: only matching rows both sides. LEFT: all left rows + matches from right (NULLs if none). RIGHT/FULL less common in app SQL.

### 136. What is normalization? Denormalization?

**Answer:** Normalization reduces redundancy (1NF–3NF typical). Denormalization adds redundancy for read performance. Balance consistency vs speed.

### 137. What is a transaction isolation level?

**Answer:** Controls visibility of concurrent transactions: Read Uncommitted, Read Committed, Repeatable Read, Serializable. Higher = fewer anomalies, more locking/contention.

### 138. Explain optimistic vs pessimistic locking.

**Answer:** Optimistic: assume rare conflicts; version column; fail on stale update. Pessimistic: lock rows (`SELECT FOR UPDATE`) during transaction. Choose based on contention.

### 139. What is connection pooling? Why needed?

**Answer:** Reuse DB connections instead of opening per request. Creating connections is expensive. Tools: SQLAlchemy pool, PgBouncer, Django CONN_MAX_AGE.

### 140. How do you prevent SQL injection?

**Answer:** Always parameterized queries / ORM bindings. Never concatenate user input into SQL. Validate/sanitize inputs as defense in depth.

### 141. ORM vs raw SQL — when raw?

**Answer:** ORM for CRUD and maintainability. Raw/SQLAlchemy Core for complex reports, window functions, performance-critical queries, DB-specific features. Measure with EXPLAIN.

### 142. What is Alembic / Django migrations role?

**Answer:** Schema migration tools that version DB changes with application code. Essential for team deploys and rollbacks strategy.

### 143. Explain eventual consistency.

**Answer:** System may temporarily show stale data but converges. Common in distributed/NoSQL/replicas. OK for feeds/caches; careful for balances/inventory.

### 144. What is Redis used for in backends?

**Answer:** Cache, session store, rate limiting, pub/sub, leaderboards, job queues (with RQ/Celery broker). In-memory, very fast; persistence optional.

### 145. Cache strategies: cache-aside vs write-through?

**Answer:** Cache-aside: app reads cache → miss → DB → populate cache. Write-through: write DB and cache together. Also write-behind, TTL eviction, stampede protection.

### 146. What is the thundering herd / cache stampede?

**Answer:** Many requests miss same hot key simultaneously and slam the DB. Mitigate with locking, soft TTL, probabilistic early refresh, or singleflight.

### 147. Explain database migrations zero-downtime tips.

**Answer:** Expand-contract: add columns nullable → deploy code → backfill → enforce constraints → remove old. Avoid destructive renames in one step. Feature flags help.

### 148. What is EXPLAIN / EXPLAIN ANALYZE?

**Answer:** Shows query plan (and actual timings with ANALYZE). Use to find sequential scans, bad joins, missing indexes.

### 149. Difference between MongoDB and PostgreSQL?

**Answer:** Postgres: relational, SQL, strong transactions, rich types/JSON too. Mongo: document store, flexible schema, horizontal sharding focus. Postgres often enough with JSONB.

### 150. What is JSONB in PostgreSQL?

**Answer:** Binary JSON storage with indexing (GIN) and querying. Good for semi-structured attributes without a separate document DB.

### 151. How do you handle soft deletes?

**Answer:** `deleted_at` timestamp instead of DELETE. Filter in queries/default managers. Tradeoffs: unique constraints, storage, accidental inclusion — document carefully.

### 152. What is a database migration rollback strategy?

**Answer:** Prefer forward-fix migrations. Keep backups. Test down migrations in staging. For production, restore from backup or reverse expand-contract if needed.

### 153. SQLAlchemy Session vs Engine?

**Answer:** Engine: connection pool + dialect. Session: unit of work / identity map for ORM objects. Commit/rollback at session boundaries.

### 154. What is `CASCADE` on foreign keys?

**Answer:** Deleting/updating parent auto-deletes/updates children. Convenient but dangerous — accidental mass deletes. Prefer explicit application deletes when unsure.

### 155. How do you choose between UUID and auto-increment IDs?

**Answer:** Auto-increment: simple, compact, sequential. UUID: safer for distributed generation, harder to guess, larger indexes. UUIDv7 improves sortability.

---

## 7. Async, Concurrency & Performance (156–170)

### 156. Threading vs multiprocessing vs asyncio?

**Answer:** Threading: good for I/O; limited by GIL for CPU. Multiprocessing: true parallelism for CPU-bound. Asyncio: single-thread cooperative concurrency for many I/O connections with less overhead.

### 157. What is an event loop?

**Answer:** Core of asyncio: schedules and runs coroutines, callbacks, and I/O ready events. Only one coroutine runs at a time until it awaits.

### 158. `asyncio.gather` vs `create_task`?

**Answer:** `gather` runs awaitables concurrently and waits for all. `create_task` schedules a coroutine on the loop immediately; you can await later. Fire-and-forget tasks need careful exception handling.

### 159. When should you not use async?

**Answer:** CPU-heavy work, libraries that are blocking-only without thread offload, simple CRUD with low concurrency. Async shines with many waiting connections.

### 160. How do you run blocking code in async apps?

**Answer:** `asyncio.to_thread()` or run in an executor. Don’t call blocking DB/HTTP drivers on the event loop.

### 161. What is Celery? Typical use cases?

**Answer:** Distributed task queue: background jobs, emails, image processing, scheduled tasks. Broker (Redis/RabbitMQ) + workers + optional result backend.

### 162. At-least-once vs exactly-once delivery?

**Answer:** Most queues are at-least-once → design idempotent consumers. Exactly-once is hard; often exactly-once processing via idempotency keys + dedupe store.

### 163. How do you profile a slow Python API?

**Answer:** Measure: APM (Datadog/New Relic), `cProfile`, Django Debug Toolbar, `py-spy`, slow query logs, EXPLAIN. Fix N+1, add indexes, cache, reduce payloads.

### 164. What is horizontal vs vertical scaling?

**Answer:** Vertical: bigger machine. Horizontal: more instances behind a load balancer. Horizontal needs stateless apps + shared store (DB/Redis).

### 165. How does Gunicorn worker model work?

**Answer:** Prefork workers handle requests. Sync workers: one request per worker. Use gevent/uvicorn workers for concurrency. Tune workers ≈ 2–4 × CPU for sync CPU-light apps (rule of thumb).

### 166. What is backpressure?

**Answer:** Slowing producers when consumers can’t keep up (queue limits, 429s, buffering). Prevents unbounded memory growth and cascading failure.

### 167. Explain circuit breaker pattern.

**Answer:** Stop calling a failing dependency temporarily; fail fast; retry after cooldown. Protects your service from cascading outages.

### 168. What is `async with` used for?

**Answer:** Asynchronous context managers (`__aenter__`/`__aexit__`) — e.g., async DB sessions, HTTP clients (`httpx.AsyncClient`).

### 169. Difference between CPU-bound and I/O-bound?

**Answer:** CPU-bound: computation (use multiprocessing/C extensions). I/O-bound: waiting on network/disk (threads/async help). Know which before optimizing.

### 170. How do you prevent memory leaks in long-running workers?

**Answer:** Avoid global caches without bounds, close connections, watch reference cycles, recycle workers (Gunicorn `max_requests`), profile with tracemalloc/`objgraph`.

---

## 8. Testing, Debugging & Code Quality (171–180)

### 171. Unit vs integration vs e2e tests?

**Answer:** Unit: isolated functions/classes (mocks). Integration: real DB/cache/HTTP boundaries. E2E: full user flows. Pyramid: many unit, fewer e2e.

### 172. What is pytest and why prefer it?

**Answer:** Popular test runner: fixtures, parametrize, plugins, clear assert introspection. De facto standard over unittest for many teams.

### 173. What are pytest fixtures?

**Answer:** Reusable setup/teardown injected into tests by name. Scopes: function/class/module/session. Compose fixtures for DB sessions, clients, users.

### 174. How do you test FastAPI/Django APIs?

**Answer:** FastAPI: `TestClient`/`httpx.ASGITransport`. Django: `APIClient`/`Client`. Prefer DB transactions rolled back per test; factory_boy/faker for data.

### 175. What is mocking? When is it wrong?

**Answer:** Replace dependencies with fakes (`unittest.mock`, `respx`). Over-mocking tests implementation details and misses integration bugs — mock at boundaries.

### 176. What is TDD?

**Answer:** Red-Green-Refactor: write failing test → implement → clean up. Improves design and regression safety when practiced pragmatically.

### 177. How do you debug production issues?

**Answer:** Structured logs + correlation IDs, metrics/traces, reproduce with same inputs, feature flags, careful hotfixes, postmortems. Don’t debug only via SSH print statements.

### 178. What is linting/formatting stack?

**Answer:** `ruff`/`flake8`, `black`/`ruff format`, `isort`, `mypy`/`pyright`. Enforce in CI/pre-commit for consistent quality.

### 179. What is coverage? Is 100% the goal?

**Answer:** Measures which lines ran in tests. High coverage helps but doesn’t guarantee correctness. Prefer meaningful assertions over chasing 100%.

### 180. How do you write a good bug report / ticket?

**Answer:** Expected vs actual, steps to reproduce, environment, logs/IDs, impact/severity, screenshots. Clear titles help triage.

---

## 9. DevOps, Security & System Design Basics (181–200)

### 181. What is CI/CD?

**Answer:** Continuous Integration: auto build/test on every push. Continuous Delivery/Deployment: auto promote to staging/prod. Catch bugs early; ship smaller changes.

### 182. What is Docker? Why use it for Python apps?

**Answer:** Containers package app + runtime + deps. Same behavior across machines. Dockerfile defines image; Compose for local multi-service (app/db/redis).

### 183. Difference between image and container?

**Answer:** Image: immutable template. Container: running instance of an image. Like class vs object.

### 184. What is Kubernetes at a high level?

**Answer:** Orchestrates containers: scheduling, scaling, health checks, rolling updates, service discovery. Useful at scale; overkill for tiny apps.

### 185. 12-factor app principles (name a few)?

**Answer:** Codebase in VCS, explicit deps, config in env, backing services as attached resources, build/release/run stages, stateless processes, port binding, logs as event streams.

### 186. How do you manage secrets?

**Answer:** Env vars for simple cases; Vault/AWS Secrets Manager/GCP Secret Manager for production. Never commit secrets; rotate regularly; least privilege IAM.

### 187. What is HTTPS/TLS doing?

**Answer:** Encrypts traffic and authenticates the server (via certificates). Prevents eavesdropping/tampering. Terminate TLS at load balancer or app.

### 188. OWASP Top risks relevant to APIs?

**Answer:** Broken auth, injection, SSRF, security misconfig, vulnerable components, excessive data exposure, lack of rate limiting, improper asset management. Validate inputs; patch deps.

### 189. How would you design a URL shortener (high level)?

**Answer:** API to create/redirect; store `code → long_url`; generate unique codes (hash/base62 id); cache hot redirects in Redis; analytics async; DB for durability.

### 190. How would you design a notification system?

**Answer:** API enqueues events → workers fan out to email/SMS/push providers; templates; user preferences; retries with backoff; idempotency; dead-letter queue for failures.

### 191. Explain load balancer basics.

**Answer:** Distributes traffic across instances (round-robin, least connections). Health checks remove bad nodes. Often terminates TLS and handles sticky sessions if needed.

### 192. What is a reverse proxy (nginx)?

**Answer:** Sits in front of app servers: TLS, static files, rate limit, buffering, routing. Clients talk to nginx; nginx talks to Gunicorn/Uvicorn.

### 193. CAP theorem in one sentence?

**Answer:** In a partition, a distributed system must choose Consistency or Availability (Partition tolerance assumed). Practical systems tune this tradeoff.

### 194. How do you make a Python service observable?

**Answer:** Structured JSON logs, metrics (latency/error/QPS), distributed tracing (OpenTelemetry), health/readiness endpoints, alerting on SLOs.

### 195. Blue-green vs rolling vs canary deploys?

**Answer:** Blue-green: switch traffic between two environments. Rolling: gradually replace instances. Canary: small % traffic to new version first. Canary reduces blast radius.

### 196. What is idempotent consumer design for queues?

**Answer:** Store processed message IDs; use unique business keys; upsert instead of insert; safe retries. Prevents duplicate side effects under at-least-once delivery.

### 197. How do you handle file uploads safely?

**Answer:** Limit size/type, scan/validate content, store outside web root/S3 with random keys, virus scan if needed, never trust filenames, serve via signed URLs.

### 198. Difference between authentication and authorization?

**Answer:** Authentication: who you are. Authorization: what you’re allowed to do. Implement both (JWT/session + roles/permissions/policies).

### 199. How would you approach designing a rate-limited public API?

**Answer:** API keys, Redis sliding window/token bucket per key, gateway enforcement, clear 429s, tiers/quotas, monitoring abuse, WAF for volumetric attacks.

### 200. Walk through debugging a 500 error in production.

**Answer:** Check error tracker (Sentry) for stack + request id → correlate logs/traces → identify recent deploys → reproduce in staging → fix with test → deploy hotfix → verify metrics/error rate drops → write postmortem if needed.

---

## Quick Study Tips (2 YOE)

- Be ready to **write code** on lists/dicts, SQL joins, and a small FastAPI/Django endpoint.
- Explain **tradeoffs** (sync vs async, SQL vs cache, ORM vs raw) more than buzzwords.
- Know **your stack deeply**: one framework, one DB, Redis, and how you deploy.
- Prepare **2–3 project stories**: bottleneck you fixed, bug you hunted, design choice you owned.

---

*Good luck with your interviews.*
