# 🐍 THE COMPLETE PYTHON DEVELOPER BIBLE
### From Zero to Interview-Ready — Every Concept, Real-World Code & Logic Building

---

> **How to use this guide:**
> Read top to bottom. Every section has: concept → real-world analogy → code → interview Q&A.
> After finishing, you'll have the knowledge, patterns, and logic-building skills to ace any Python interview.

---

## 📌 TABLE OF CONTENTS

1. [How to Build Logic in Programming](#logic-building)
2. [Python Basics & Syntax](#basics)
3. [Variables, Data Types & Type System](#data-types)
4. [Operators & Expressions](#operators)
5. [Control Flow (if/elif/else, loops)](#control-flow)
6. [Functions (Deep Dive)](#functions)
7. [Data Structures — Lists, Tuples, Sets, Dicts](#data-structures)
8. [Strings (Complete)](#strings)
9. [File Handling & I/O](#file-handling)
10. [Object-Oriented Programming (OOP)](#oop)
11. [Inheritance, Polymorphism, Abstraction, Encapsulation](#pillars)
12. [Decorators & Closures](#decorators)
13. [Generators & Iterators](#generators)
14. [Comprehensions](#comprehensions)
15. [Error & Exception Handling](#exceptions)
16. [Modules, Packages & Import System](#modules)
17. [Regular Expressions](#regex)
18. [Functional Programming (map, filter, lambda, functools)](#functional)
19. [Context Managers (with statement)](#context-managers)
20. [Multithreading & Multiprocessing](#concurrency)
21. [Async / Await (Asyncio)](#async)
22. [Database (SQLite + SQLAlchemy)](#database)
23. [REST APIs with Flask / FastAPI](#api)
24. [Testing (unittest + pytest)](#testing)
25. [Design Patterns in Python](#design-patterns)
26. [Data Structures & Algorithms (DSA) for Interviews](#dsa)
27. [Memory Management & Performance](#memory)
28. [Python Internals (GIL, bytecode, etc.)](#internals)
29. [Top 100 Interview Questions with Answers](#interview)
30. [Logic Building Exercises (Solved)](#exercises)

---

<a name="logic-building"></a>
## 🧠 CHAPTER 0: HOW TO BUILD LOGIC IN PROGRAMMING

This is the most important chapter. No one teaches this, but it's the root of everything.

### What is "Logic"?

Logic = **Breaking a big problem into small, ordered steps a computer can follow.**

Think of it like giving directions to someone who has never been to your city:
- You can't say "go to the mall." You say: turn left, go 2 km, turn right at the signal, etc.
- A computer is that person. It needs exact, unambiguous steps.

### The 5-Step Framework to Solve ANY Problem

```
1. UNDERSTAND   → What is the input? What is the expected output?
2. EXAMPLES     → Manually solve 2-3 examples on paper
3. PATTERN      → What rule/pattern did you use to solve it manually?
4. PSEUDOCODE   → Write the steps in plain English (not code)
5. CODE         → Translate pseudocode to Python
```

### Real Example: "Find the largest number in a list"

**Step 1 - Understand:**
- Input: `[3, 7, 2, 9, 1]`
- Output: `9`

**Step 2 - Example manually:**
- Look at first number: 3. It's the "current largest."
- See 7: 7 > 3, so new largest = 7
- See 2: 2 < 7, skip
- See 9: 9 > 7, new largest = 9
- See 1: 1 < 9, skip
- Answer: 9

**Step 3 - Pattern:**
- Keep track of the "current largest"
- For each number, if it's bigger than current largest, update it

**Step 4 - Pseudocode:**
```
SET largest = first element
FOR each number in list:
    IF number > largest:
        SET largest = number
RETURN largest
```

**Step 5 - Code:**
```python
def find_largest(numbers):
    largest = numbers[0]          # Start with first element
    for num in numbers:           # Go through each number
        if num > largest:         # If current is bigger
            largest = num         # Update our record
    return largest

print(find_largest([3, 7, 2, 9, 1]))  # Output: 9
```

### Logic Building Tips

| Habit | Why It Helps |
|-------|-------------|
| Solve on paper first | Forces you to understand before coding |
| Use print() everywhere | See what's happening at each step |
| Start with simplest case | What if list has 1 element? 0 elements? |
| Name variables clearly | `largest` not `x`, `count` not `c` |
| Draw diagrams | Trees, arrays, flow — draw it |
| Read others' code | See different thinking styles |
| Practice daily | 1 problem a day = 365 patterns a year |

### The "Rubber Duck" Method
When stuck, explain your code line-by-line to an imaginary rubber duck.
The moment you explain it, you often find the bug yourself.

---

<a name="basics"></a>
## 🐍 CHAPTER 1: PYTHON BASICS & SYNTAX

### Why Python?

```python
# Java to print Hello World:
# public class Hello {
#     public static void main(String[] args) {
#         System.out.println("Hello World");
#     }
# }

# Python:
print("Hello World")
```

Python is readable, fast to write, and has a massive ecosystem.

### Running Python

```bash
# Run a file
python script.py

# Interactive shell
python3

# Run one line
python -c "print('Hello')"
```

### Python Indentation (CRITICAL)

Python uses **indentation** (spaces/tabs) instead of `{}` to define code blocks.

```python
# CORRECT
if True:
    print("This is inside the if")   # 4 spaces indented
    print("So is this")
print("This is outside")             # Back to left

# WRONG - IndentationError
if True:
print("This will crash")             # Must be indented!
```

### Comments

```python
# This is a single-line comment

"""
This is a 
multi-line comment
(technically a string, but used as comment)
"""

x = 5  # Inline comment
```

### The `print()` Function

```python
print("Hello")                      # Hello
print("Hello", "World")             # Hello World
print("Hello", "World", sep="-")    # Hello-World
print("Hello", end=" ")             # No newline at end
print("World")                      # Hello World (same line)
print(f"I am {25} years old")       # f-string formatting
print("Score:", 95, "Grade:", "A")  # Multiple values
```

---

<a name="data-types"></a>
## 📦 CHAPTER 2: VARIABLES, DATA TYPES & TYPE SYSTEM

### Variables

A variable is a **named container** for data.

```python
# No need to declare type — Python infers it
name = "Alice"          # str
age = 25                # int
height = 5.6            # float
is_student = True       # bool
nothing = None          # NoneType

# Multiple assignment
x, y, z = 1, 2, 3
a = b = c = 0           # All three equal 0

# Swap (Python magic — no temp variable needed!)
x, y = y, x
```

### Python's Built-in Data Types

```python
# Numeric
i = 10          # int
f = 3.14        # float
c = 3 + 4j      # complex
b = 0b1010      # binary (10 in decimal)
h = 0xFF        # hexadecimal (255 in decimal)

# Text
s = "Hello"     # str

# Boolean
t = True
fa = False

# None
n = None        # represents "nothing" / null

# Collections (covered in depth later)
lst = [1, 2, 3]           # list — ordered, mutable
tup = (1, 2, 3)           # tuple — ordered, immutable
st  = {1, 2, 3}           # set — unordered, unique
dct = {"a": 1, "b": 2}    # dict — key-value pairs
```

### Type Checking & Conversion

```python
x = 42
print(type(x))            # <class 'int'>
print(isinstance(x, int)) # True
print(isinstance(x, (int, float)))  # True — checks multiple

# Type Conversion (Casting)
int("42")       # → 42
float("3.14")   # → 3.14
str(100)        # → "100"
bool(0)         # → False
bool(1)         # → True
bool("")        # → False
bool("hello")   # → True
list("abc")     # → ['a', 'b', 'c']
```

### Truthy and Falsy Values (VERY IMPORTANT for interviews)

```python
# Falsy values — evaluate to False in boolean context
False, 0, 0.0, 0j, "", [], (), {}, set(), None

# Everything else is Truthy

# Real use:
name = ""
if name:
    print("Name exists")
else:
    print("Name is empty")   # This runs

# Checking empty collection
items = []
if not items:
    print("Cart is empty!")
```

### Variable Naming Rules

```python
# Valid names
my_variable = 1
_private = 2
camelCase = 3    # Works but not Pythonic
ClassName = 4    # For classes
CONSTANT = 5     # Convention for constants

# Invalid — SyntaxError
2var = 1         # Can't start with digit
my-var = 1       # Hyphen not allowed
class = 1        # Reserved keyword

# Python keywords (cannot use as variable names)
# False, None, True, and, as, assert, async, await,
# break, class, continue, def, del, elif, else, except,
# finally, for, from, global, if, import, in, is,
# lambda, nonlocal, not, or, pass, raise, return,
# try, while, with, yield
```

### Integers — No Overflow in Python!

```python
# Python integers can be ARBITRARILY large
big = 10 ** 1000   # No overflow error!
print(big)

# Useful for factorial, fibonacci, cryptography
import math
print(math.factorial(100))  # Exact! No overflow
```

### Floats — Precision Issue

```python
# Classic floating point trap
print(0.1 + 0.2)          # 0.30000000000000004 !!!

# Fix: use Decimal for precise math
from decimal import Decimal
print(Decimal("0.1") + Decimal("0.2"))  # 0.3

# Or round
print(round(0.1 + 0.2, 2))  # 0.3
```

---

<a name="operators"></a>
## ⚙️ CHAPTER 3: OPERATORS & EXPRESSIONS

### Arithmetic Operators

```python
x, y = 10, 3

print(x + y)    # 13  — Addition
print(x - y)    # 7   — Subtraction
print(x * y)    # 30  — Multiplication
print(x / y)    # 3.333... — True Division (always float)
print(x // y)   # 3   — Floor Division (integer result)
print(x % y)    # 1   — Modulo (remainder)
print(x ** y)   # 1000 — Exponentiation
```

### Modulo — The Most Underused Operator

```python
# Check even/odd
num = 7
if num % 2 == 0:
    print("Even")
else:
    print("Odd")      # Prints "Odd"

# Cycling through indices
items = ["A", "B", "C"]
for i in range(9):
    print(items[i % 3])   # A B C A B C A B C

# Real-world: every 7th day is the same weekday
day_number = 10
days = ["Mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun"]
print(days[day_number % 7])  # "Tue"
```

### Comparison Operators

```python
x = 5
print(x == 5)   # True  — equal
print(x != 3)   # True  — not equal
print(x > 3)    # True  — greater than
print(x < 3)    # False — less than
print(x >= 5)   # True  — greater than or equal
print(x <= 4)   # False — less than or equal

# Chaining comparisons — Python exclusive!
age = 25
print(18 <= age <= 60)   # True — works like math!
# Equivalent to: age >= 18 and age <= 60
```

### Logical Operators

```python
x = True
y = False

print(x and y)   # False — both must be True
print(x or y)    # True  — at least one True
print(not x)     # False — flips

# Short-circuit evaluation (IMPORTANT!)
def risky():
    print("risky called!")
    return True

# 'and' stops at first False
False and risky()      # risky() NOT called — short circuited

# 'or' stops at first True
True or risky()        # risky() NOT called — short circuited

# Practical use: default values
name = ""
display_name = name or "Anonymous"   # "Anonymous"

config = {"timeout": 30}
timeout = config.get("retry") or 3   # 3 (default)
```

### Identity & Membership Operators

```python
# Identity — checks if same object in memory
a = [1, 2, 3]
b = [1, 2, 3]
c = a

print(a == b)    # True  — same value
print(a is b)    # False — different objects!
print(a is c)    # True  — same object

# None check (always use 'is', not '==')
x = None
if x is None:    # Correct way
    print("x is None")

# Membership — checks if value in sequence
print(3 in [1, 2, 3])       # True
print("ell" in "Hello")      # True
print(5 not in [1, 2, 3])    # True
```

### Assignment Operators

```python
x = 10
x += 5   # x = x + 5  → 15
x -= 3   # x = x - 3  → 12
x *= 2   # x = x * 2  → 24
x //= 5  # x = x // 5 → 4
x **= 3  # x = x ** 3 → 64
x %= 10  # x = x % 10 → 4

# Walrus Operator := (Python 3.8+) — assign and evaluate
# Real use: avoid calling function twice
import re
data = "age: 25"
if match := re.search(r"\d+", data):
    print(f"Found number: {match.group()}")  # 25
```

---

<a name="control-flow"></a>
## 🔀 CHAPTER 4: CONTROL FLOW

### if / elif / else

```python
# Scenario: Grade calculator
score = 85

if score >= 90:
    grade = "A"
elif score >= 80:
    grade = "B"
elif score >= 70:
    grade = "C"
elif score >= 60:
    grade = "D"
else:
    grade = "F"

print(f"Grade: {grade}")  # Grade: B
```

### Ternary (One-line if-else)

```python
# Syntax: value_if_true if condition else value_if_false
age = 20
status = "adult" if age >= 18 else "minor"
print(status)   # "adult"

# Real use: cap a value
price = 150
discounted = price * 0.9 if price > 100 else price
print(discounted)  # 135.0
```

### for Loop

```python
# Loop over list
fruits = ["apple", "banana", "cherry"]
for fruit in fruits:
    print(fruit)

# Loop with index — use enumerate()
for i, fruit in enumerate(fruits):
    print(f"{i}: {fruit}")
# 0: apple, 1: banana, 2: cherry

# Loop with enumerate starting at 1
for i, fruit in enumerate(fruits, start=1):
    print(f"{i}. {fruit}")
# 1. apple, 2. banana, 3. cherry

# range() — generates numbers
for i in range(5):        # 0 1 2 3 4
    print(i)

for i in range(1, 6):     # 1 2 3 4 5
    print(i)

for i in range(0, 10, 2): # 0 2 4 6 8 (step=2)
    print(i)

for i in range(10, 0, -1): # 10 9 8 ... 1 (countdown)
    print(i)
```

### while Loop

```python
# Real-world: ATM PIN retry
attempts = 0
correct_pin = "1234"

while attempts < 3:
    pin = input("Enter PIN: ")
    if pin == correct_pin:
        print("Access granted!")
        break
    else:
        attempts += 1
        print(f"Wrong PIN. {3 - attempts} attempts left.")
else:
    # 'else' on while runs when condition becomes False (not broken)
    print("Account locked!")
```

### break, continue, pass

```python
# break — exits the loop immediately
for i in range(10):
    if i == 5:
        break       # Stop at 5
    print(i)        # 0 1 2 3 4

# continue — skips current iteration
for i in range(10):
    if i % 2 == 0:
        continue    # Skip even numbers
    print(i)        # 1 3 5 7 9

# pass — does nothing (placeholder)
for i in range(5):
    pass            # Empty loop (no error)

def todo_function():
    pass            # To implement later
```

### for...else and while...else

```python
# 'else' runs ONLY if loop completed WITHOUT break
# Real use: searching

numbers = [1, 3, 5, 7, 9]
target = 6

for num in numbers:
    if num == target:
        print(f"Found {target}!")
        break
else:
    print(f"{target} not found in list")  # This runs

# Prime check using for...else
def is_prime(n):
    if n < 2:
        return False
    for i in range(2, int(n**0.5) + 1):
        if n % i == 0:
            return False      # Not prime, break implied
    else:
        return True           # Completed without finding divisor

print(is_prime(17))  # True
print(is_prime(18))  # False
```

### Nested Loops — Pattern Building (Logic Training)

```python
# Print multiplication table
for i in range(1, 6):
    for j in range(1, 6):
        print(f"{i*j:4}", end="")   # :4 = width 4
    print()   # newline after each row

# Triangle pattern
rows = 5
for i in range(1, rows + 1):
    print("* " * i)
# *
# * *
# * * *
# * * * *
# * * * * *

# Flattening logic: how 2D loops relate to position
matrix = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]
for row in matrix:
    for val in row:
        print(val, end=" ")
    print()
```

---

<a name="functions"></a>
## 🔧 CHAPTER 5: FUNCTIONS (DEEP DIVE)

### Why Functions?

> Functions are like recipes. You write once, use many times.

```python
# Without function (bad — duplicate code)
print(f"Employee: Alice, Salary: $5000")
print(f"Employee: Bob, Salary: $6000")
print(f"Employee: Charlie, Salary: $7000")

# With function (clean, reusable)
def display_employee(name, salary):
    print(f"Employee: {name}, Salary: ${salary}")

display_employee("Alice", 5000)
display_employee("Bob", 6000)
display_employee("Charlie", 7000)
```

### Function Anatomy

```python
def function_name(parameter1, parameter2):
    """Docstring: describes what function does."""
    # body of function
    result = parameter1 + parameter2
    return result

# Call it
output = function_name(3, 4)
print(output)   # 7
```

### Default Parameters

```python
def greet(name, greeting="Hello"):   # Default value
    return f"{greeting}, {name}!"

print(greet("Alice"))              # Hello, Alice!
print(greet("Bob", "Hi"))          # Hi, Bob!
print(greet("Eve", greeting="Hey")) # Hey, Eve!

# Real-world: connect to database
def connect_db(host="localhost", port=5432, timeout=30):
    print(f"Connecting to {host}:{port} (timeout={timeout}s)")

connect_db()                          # Use all defaults
connect_db("prod-server.com", 5433)  # Override some
```

### *args — Variable Positional Arguments

```python
# *args collects extra positional arguments into a tuple
def add_all(*numbers):
    total = 0
    for n in numbers:
        total += n
    return total

print(add_all(1, 2))          # 3
print(add_all(1, 2, 3, 4, 5)) # 15

# Real: logging function
def log(level, *messages):
    for msg in messages:
        print(f"[{level}] {msg}")

log("INFO", "Server started", "Listening on port 8080")
# [INFO] Server started
# [INFO] Listening on port 8080
```

### **kwargs — Variable Keyword Arguments

```python
# **kwargs collects extra keyword arguments into a dict
def print_info(**details):
    for key, value in details.items():
        print(f"{key}: {value}")

print_info(name="Alice", age=25, city="NYC")
# name: Alice
# age: 25
# city: NYC

# Real: flexible API request builder
def make_request(url, method="GET", **options):
    print(f"{method} {url}")
    for k, v in options.items():
        print(f"  {k}: {v}")

make_request(
    "https://api.example.com/users",
    method="POST",
    timeout=30,
    auth_token="abc123",
    retry=3
)
```

### Combining All Parameter Types

```python
# Order: regular, *args, keyword-only, **kwargs
def full_example(a, b, *args, keyword_only, **kwargs):
    print(f"a={a}, b={b}")
    print(f"args={args}")
    print(f"keyword_only={keyword_only}")
    print(f"kwargs={kwargs}")

full_example(1, 2, 3, 4, 5, keyword_only="hello", x=10, y=20)
# a=1, b=2
# args=(3, 4, 5)
# keyword_only=hello
# kwargs={'x': 10, 'y': 20}
```

### Return Values

```python
# Return multiple values (actually a tuple)
def min_max(numbers):
    return min(numbers), max(numbers)

low, high = min_max([3, 1, 4, 1, 5, 9, 2, 6])
print(low, high)   # 1 9

# Return None implicitly
def just_print(msg):
    print(msg)
    # No return — returns None

result = just_print("hi")  # prints "hi"
print(result)              # None
```

### Scope — LEGB Rule

```python
# L — Local: inside function
# E — Enclosing: outer function (closures)
# G — Global: module level
# B — Built-in: Python built-ins (print, len, etc.)

x = "global"

def outer():
    x = "enclosing"

    def inner():
        x = "local"
        print(x)   # local  (L wins)

    inner()
    print(x)       # enclosing (E, after inner() used L)

outer()
print(x)           # global  (G at module level)

# global keyword — modify global from inside function
count = 0
def increment():
    global count
    count += 1

increment()
increment()
print(count)  # 2

# nonlocal — modify enclosing scope variable
def make_counter():
    count = 0
    def increment():
        nonlocal count
        count += 1
        return count
    return increment

counter = make_counter()
print(counter())  # 1
print(counter())  # 2
print(counter())  # 3
```

### Lambda Functions (Anonymous Functions)

```python
# Syntax: lambda args: expression
square = lambda x: x ** 2
print(square(5))   # 25

add = lambda x, y: x + y
print(add(3, 4))   # 7

# Real use: as key for sorting
employees = [
    {"name": "Alice", "salary": 70000},
    {"name": "Bob", "salary": 85000},
    {"name": "Charlie", "salary": 60000},
]

# Sort by salary
sorted_emp = sorted(employees, key=lambda e: e["salary"])
for e in sorted_emp:
    print(e["name"], e["salary"])
# Charlie 60000, Alice 70000, Bob 85000

# Sort by name length
words = ["banana", "apple", "fig", "mango"]
print(sorted(words, key=lambda w: len(w)))
# ['fig', 'apple', 'mango', 'banana']
```

### Recursion

```python
# A function that calls itself
# Every recursive function needs:
# 1. Base case (stop condition)
# 2. Recursive case (smaller problem)

# Factorial
def factorial(n):
    if n <= 1:         # Base case
        return 1
    return n * factorial(n - 1)  # Recursive case

print(factorial(5))   # 120
# How it works:
# factorial(5) = 5 * factorial(4)
#                5 * 4 * factorial(3)
#                5 * 4 * 3 * factorial(2)
#                5 * 4 * 3 * 2 * factorial(1)
#                5 * 4 * 3 * 2 * 1 = 120

# Fibonacci
def fib(n):
    if n <= 1:
        return n
    return fib(n-1) + fib(n-2)

print([fib(i) for i in range(10)])  # [0, 1, 1, 2, 3, 5, 8, 13, 21, 34]

# Fibonacci with memoization (FAST)
from functools import lru_cache

@lru_cache(maxsize=None)
def fib_fast(n):
    if n <= 1:
        return n
    return fib_fast(n-1) + fib_fast(n-2)

print(fib_fast(100))  # Fast! Without cache this would take forever
```

---

<a name="data-structures"></a>
## 📚 CHAPTER 6: DATA STRUCTURES

### LIST — Ordered, Mutable

```python
# Creation
fruits = ["apple", "banana", "cherry"]
mixed = [1, "hello", True, 3.14, None]
nested = [[1, 2], [3, 4], [5, 6]]
empty = []
from_range = list(range(1, 6))  # [1, 2, 3, 4, 5]

# Access
print(fruits[0])    # apple (index from 0)
print(fruits[-1])   # cherry (negative = from end)
print(fruits[1:3])  # ['banana', 'cherry'] (slicing)
print(fruits[::-1]) # ['cherry', 'banana', 'apple'] (reversed)

# Modify
fruits[0] = "avocado"        # Change item
fruits.append("mango")       # Add to end
fruits.insert(1, "blueberry")# Insert at index
fruits.extend(["grape", "kiwi"]) # Add multiple
del fruits[0]                # Delete by index
fruits.remove("banana")      # Delete by value
popped = fruits.pop()        # Remove and return last
popped_idx = fruits.pop(1)   # Remove and return at index

# Search
print("cherry" in fruits)          # True
print(fruits.index("cherry"))      # Index of item
print(fruits.count("apple"))       # Count occurrences

# Sort
nums = [3, 1, 4, 1, 5, 9, 2]
nums.sort()                        # Sort in-place (modifies list)
nums.sort(reverse=True)            # Descending
sorted_nums = sorted(nums)         # Returns new list (original unchanged)

# Length, min, max, sum
print(len(fruits))
print(min(nums))
print(max(nums))
print(sum(nums))

# Copy (IMPORTANT — avoid reference trap)
original = [1, 2, 3]
wrong_copy = original           # Both point to SAME list!
right_copy = original.copy()    # or original[:]  or list(original)

wrong_copy.append(4)
print(original)   # [1, 2, 3, 4] — MODIFIED! Bug!

right_copy.append(4)
print(original)   # [1, 2, 3] — Safe
```

### Real-World List Example: Shopping Cart

```python
class ShoppingCart:
    def __init__(self):
        self.items = []

    def add_item(self, name, price, qty=1):
        self.items.append({"name": name, "price": price, "qty": qty})

    def remove_item(self, name):
        self.items = [i for i in self.items if i["name"] != name]

    def total(self):
        return sum(item["price"] * item["qty"] for item in self.items)

    def receipt(self):
        print("===== RECEIPT =====")
        for item in self.items:
            print(f"{item['name']}: ${item['price']} x {item['qty']}")
        print(f"TOTAL: ${self.total():.2f}")

cart = ShoppingCart()
cart.add_item("Apple", 1.5, 3)
cart.add_item("Milk", 2.99)
cart.add_item("Bread", 3.49, 2)
cart.receipt()
```

### TUPLE — Ordered, Immutable

```python
# Tuples can't be changed after creation — use for fixed data
point = (3, 4)
rgb = (255, 128, 0)
person = ("Alice", 25, "NYC")

# Unpack
x, y = point
name, age, city = person

# Single-element tuple (comma is REQUIRED)
single = (42,)      # Is a tuple
not_tuple = (42)    # Is just int 42!

# Why use tuples?
# 1. Faster than lists
# 2. Can be used as dict keys (lists cannot)
# 3. Signals "this data should not change"

# Coordinates stored as tuple keys
locations = {
    (40.7128, -74.0060): "New York",
    (51.5074, -0.1278): "London",
    (35.6762, 139.6503): "Tokyo",
}
print(locations[(40.7128, -74.0060)])  # New York

# Named tuple — like a lightweight class
from collections import namedtuple
Point = namedtuple("Point", ["x", "y"])
p = Point(3, 4)
print(p.x, p.y)     # 3 4
print(p)            # Point(x=3, y=4)
```

### SET — Unordered, Unique Elements

```python
# Auto-removes duplicates
s = {1, 2, 2, 3, 3, 3}
print(s)   # {1, 2, 3}

# Create from list (deduplication trick!)
names = ["Alice", "Bob", "Alice", "Charlie", "Bob"]
unique = list(set(names))
print(unique)   # ['Alice', 'Bob', 'Charlie'] (order may vary)

# Operations
a = {1, 2, 3, 4}
b = {3, 4, 5, 6}

print(a | b)    # {1,2,3,4,5,6} — Union (all elements)
print(a & b)    # {3,4}         — Intersection (common)
print(a - b)    # {1,2}         — Difference (in a, not b)
print(a ^ b)    # {1,2,5,6}     — Symmetric diff (not in both)

# Add/Remove
a.add(5)
a.remove(1)          # Raises KeyError if not found
a.discard(99)        # Safe — no error if not found

# Real use: find common users between two platforms
twitter_users = {"alice", "bob", "charlie", "diana"}
instagram_users = {"bob", "diana", "eve", "frank"}

both_platforms = twitter_users & instagram_users
only_twitter = twitter_users - instagram_users
print("On both:", both_platforms)    # {'bob', 'diana'}
print("Only Twitter:", only_twitter) # {'alice', 'charlie'}
```

### DICTIONARY — Key-Value Store

```python
# Create
person = {"name": "Alice", "age": 25, "city": "NYC"}
empty = {}
from_keys = dict.fromkeys(["a", "b", "c"], 0)  # {'a':0,'b':0,'c':0}

# Access
print(person["name"])             # Alice
print(person.get("age"))          # 25
print(person.get("salary", 0))    # 0 (default if key missing)

# Modify
person["email"] = "alice@example.com"  # Add
person["age"] = 26                      # Update
del person["city"]                      # Delete
person.pop("email")                     # Remove and return

# Iterate
for key in person:
    print(key)

for value in person.values():
    print(value)

for key, value in person.items():
    print(f"{key}: {value}")

# Check existence
print("name" in person)         # True
print("salary" in person)       # False

# Merge dicts (Python 3.9+)
defaults = {"timeout": 30, "retry": 3}
custom = {"timeout": 60, "debug": True}
merged = defaults | custom    # {'timeout': 60, 'retry': 3, 'debug': True}

# Nested dict — common in APIs / JSON
employee = {
    "id": 101,
    "name": "Bob",
    "address": {
        "street": "123 Main St",
        "city": "Boston",
        "zip": "02101"
    },
    "skills": ["Python", "SQL", "Docker"]
}

print(employee["address"]["city"])   # Boston
print(employee["skills"][0])         # Python
```

### Real-World Dict Example: Word Frequency Counter

```python
def word_frequency(text):
    words = text.lower().split()
    freq = {}
    for word in words:
        # Clean punctuation
        word = word.strip(".,!?;:")
        freq[word] = freq.get(word, 0) + 1
    return freq

text = "the quick brown fox jumps over the lazy dog the fox"
freq = word_frequency(text)

# Sort by frequency
sorted_freq = sorted(freq.items(), key=lambda x: x[1], reverse=True)
for word, count in sorted_freq[:5]:
    print(f"'{word}': {count}")
# 'the': 3
# 'fox': 2
# ...

# Using Counter (simpler!)
from collections import Counter
counter = Counter(text.split())
print(counter.most_common(3))
```

### collections Module — Advanced Data Structures

```python
from collections import defaultdict, OrderedDict, Counter, deque

# defaultdict — auto-creates missing keys
dd = defaultdict(list)
dd["fruits"].append("apple")
dd["fruits"].append("banana")
dd["veggies"].append("carrot")
print(dict(dd))  # {'fruits': ['apple', 'banana'], 'veggies': ['carrot']}

# Group words by first letter
words = ["apple", "ant", "banana", "bat", "cherry"]
grouped = defaultdict(list)
for word in words:
    grouped[word[0]].append(word)
print(dict(grouped))
# {'a': ['apple', 'ant'], 'b': ['banana', 'bat'], 'c': ['cherry']}

# Counter — count occurrences
votes = ["Alice", "Bob", "Alice", "Charlie", "Bob", "Alice"]
result = Counter(votes)
print(result)                    # Counter({'Alice': 3, 'Bob': 2, 'Charlie': 1})
print(result.most_common(1))     # [('Alice', 3)]

# deque — double-ended queue (O(1) append/pop from both ends)
dq = deque([1, 2, 3])
dq.appendleft(0)   # [0, 1, 2, 3]
dq.append(4)       # [0, 1, 2, 3, 4]
dq.popleft()       # removes 0
dq.pop()           # removes 4
print(list(dq))    # [1, 2, 3]

# Sliding window with deque
def sliding_window_max(arr, k):
    dq = deque()
    result = []
    for i, val in enumerate(arr):
        while dq and arr[dq[-1]] <= val:
            dq.pop()
        dq.append(i)
        if dq[0] == i - k:
            dq.popleft()
        if i >= k - 1:
            result.append(arr[dq[0]])
    return result

print(sliding_window_max([1,3,-1,-3,5,3,6,7], 3))
# [3, 3, 5, 5, 6, 7]
```

---

<a name="strings"></a>
## 📝 CHAPTER 7: STRINGS

### String Basics

```python
# Strings are immutable sequences of characters
s = "Hello, World!"

# Length
print(len(s))          # 13

# Access (indexing)
print(s[0])            # H
print(s[-1])           # !
print(s[7:12])         # World
print(s[::2])          # Hlo ol!
print(s[::-1])         # !dlroW ,olleH  (reversed)

# Multiline
multi = """This is
a multiline
string"""

# Raw string (backslashes not treated as escape)
path = r"C:\Users\alice\Documents"   # r prefix
print(path)   # C:\Users\alice\Documents
```

### String Methods (The Complete Toolkit)

```python
s = "  Hello, World!  "

# Case
print(s.upper())            # "  HELLO, WORLD!  "
print(s.lower())            # "  hello, world!  "
print(s.title())            # "  Hello, World!  "
print(s.swapcase())         # "  hELLO, wORLD!  "
print(s.capitalize())       # "  hello, world!  "

# Strip whitespace
print(s.strip())            # "Hello, World!"
print(s.lstrip())           # "Hello, World!  "
print(s.rstrip())           # "  Hello, World!"

# Search
s2 = "Hello, World!"
print(s2.find("World"))     # 7  (index, or -1)
print(s2.index("World"))    # 7  (raises ValueError if not found)
print(s2.count("l"))        # 3
print(s2.startswith("Hello")) # True
print(s2.endswith("!"))       # True

# Replace
print(s2.replace("World", "Python"))  # "Hello, Python!"
print(s2.replace("l", "L", 2))        # "HeLLo, World!" (max 2)

# Split and Join
csv = "alice,bob,charlie,diana"
names = csv.split(",")               # ['alice', 'bob', 'charlie', 'diana']
print(" | ".join(names))             # alice | bob | charlie | diana

sentence = "  too   many   spaces  "
clean = " ".join(sentence.split())   # "too many spaces"

# Check content
print("hello123".isalnum())  # True  (letters + digits)
print("hello".isalpha())     # True  (only letters)
print("12345".isdigit())     # True  (only digits)
print("  ".isspace())        # True  (only whitespace)
```

### String Formatting

```python
name = "Alice"
age = 25
score = 98.567

# f-strings (RECOMMENDED — Python 3.6+)
print(f"Name: {name}, Age: {age}")
print(f"Score: {score:.2f}")         # 2 decimal places
print(f"Score: {score:08.2f}")       # Width 8, zero-padded
print(f"Price: ${1234567:,}")        # 1,234,567 (thousands separator)
print(f"{name!r}")                   # 'Alice' (repr)
print(f"{name!u}")                   # Only in Python3.12+
print(f"{age:>10}")                  # Right-align in width 10
print(f"{age:<10}")                  # Left-align
print(f"{age:^10}")                  # Center

# .format()
print("Name: {}, Age: {}".format(name, age))
print("Name: {name}, Age: {age}".format(name=name, age=age))

# % formatting (old style)
print("Name: %s, Age: %d" % (name, age))
```

### String as Sequence — Useful Tricks

```python
# Check palindrome
def is_palindrome(s):
    s = s.lower().replace(" ", "")
    return s == s[::-1]

print(is_palindrome("racecar"))    # True
print(is_palindrome("A man a plan a canal Panama"))  # True

# Count vowels
def count_vowels(s):
    return sum(1 for c in s.lower() if c in "aeiou")

print(count_vowels("Hello World"))  # 3

# Anagram check
def is_anagram(s1, s2):
    return sorted(s1.lower()) == sorted(s2.lower())

print(is_anagram("listen", "silent"))  # True
print(is_anagram("hello", "world"))    # False

# Using Counter for anagram
from collections import Counter
def is_anagram_v2(s1, s2):
    return Counter(s1.lower()) == Counter(s2.lower())
```

---

<a name="file-handling"></a>
## 📁 CHAPTER 8: FILE HANDLING & I/O

### Reading Files

```python
# ALWAYS use 'with' — auto-closes file even on error
with open("data.txt", "r") as f:
    content = f.read()          # Read entire file as string

with open("data.txt", "r") as f:
    lines = f.readlines()       # Read all lines as list

with open("data.txt", "r") as f:
    for line in f:              # Memory-efficient: one line at a time
        print(line.strip())     # strip() removes \n

# Read with encoding
with open("data.txt", "r", encoding="utf-8") as f:
    content = f.read()
```

### Writing Files

```python
# Write (overwrites if exists)
with open("output.txt", "w") as f:
    f.write("Hello, World!\n")
    f.write("Second line\n")

# Append (adds to existing)
with open("log.txt", "a") as f:
    f.write("New log entry\n")

# Write multiple lines
lines = ["Line 1", "Line 2", "Line 3"]
with open("output.txt", "w") as f:
    f.writelines(line + "\n" for line in lines)
```

### CSV Files

```python
import csv

# Write CSV
data = [
    ["Name", "Age", "City"],
    ["Alice", 25, "NYC"],
    ["Bob", 30, "LA"],
    ["Charlie", 35, "Chicago"]
]

with open("people.csv", "w", newline="") as f:
    writer = csv.writer(f)
    writer.writerows(data)

# Read CSV
with open("people.csv", "r") as f:
    reader = csv.DictReader(f)  # Each row is a dict
    for row in reader:
        print(f"{row['Name']} lives in {row['City']}")

# Real-world: process sales report
def process_sales(filename):
    total = 0
    with open(filename, "r") as f:
        reader = csv.DictReader(f)
        for row in reader:
            total += float(row["amount"])
    return total
```

### JSON Files

```python
import json

# Write JSON
config = {
    "database": {
        "host": "localhost",
        "port": 5432,
        "name": "mydb"
    },
    "debug": True,
    "allowed_hosts": ["localhost", "127.0.0.1"]
}

with open("config.json", "w") as f:
    json.dump(config, f, indent=4)

# Read JSON
with open("config.json", "r") as f:
    loaded = json.load(f)
    print(loaded["database"]["host"])  # localhost

# Convert between JSON string and dict
json_str = '{"name": "Alice", "age": 25}'
data = json.loads(json_str)       # str → dict
back_to_str = json.dumps(data)    # dict → str
```

### os and pathlib — File System Operations

```python
import os
from pathlib import Path

# os module
print(os.getcwd())              # Current directory
os.makedirs("new/folder", exist_ok=True)
os.listdir(".")                 # List files in dir
os.path.exists("file.txt")      # Check if exists
os.path.join("folder", "file.txt")  # Safe path joining

# pathlib (modern, OOP approach)
p = Path("documents/report.txt")
print(p.name)           # report.txt
print(p.stem)           # report
print(p.suffix)         # .txt
print(p.parent)         # documents

# Create directories
Path("new/folder").mkdir(parents=True, exist_ok=True)

# Find all Python files
for py_file in Path(".").rglob("*.py"):
    print(py_file)

# Read file with pathlib
content = Path("data.txt").read_text(encoding="utf-8")
Path("output.txt").write_text("Hello!", encoding="utf-8")
```

---

<a name="oop"></a>
## 🏗️ CHAPTER 9: OBJECT-ORIENTED PROGRAMMING

### Why OOP?

> Real-world has objects (car, person, bank account).
> OOP lets us model these naturally in code.

```
Without OOP:             With OOP:
name1 = "Alice"          alice = Person("Alice", 25)
age1 = 25               alice.greet()
salary1 = 50000          
name2 = "Bob"            
age2 = 30               bob = Person("Bob", 30)
salary2 = 60000          bob.greet()

# OOP is cleaner, easier to manage, and scales better
```

### Class Basics

```python
class Person:
    # Class attribute (shared by all instances)
    species = "Homo sapiens"
    count = 0

    # __init__ is the constructor — called when creating object
    def __init__(self, name, age):
        # Instance attributes (unique to each object)
        self.name = name
        self.age = age
        Person.count += 1   # Track total persons created

    # Instance method
    def greet(self):
        return f"Hi, I'm {self.name} and I'm {self.age} years old."

    # String representation
    def __str__(self):
        return f"Person(name={self.name}, age={self.age})"

    def __repr__(self):
        return f"Person('{self.name}', {self.age})"

# Create instances
alice = Person("Alice", 25)
bob = Person("Bob", 30)

print(alice.greet())       # Hi, I'm Alice and I'm 25 years old.
print(alice)               # Person(name=Alice, age=25)
print(Person.count)        # 2
print(alice.species)       # Homo sapiens (class attribute)
```

### Real-World OOP: Bank Account

```python
class BankAccount:
    def __init__(self, owner, initial_balance=0):
        self.owner = owner
        self._balance = initial_balance    # _ prefix = "private" convention
        self._transactions = []

    def deposit(self, amount):
        if amount <= 0:
            raise ValueError("Deposit must be positive")
        self._balance += amount
        self._transactions.append(("deposit", amount))
        return self._balance

    def withdraw(self, amount):
        if amount <= 0:
            raise ValueError("Withdrawal must be positive")
        if amount > self._balance:
            raise ValueError("Insufficient funds")
        self._balance -= amount
        self._transactions.append(("withdrawal", amount))
        return self._balance

    @property
    def balance(self):      # Getter — access as attribute
        return self._balance

    def statement(self):
        print(f"Account: {self.owner}")
        print(f"Balance: ${self._balance:,.2f}")
        print("Transactions:")
        for t_type, amount in self._transactions:
            print(f"  {t_type}: ${amount:,.2f}")

acc = BankAccount("Alice", 1000)
acc.deposit(500)
acc.withdraw(200)
print(acc.balance)   # 1300
acc.statement()
```

### Special (Dunder) Methods

```python
class Vector:
    def __init__(self, x, y):
        self.x = x
        self.y = y

    def __str__(self):          # str(obj) and print(obj)
        return f"Vector({self.x}, {self.y})"

    def __repr__(self):         # Developer representation
        return f"Vector({self.x!r}, {self.y!r})"

    def __add__(self, other):   # v1 + v2
        return Vector(self.x + other.x, self.y + other.y)

    def __sub__(self, other):   # v1 - v2
        return Vector(self.x - other.x, self.y - other.y)

    def __mul__(self, scalar):  # v * 3
        return Vector(self.x * scalar, self.y * scalar)

    def __len__(self):          # len(v)
        return int((self.x**2 + self.y**2) ** 0.5)

    def __eq__(self, other):    # v1 == v2
        return self.x == other.x and self.y == other.y

    def __lt__(self, other):    # v1 < v2
        return abs(self) < abs(other)

v1 = Vector(1, 2)
v2 = Vector(3, 4)
print(v1 + v2)          # Vector(4, 6)
print(v1 * 3)           # Vector(3, 6)
print(v1 == v2)         # False
```

### Class Methods and Static Methods

```python
class Employee:
    company = "TechCorp"
    _count = 0

    def __init__(self, name, department):
        self.name = name
        self.department = department
        Employee._count += 1

    @classmethod
    def get_count(cls):     # cls = class itself
        return cls._count

    @classmethod
    def from_string(cls, emp_string):  # Alternative constructor
        name, dept = emp_string.split("-")
        return cls(name, dept)         # Creates new Employee

    @staticmethod
    def validate_name(name):  # No self or cls — utility function
        return bool(name and name.isalpha())

e1 = Employee("Alice", "Engineering")
e2 = Employee.from_string("Bob-Marketing")

print(Employee.get_count())          # 2
print(Employee.validate_name("Alice"))  # True
print(Employee.validate_name("123"))    # False
```

### Properties (@property)

```python
class Temperature:
    def __init__(self, celsius):
        self._celsius = celsius    # Private storage

    @property
    def celsius(self):             # Getter
        return self._celsius

    @celsius.setter
    def celsius(self, value):      # Setter with validation
        if value < -273.15:
            raise ValueError("Temperature below absolute zero!")
        self._celsius = value

    @property
    def fahrenheit(self):          # Computed property
        return self._celsius * 9/5 + 32

    @property
    def kelvin(self):
        return self._celsius + 273.15

t = Temperature(100)
print(t.celsius)       # 100
print(t.fahrenheit)    # 212.0
print(t.kelvin)        # 373.15

t.celsius = 25         # Uses setter (validates!)
# t.celsius = -300     # Raises ValueError
```

---

<a name="pillars"></a>
## 🏛️ CHAPTER 10: FOUR PILLARS OF OOP

### 1. Encapsulation — Hide internal details

```python
class CreditCard:
    def __init__(self, number, cvv, holder):
        self.holder = holder
        self.__number = number    # __ = name mangling (strong private)
        self.__cvv = cvv

    def charge(self, amount):
        print(f"Charging ${amount} to card ending in {self.__number[-4:]}")

    def __str__(self):
        return f"Card of {self.holder} ending in {self.__number[-4:]}"

card = CreditCard("4111111111111234", "123", "Alice")
print(card)                        # Card of Alice ending in 1234
card.charge(50)                    # Charging $50 to card ending in 1234
# print(card.__number)             # AttributeError — can't access!
# Internal: card._CreditCard__number  (Python's name mangling)
```

### 2. Inheritance — Reuse parent class

```python
# Base class (Parent)
class Animal:
    def __init__(self, name, species):
        self.name = name
        self.species = species

    def breathe(self):
        return f"{self.name} breathes air."

    def speak(self):
        return "..."   # Default

    def __str__(self):
        return f"{self.name} ({self.species})"

# Derived class (Child)
class Dog(Animal):
    def __init__(self, name, breed):
        super().__init__(name, "Canis lupus familiaris")  # Call parent __init__
        self.breed = breed

    def speak(self):
        return "Woof!"

    def fetch(self):
        return f"{self.name} fetches the ball!"

class Cat(Animal):
    def speak(self):
        return "Meow!"

    def purr(self):
        return f"{self.name} purrs..."

dog = Dog("Rex", "German Shepherd")
cat = Cat("Whiskers", "Felis catus")

print(dog.speak())     # Woof!  — overridden
print(dog.breathe())   # Rex breathes air. — inherited
print(dog.fetch())     # Rex fetches the ball! — new
print(cat.speak())     # Meow!

# isinstance / issubclass
print(isinstance(dog, Dog))     # True
print(isinstance(dog, Animal))  # True — Dog is Animal!
print(issubclass(Dog, Animal))  # True
```

### Multiple Inheritance & MRO

```python
class Flyable:
    def fly(self):
        return "I can fly!"

class Swimmable:
    def swim(self):
        return "I can swim!"

class Duck(Animal, Flyable, Swimmable):
    def speak(self):
        return "Quack!"

donald = Duck("Donald", "Duck")
print(donald.fly())    # I can fly!
print(donald.swim())   # I can swim!
print(donald.speak())  # Quack!

# MRO — Method Resolution Order
print(Duck.__mro__)
# (<class 'Duck'>, <class 'Animal'>, <class 'Flyable'>, <class 'Swimmable'>, <class 'object'>)
```

### 3. Polymorphism — Same interface, different behavior

```python
# Same method name, different behavior per class
class Shape:
    def area(self):
        raise NotImplementedError("Subclass must implement area()")

class Circle(Shape):
    def __init__(self, radius):
        self.radius = radius

    def area(self):
        return 3.14159 * self.radius ** 2

class Rectangle(Shape):
    def __init__(self, width, height):
        self.width = width
        self.height = height

    def area(self):
        return self.width * self.height

class Triangle(Shape):
    def __init__(self, base, height):
        self.base = base
        self.height = height

    def area(self):
        return 0.5 * self.base * self.height

# Polymorphic usage — treat all shapes the same
shapes = [Circle(5), Rectangle(4, 6), Triangle(3, 8)]

for shape in shapes:
    print(f"{shape.__class__.__name__}: area = {shape.area():.2f}")
# Circle: area = 78.54
# Rectangle: area = 24.00
# Triangle: area = 12.00

# Total area — doesn't matter what shape it is!
total = sum(s.area() for s in shapes)
print(f"Total: {total:.2f}")
```

### 4. Abstraction — Abstract Base Classes (ABC)

```python
from abc import ABC, abstractmethod

class Vehicle(ABC):
    def __init__(self, brand, model):
        self.brand = brand
        self.model = model

    @abstractmethod
    def start_engine(self):    # MUST be implemented by subclasses
        pass

    @abstractmethod
    def stop_engine(self):
        pass

    def info(self):            # Concrete method (optional override)
        return f"{self.brand} {self.model}"

class Car(Vehicle):
    def start_engine(self):
        return "Car engine: Vroom vroom!"

    def stop_engine(self):
        return "Car engine stopped."

class ElectricCar(Vehicle):
    def start_engine(self):
        return "Electric motor: Whirrrr..."

    def stop_engine(self):
        return "Electric motor stopped silently."

# v = Vehicle("X", "Y")  # TypeError — can't instantiate abstract class!

tesla = ElectricCar("Tesla", "Model 3")
print(tesla.start_engine())  # Electric motor: Whirrrr...
print(tesla.info())          # Tesla Model 3
```

---

<a name="decorators"></a>
## 🎨 CHAPTER 11: DECORATORS & CLOSURES

### Closures

```python
# A function that "remembers" the enclosing scope

def make_multiplier(n):
    def multiplier(x):     # Inner function
        return x * n       # Remembers 'n' even after make_multiplier returns
    return multiplier      # Return the function itself

double = make_multiplier(2)
triple = make_multiplier(3)

print(double(5))    # 10
print(triple(5))    # 15

# Why useful? Creating specialized functions from general ones
def make_power(exp):
    return lambda x: x ** exp

square = make_power(2)
cube = make_power(3)
print(square(4))   # 16
print(cube(3))     # 27
```

### Decorators

```python
# A decorator is a function that wraps another function
# Syntax: @decorator_name above function definition

def my_decorator(func):
    def wrapper(*args, **kwargs):
        print("Before function")
        result = func(*args, **kwargs)
        print("After function")
        return result
    return wrapper

@my_decorator
def say_hello(name):
    print(f"Hello, {name}!")

say_hello("Alice")
# Before function
# Hello, Alice!
# After function
```

### Real-World Decorators

```python
import time
import functools

# 1. Timer decorator
def timer(func):
    @functools.wraps(func)  # Preserves function metadata
    def wrapper(*args, **kwargs):
        start = time.perf_counter()
        result = func(*args, **kwargs)
        end = time.perf_counter()
        print(f"{func.__name__} took {end - start:.4f}s")
        return result
    return wrapper

@timer
def slow_function():
    time.sleep(0.1)
    return "done"

slow_function()  # slow_function took 0.1001s

# 2. Login required decorator
def login_required(func):
    @functools.wraps(func)
    def wrapper(user, *args, **kwargs):
        if not user.get("is_logged_in"):
            raise PermissionError("You must be logged in!")
        return func(user, *args, **kwargs)
    return wrapper

@login_required
def view_profile(user):
    print(f"Profile: {user['name']}")

user = {"name": "Alice", "is_logged_in": True}
view_profile(user)   # Profile: Alice

# 3. Retry decorator
def retry(max_attempts=3, delay=1):
    def decorator(func):
        @functools.wraps(func)
        def wrapper(*args, **kwargs):
            for attempt in range(max_attempts):
                try:
                    return func(*args, **kwargs)
                except Exception as e:
                    if attempt == max_attempts - 1:
                        raise
                    print(f"Attempt {attempt+1} failed: {e}. Retrying...")
                    time.sleep(delay)
        return wrapper
    return decorator

@retry(max_attempts=3, delay=0.5)
def unreliable_api_call():
    import random
    if random.random() < 0.7:    # 70% chance of failure
        raise ConnectionError("API unavailable")
    return "Success!"

# 4. Cache decorator (manual memoization)
def memoize(func):
    cache = {}
    @functools.wraps(func)
    def wrapper(*args):
        if args not in cache:
            cache[args] = func(*args)
        return cache[args]
    return wrapper

@memoize
def expensive_calc(n):
    print(f"Computing {n}...")
    return n * n * n

print(expensive_calc(5))   # Computing 5... → 125
print(expensive_calc(5))   # 125 (from cache, no "Computing")
print(expensive_calc(10))  # Computing 10... → 1000
```

### Stacking Decorators

```python
@timer
@login_required
def dashboard(user):
    return f"Dashboard for {user['name']}"

# Equivalent to:
# dashboard = timer(login_required(dashboard))
```

---

<a name="generators"></a>
## ⚡ CHAPTER 12: GENERATORS & ITERATORS

### Iterators

```python
# An iterator is an object with __iter__ and __next__ methods
class CountDown:
    def __init__(self, start):
        self.current = start

    def __iter__(self):
        return self

    def __next__(self):
        if self.current <= 0:
            raise StopIteration
        self.current -= 1
        return self.current + 1

for n in CountDown(5):
    print(n)    # 5 4 3 2 1
```

### Generators — Easy Iterators

```python
# Generator function uses 'yield' instead of 'return'
# Pauses at yield, resumes on next()
# LAZY — values computed on demand, not all at once

def countdown(n):
    while n > 0:
        yield n        # Pause here, return n
        n -= 1         # Resume from here

gen = countdown(5)
print(next(gen))    # 5
print(next(gen))    # 4
print(list(gen))    # [3, 2, 1]

# Memory-efficient: generate 1 million numbers without storing all
def huge_range(n):
    i = 0
    while i < n:
        yield i
        i += 1

# Only one number in memory at a time!
total = sum(huge_range(1_000_000))   # Works fine
# list(range(1_000_000))             # Uses lots of memory

# Real-world: reading large log files
def read_logs(filename):
    with open(filename) as f:
        for line in f:
            if "ERROR" in line:
                yield line.strip()

# for error in read_logs("server.log"):
#     print(error)    # Processes one line at a time

# Generator with send() — coroutine-like
def running_average():
    total = 0
    count = 0
    while True:
        value = yield total / count if count > 0 else 0
        if value is None:
            break
        total += value
        count += 1

gen = running_average()
next(gen)              # Prime the generator
print(gen.send(10))    # 10.0
print(gen.send(20))    # 15.0
print(gen.send(30))    # 20.0
```

### Generator Expressions

```python
# Like list comprehension but lazy
squares_list = [x**2 for x in range(10)]    # List — all in memory
squares_gen  = (x**2 for x in range(10))    # Generator — lazy

# Efficient chaining
data = range(1_000_000)
result = sum(x**2 for x in data if x % 2 == 0)  # Memory-efficient pipeline
```

---

<a name="comprehensions"></a>
## 📋 CHAPTER 13: COMPREHENSIONS

### List Comprehension

```python
# Syntax: [expression for item in iterable if condition]

# Basic
squares = [x**2 for x in range(10)]
# [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]

# With condition
evens = [x for x in range(20) if x % 2 == 0]
# [0, 2, 4, 6, 8, 10, 12, 14, 16, 18]

# Transform strings
names = ["alice", "BOB", "Charlie"]
normalized = [n.title() for n in names]
# ['Alice', 'Bob', 'Charlie']

# Nested
matrix = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
flat = [val for row in matrix for val in row]
# [1, 2, 3, 4, 5, 6, 7, 8, 9]

# Conditional expression
result = ["even" if x % 2 == 0 else "odd" for x in range(6)]
# ['even', 'odd', 'even', 'odd', 'even', 'odd']

# Real: filter and transform in one line
employees = [
    {"name": "Alice", "salary": 70000, "dept": "Eng"},
    {"name": "Bob", "salary": 50000, "dept": "Sales"},
    {"name": "Charlie", "salary": 90000, "dept": "Eng"},
]
# Get names of engineers with salary > 60000
senior_eng = [e["name"] for e in employees
              if e["dept"] == "Eng" and e["salary"] > 60000]
# ['Alice', 'Charlie']
```

### Dict Comprehension

```python
# {key: value for item in iterable}
squares = {x: x**2 for x in range(6)}
# {0: 0, 1: 1, 2: 4, 3: 9, 4: 16, 5: 25}

# Invert dict
original = {"a": 1, "b": 2, "c": 3}
inverted = {v: k for k, v in original.items()}
# {1: 'a', 2: 'b', 3: 'c'}

# Filter dict
scores = {"Alice": 85, "Bob": 42, "Charlie": 91, "Diana": 60}
passed = {name: score for name, score in scores.items() if score >= 60}
# {'Alice': 85, 'Charlie': 91, 'Diana': 60}
```

### Set Comprehension

```python
unique_squares = {x**2 for x in range(-5, 6)}
# {0, 1, 4, 9, 16, 25}

text = "Hello World"
unique_chars = {c.lower() for c in text if c.isalpha()}
# {'h', 'e', 'l', 'o', 'w', 'r', 'd'}
```

---

<a name="exceptions"></a>
## ⚠️ CHAPTER 14: EXCEPTION HANDLING

### Basic try/except

```python
# Without exception handling — program crashes!
# result = 10 / 0   # ZeroDivisionError: division by zero

# With exception handling — graceful error management
try:
    result = 10 / 0
except ZeroDivisionError:
    print("Cannot divide by zero!")
    result = 0

print(result)  # 0
```

### Full Exception Hierarchy

```python
try:
    # Risky code here
    number = int("abc")       # ValueError
    result = 10 / 0           # ZeroDivisionError
    lst = [1, 2]
    lst[10]                   # IndexError

except ValueError as e:
    print(f"Value error: {e}")

except ZeroDivisionError:
    print("Division by zero!")

except (IndexError, KeyError) as e:    # Multiple exception types
    print(f"Access error: {e}")

except Exception as e:      # Catches ANY exception (use sparingly)
    print(f"Unexpected error: {type(e).__name__}: {e}")

else:
    # Runs ONLY if NO exception occurred
    print("All good!")

finally:
    # ALWAYS runs — cleanup code here
    print("This always runs (cleanup)")
```

### Real-World Exception Handling

```python
import json
import requests  # for HTTP

# Layered exception handling
def fetch_user_data(user_id):
    """Fetch user from database with proper error handling."""
    if not isinstance(user_id, int) or user_id <= 0:
        raise ValueError(f"Invalid user_id: {user_id}")

    # Simulate database lookup
    users = {1: {"name": "Alice"}, 2: {"name": "Bob"}}

    user = users.get(user_id)
    if user is None:
        raise KeyError(f"User {user_id} not found")

    return user

# Using the function safely
for uid in [1, 3, -1, "abc"]:
    try:
        user = fetch_user_data(uid)
        print(f"Found user: {user['name']}")
    except ValueError as e:
        print(f"Invalid input: {e}")
    except KeyError as e:
        print(f"Not found: {e}")
```

### Custom Exceptions

```python
# Create your own exception hierarchy
class AppError(Exception):
    """Base exception for our app."""
    pass

class DatabaseError(AppError):
    """Raised when database operation fails."""
    def __init__(self, message, query=None):
        super().__init__(message)
        self.query = query

class AuthenticationError(AppError):
    """Raised when authentication fails."""
    pass

class InsufficientFundsError(AppError):
    """Raised when account has insufficient funds."""
    def __init__(self, amount, balance):
        self.amount = amount
        self.balance = balance
        super().__init__(
            f"Cannot withdraw ${amount}. Balance is ${balance}."
        )

# Using custom exceptions
def withdraw(amount, balance):
    if amount > balance:
        raise InsufficientFundsError(amount, balance)
    return balance - amount

try:
    new_balance = withdraw(500, 200)
except InsufficientFundsError as e:
    print(e)                    # Cannot withdraw $500. Balance is $200.
    print(f"Needed: ${e.amount - e.balance} more")
```

### Context Manager with Exception

```python
# with statement guarantees cleanup even on exception
class ManagedFile:
    def __init__(self, filename, mode):
        self.filename = filename
        self.mode = mode

    def __enter__(self):
        self.file = open(self.filename, self.mode)
        return self.file

    def __exit__(self, exc_type, exc_val, exc_tb):
        self.file.close()
        if exc_type:
            print(f"Exception occurred: {exc_val}")
        return False   # Don't suppress the exception

with ManagedFile("test.txt", "w") as f:
    f.write("Hello!")
# File automatically closed, even if error occurs
```

---

<a name="modules"></a>
## 📦 CHAPTER 15: MODULES, PACKAGES & IMPORT SYSTEM

### Modules

```python
# A module is any .py file
# math_utils.py:
def add(a, b): return a + b
def multiply(a, b): return a * b
PI = 3.14159

# main.py:
import math_utils
print(math_utils.add(3, 4))      # 7
print(math_utils.PI)             # 3.14159

# Import specific names
from math_utils import add, PI
print(add(3, 4))     # 7 — no prefix needed
print(PI)            # 3.14159

# Alias
import math_utils as mu
from math_utils import multiply as mult
print(mu.add(1, 2))
print(mult(3, 4))
```

### Built-in Standard Library (Must Know)

```python
import math
print(math.sqrt(16))          # 4.0
print(math.pi)                # 3.14159...
print(math.ceil(4.3))         # 5
print(math.floor(4.7))        # 4
print(math.log(100, 10))      # 2.0
print(math.factorial(5))      # 120

import random
print(random.random())        # Float 0.0 to 1.0
print(random.randint(1, 6))   # Simluate dice
print(random.choice(["a","b","c"]))  # Random item
lst = [1, 2, 3, 4, 5]
random.shuffle(lst)           # Shuffle in-place
print(random.sample(lst, 3))  # 3 unique random items

import datetime
now = datetime.datetime.now()
print(now)                    # 2024-01-15 10:30:00
print(now.strftime("%Y-%m-%d"))  # 2024-01-15
today = datetime.date.today()
delta = datetime.timedelta(days=30)
future = today + delta
print(future)

import os
print(os.getenv("PATH"))       # Get environment variable
os.environ["MY_VAR"] = "value" # Set env var
print(os.cpu_count())          # Number of CPUs

import sys
print(sys.argv)               # Command line arguments
print(sys.version)            # Python version
sys.exit(0)                   # Exit program

import itertools
# Infinite counter
counter = itertools.count(start=1, step=2)
print([next(counter) for _ in range(5)])  # [1, 3, 5, 7, 9]

# Combinations & permutations
from itertools import combinations, permutations, product
print(list(combinations([1,2,3], 2)))    # [(1,2),(1,3),(2,3)]
print(list(permutations([1,2,3], 2)))    # [(1,2),(1,3),(2,1),...]
print(list(product([0,1], repeat=3)))    # Binary strings of length 3

import collections
from collections import Counter, defaultdict, OrderedDict, deque, namedtuple
# (Already covered in Chapter 6)
```

### Packages

```python
# Package = folder with __init__.py
#
# my_package/
#   __init__.py
#   database.py
#   auth.py
#   utils/
#     __init__.py
#     helpers.py

# Import from package
from my_package import database
from my_package.auth import login
from my_package.utils.helpers import format_date

# __init__.py can expose what's public
# In my_package/__init__.py:
# from .database import Database
# from .auth import login, logout
# This lets users do: from my_package import Database
```

### if __name__ == "__main__"

```python
# This pattern is crucial!
# When Python runs a file:
# - Directly (python script.py): __name__ == "__main__"
# - Imported: __name__ == "script" (the module name)

def main():
    print("Running as main script")

def helper():
    return "I'm a reusable function"

if __name__ == "__main__":
    main()    # Only runs when executed directly, not when imported

# This lets files be both executable scripts AND importable modules
```

---

---

<a name="regex"></a>
## 🔍 CHAPTER 16: REGULAR EXPRESSIONS

```python
import re

text = "Contact us at support@company.com or sales@company.org"

# Search — find first match
match = re.search(r'\w+@\w+\.\w+', text)
if match:
    print(match.group())   # support@company.com

# Findall — find all matches
emails = re.findall(r'\w+@\w+\.\w+', text)
print(emails)   # ['support@company.com', 'sales@company.org']

# Common patterns
patterns = {
    "email":   r'[\w.-]+@[\w.-]+\.\w+',
    "phone":   r'\b\d{3}[-.]?\d{3}[-.]?\d{4}\b',
    "url":     r'https?://[\w/:%#\$&\?\(\)~\.=\+\-]+',
    "ip":      r'\b\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3}\b',
    "date":    r'\d{4}-\d{2}-\d{2}',
    "integer": r'-?\d+',
}

# Groups
log = "2024-01-15 ERROR: Connection timeout"
pattern = r'(\d{4}-\d{2}-\d{2}) (\w+): (.+)'
m = re.match(pattern, log)
if m:
    print(m.group(1))   # 2024-01-15
    print(m.group(2))   # ERROR
    print(m.group(3))   # Connection timeout

# Named groups
pattern = r'(?P<date>\d{4}-\d{2}-\d{2}) (?P<level>\w+): (?P<msg>.+)'
m = re.match(pattern, log)
if m:
    print(m.group("date"))  # 2024-01-15
    print(m.group("level")) # ERROR

# Sub — replace
text = "Hello   World   Python"
clean = re.sub(r'\s+', ' ', text)   # "Hello World Python"

# Compile for reuse (faster)
email_re = re.compile(r'[\w.-]+@[\w.-]+\.\w+', re.IGNORECASE)
found = email_re.findall(text)
```

---

<a name="functional"></a>
## ⚙️ CHAPTER 17: FUNCTIONAL PROGRAMMING

```python
# map — apply function to each item
numbers = [1, 2, 3, 4, 5]
squared = list(map(lambda x: x**2, numbers))
# [1, 4, 9, 16, 25]

# More Pythonic: use comprehension instead
squared = [x**2 for x in numbers]

# filter — keep items where function returns True
evens = list(filter(lambda x: x % 2 == 0, numbers))
# [2, 4]

# reduce — combine all items into one value
from functools import reduce
product = reduce(lambda a, b: a * b, numbers)   # 1*2*3*4*5 = 120
total = reduce(lambda a, b: a + b, numbers)     # 15

# Real-world pipeline
orders = [
    {"item": "Laptop", "price": 999.99, "qty": 2},
    {"item": "Mouse",  "price": 29.99,  "qty": 5},
    {"item": "Desk",   "price": 499.99, "qty": 1},
]

# Calculate total revenue
total = sum(map(lambda o: o["price"] * o["qty"], orders))
print(f"Revenue: ${total:,.2f}")   # $2,648.93

# High-value orders only
high_value = list(filter(lambda o: o["price"] * o["qty"] > 500, orders))

# functools.partial — pre-fill arguments
from functools import partial

def power(base, exp):
    return base ** exp

square = partial(power, exp=2)
cube   = partial(power, exp=3)
print(square(5))   # 25
print(cube(3))     # 27

# functools.lru_cache — memoization
from functools import lru_cache

@lru_cache(maxsize=128)
def fibonacci(n):
    if n < 2:
        return n
    return fibonacci(n-1) + fibonacci(n-2)

print(fibonacci(50))   # Instant, even for large n
```

---

<a name="context-managers"></a>
## 🔒 CHAPTER 18: CONTEXT MANAGERS

```python
# with statement ensures setup/teardown even if error occurs
# __enter__ runs on entry, __exit__ runs on exit

# Class-based context manager
class DatabaseConnection:
    def __init__(self, url):
        self.url = url
        self.connection = None

    def __enter__(self):
        print(f"Connecting to {self.url}")
        self.connection = {"url": self.url, "active": True}
        return self.connection

    def __exit__(self, exc_type, exc_val, exc_tb):
        print("Closing connection")
        self.connection["active"] = False
        return False   # Don't suppress exceptions

with DatabaseConnection("localhost:5432") as conn:
    print(f"Using connection: {conn}")
# Connecting to localhost:5432
# Using connection: ...
# Closing connection (ALWAYS runs)

# Generator-based context manager (simpler)
from contextlib import contextmanager

@contextmanager
def timer_context(name):
    import time
    print(f"Starting: {name}")
    start = time.perf_counter()
    try:
        yield           # Code inside 'with' runs here
    finally:
        elapsed = time.perf_counter() - start
        print(f"Finished {name}: {elapsed:.4f}s")

with timer_context("data processing"):
    total = sum(range(1_000_000))

# Multiple context managers
with open("input.txt") as fin, open("output.txt", "w") as fout:
    fout.write(fin.read().upper())
```

---

<a name="concurrency"></a>
## 🔄 CHAPTER 19: MULTITHREADING & MULTIPROCESSING

```python
# Concurrency: doing multiple things seemingly at once
# Parallelism: actually doing multiple things at once

# THREADING — good for I/O-bound tasks (network, file I/O)
import threading
import time

def download_file(url, delay):
    print(f"Downloading {url}...")
    time.sleep(delay)   # Simulate download
    print(f"Done: {url}")

# Sequential: 4 + 2 + 3 = 9 seconds
# Threaded: max(4, 2, 3) = 4 seconds

urls = [("site1.com", 4), ("site2.com", 2), ("site3.com", 3)]

threads = []
for url, delay in urls:
    t = threading.Thread(target=download_file, args=(url, delay))
    threads.append(t)
    t.start()

for t in threads:
    t.join()   # Wait for all threads to finish

# Thread with return value using list
results = []
lock = threading.Lock()   # Prevent race conditions

def worker(n, results, lock):
    result = n * n
    with lock:
        results.append(result)

threads = [threading.Thread(target=worker, args=(i, results, lock))
           for i in range(5)]
for t in threads: t.start()
for t in threads: t.join()
print(sorted(results))   # [0, 1, 4, 9, 16]

# ThreadPoolExecutor (easier)
from concurrent.futures import ThreadPoolExecutor

def fetch_data(url):
    time.sleep(1)   # Simulate
    return f"Data from {url}"

with ThreadPoolExecutor(max_workers=4) as executor:
    futures = [executor.submit(fetch_data, f"url{i}") for i in range(5)]
    results = [f.result() for f in futures]
print(results)

# MULTIPROCESSING — good for CPU-bound tasks
from multiprocessing import Pool
import os

def cpu_intensive(n):
    # Heavy computation
    return sum(i**2 for i in range(n))

if __name__ == "__main__":   # Required guard for multiprocessing
    with Pool(processes=os.cpu_count()) as pool:
        results = pool.map(cpu_intensive, [100000, 200000, 300000])
    print(results)
```

---

<a name="async"></a>
## ⚡ CHAPTER 20: ASYNC / AWAIT

```python
# Async is best for I/O-bound work with many concurrent operations
# (web servers, scrapers, chat bots)
import asyncio
import time

# async def makes a coroutine
async def fetch_page(url, delay):
    print(f"Fetching {url}")
    await asyncio.sleep(delay)   # Non-blocking sleep
    return f"Content of {url}"

async def main():
    # Sequential: 3 seconds total
    # r1 = await fetch_page("site1.com", 1)
    # r2 = await fetch_page("site2.com", 2)

    # Concurrent: ~2 seconds total
    results = await asyncio.gather(
        fetch_page("site1.com", 1),
        fetch_page("site2.com", 2),
        fetch_page("site3.com", 1.5),
    )
    for r in results:
        print(r)

asyncio.run(main())

# Real async web scraper pattern
async def scrape_all(urls):
    async def fetch(session, url):
        # In real code: async with session.get(url) as resp:
        await asyncio.sleep(0.1)   # Simulate
        return f"data:{url}"

    tasks = [fetch(None, url) for url in urls]
    return await asyncio.gather(*tasks)
```

---

<a name="database"></a>
## 🗄️ CHAPTER 21: DATABASE (SQLite)

```python
import sqlite3

# Connect (creates file if not exists)
conn = sqlite3.connect("myapp.db")
conn.row_factory = sqlite3.Row  # Access columns by name
cursor = conn.cursor()

# Create table
cursor.execute("""
    CREATE TABLE IF NOT EXISTS users (
        id INTEGER PRIMARY KEY AUTOINCREMENT,
        name TEXT NOT NULL,
        email TEXT UNIQUE NOT NULL,
        age INTEGER,
        created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
    )
""")

# Insert — use ? placeholders (NEVER string format — SQL injection!)
cursor.execute(
    "INSERT INTO users (name, email, age) VALUES (?, ?, ?)",
    ("Alice", "alice@example.com", 25)
)

# Insert many
users_data = [
    ("Bob", "bob@example.com", 30),
    ("Charlie", "charlie@example.com", 35),
]
cursor.executemany(
    "INSERT INTO users (name, email, age) VALUES (?, ?, ?)",
    users_data
)
conn.commit()

# Query
cursor.execute("SELECT * FROM users WHERE age > ?", (25,))
rows = cursor.fetchall()
for row in rows:
    print(dict(row))   # {'id': 2, 'name': 'Bob', ...}

# Update
cursor.execute("UPDATE users SET age = ? WHERE name = ?", (26, "Alice"))
conn.commit()

# Delete
cursor.execute("DELETE FROM users WHERE id = ?", (3,))
conn.commit()

conn.close()

# Context manager pattern (recommended)
with sqlite3.connect("myapp.db") as conn:
    conn.row_factory = sqlite3.Row
    cursor = conn.cursor()
    cursor.execute("SELECT COUNT(*) as total FROM users")
    print(cursor.fetchone()["total"])
```

---

<a name="testing"></a>
## 🧪 CHAPTER 22: TESTING

```python
# test_calculator.py
import unittest

def add(a, b): return a + b
def divide(a, b):
    if b == 0:
        raise ZeroDivisionError("Cannot divide by zero")
    return a / b

class TestCalculator(unittest.TestCase):

    def test_add_positive(self):
        self.assertEqual(add(3, 4), 7)

    def test_add_negative(self):
        self.assertEqual(add(-1, -2), -3)

    def test_add_zero(self):
        self.assertEqual(add(5, 0), 5)

    def test_divide_normal(self):
        self.assertAlmostEqual(divide(10, 3), 3.333, places=3)

    def test_divide_by_zero(self):
        with self.assertRaises(ZeroDivisionError):
            divide(10, 0)

    def setUp(self):
        """Runs before EACH test."""
        self.data = [1, 2, 3]

    def tearDown(self):
        """Runs after EACH test."""
        pass

    @classmethod
    def setUpClass(cls):
        """Runs ONCE before all tests."""
        cls.db = "test_db"

    @classmethod
    def tearDownClass(cls):
        """Runs ONCE after all tests."""
        pass

if __name__ == "__main__":
    unittest.main()

# Run: python -m pytest test_calculator.py -v
# Or:  python -m unittest test_calculator.py
```

---

<a name="design-patterns"></a>
## 🏗️ CHAPTER 23: DESIGN PATTERNS

```python
# ===== SINGLETON — Only one instance ever =====
class DatabasePool:
    _instance = None

    def __new__(cls):
        if cls._instance is None:
            cls._instance = super().__new__(cls)
            cls._instance.connections = []
        return cls._instance

db1 = DatabasePool()
db2 = DatabasePool()
print(db1 is db2)   # True — same object!

# ===== FACTORY — Create objects without specifying class =====
class Notification:
    def send(self, message): pass

class EmailNotification(Notification):
    def send(self, message):
        print(f"Email: {message}")

class SMSNotification(Notification):
    def send(self, message):
        print(f"SMS: {message}")

class PushNotification(Notification):
    def send(self, message):
        print(f"Push: {message}")

def notification_factory(channel):
    channels = {
        "email": EmailNotification,
        "sms": SMSNotification,
        "push": PushNotification,
    }
    cls = channels.get(channel)
    if not cls:
        raise ValueError(f"Unknown channel: {channel}")
    return cls()

notif = notification_factory("email")
notif.send("Your order shipped!")   # Email: Your order shipped!

# ===== OBSERVER — Subscribe to events =====
class EventBus:
    def __init__(self):
        self._listeners = {}

    def subscribe(self, event, callback):
        self._listeners.setdefault(event, []).append(callback)

    def publish(self, event, data=None):
        for cb in self._listeners.get(event, []):
            cb(data)

bus = EventBus()
bus.subscribe("user.signup", lambda d: print(f"Send welcome email to {d}"))
bus.subscribe("user.signup", lambda d: print(f"Log signup event: {d}"))
bus.publish("user.signup", "alice@example.com")
# Send welcome email to alice@example.com
# Log signup event: alice@example.com

# ===== STRATEGY — Swap algorithms at runtime =====
class Sorter:
    def __init__(self, strategy):
        self.strategy = strategy

    def sort(self, data):
        return self.strategy(data)

sorter = Sorter(sorted)
print(sorter.sort([3, 1, 4, 1, 5]))   # [1, 1, 3, 4, 5]

sorter.strategy = lambda d: sorted(d, reverse=True)
print(sorter.sort([3, 1, 4, 1, 5]))   # [5, 4, 3, 1, 1]
```

---

<a name="dsa"></a>
## 🧮 CHAPTER 24: DATA STRUCTURES & ALGORITHMS (DSA)

### Complexity Reference

| Operation       | List  | Dict/Set | Sorted List |
|-----------------|-------|----------|-------------|
| Access by index | O(1)  | N/A      | O(1)        |
| Search          | O(n)  | O(1) avg | O(log n)    |
| Insert at end   | O(1)  | O(1) avg | O(log n)    |
| Insert at front | O(n)  | O(1) avg | O(log n)    |
| Delete          | O(n)  | O(1) avg | O(log n)    |

### Stack (LIFO)

```python
# Use list as stack
stack = []
stack.append(1)    # push
stack.append(2)
stack.append(3)
print(stack.pop()) # 3 — LIFO
print(stack)       # [1, 2]

# Real use: balanced parentheses check
def is_balanced(s):
    stack = []
    pairs = {")": "(", "}": "{", "]": "["}
    for ch in s:
        if ch in "({[":
            stack.append(ch)
        elif ch in ")}]":
            if not stack or stack[-1] != pairs[ch]:
                return False
            stack.pop()
    return len(stack) == 0

print(is_balanced("{[()]}"))  # True
print(is_balanced("{[(])}"))  # False
```

### Queue (FIFO)

```python
from collections import deque

queue = deque()
queue.append(1)       # enqueue
queue.append(2)
queue.append(3)
print(queue.popleft()) # 1 — FIFO

# BFS uses a queue
def bfs(graph, start):
    visited = set()
    queue = deque([start])
    order = []
    while queue:
        node = queue.popleft()
        if node not in visited:
            visited.add(node)
            order.append(node)
            queue.extend(graph.get(node, []))
    return order

graph = {
    "A": ["B", "C"],
    "B": ["D", "E"],
    "C": ["F"],
    "D": [], "E": [], "F": []
}
print(bfs(graph, "A"))   # ['A', 'B', 'C', 'D', 'E', 'F']
```

### Linked List

```python
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None

class LinkedList:
    def __init__(self):
        self.head = None

    def append(self, data):
        new = Node(data)
        if not self.head:
            self.head = new
            return
        current = self.head
        while current.next:
            current = current.next
        current.next = new

    def display(self):
        result = []
        current = self.head
        while current:
            result.append(str(current.data))
            current = current.next
        return " -> ".join(result)

    def reverse(self):
        prev, current = None, self.head
        while current:
            next_node = current.next
            current.next = prev
            prev = current
            current = next_node
        self.head = prev

ll = LinkedList()
for v in [1, 2, 3, 4, 5]:
    ll.append(v)
print(ll.display())   # 1 -> 2 -> 3 -> 4 -> 5
ll.reverse()
print(ll.display())   # 5 -> 4 -> 3 -> 2 -> 1
```

### Binary Search

```python
# O(log n) — extremely fast on sorted lists
def binary_search(arr, target):
    left, right = 0, len(arr) - 1
    while left <= right:
        mid = (left + right) // 2
        if arr[mid] == target:
            return mid
        elif arr[mid] < target:
            left = mid + 1
        else:
            right = mid - 1
    return -1

arr = [1, 3, 5, 7, 9, 11, 13, 15]
print(binary_search(arr, 7))    # 3 (index)
print(binary_search(arr, 6))    # -1 (not found)
```

### Sorting Algorithms

```python
# Bubble Sort — O(n²)
def bubble_sort(arr):
    n = len(arr)
    for i in range(n):
        for j in range(0, n-i-1):
            if arr[j] > arr[j+1]:
                arr[j], arr[j+1] = arr[j+1], arr[j]
    return arr

# Merge Sort — O(n log n)
def merge_sort(arr):
    if len(arr) <= 1:
        return arr
    mid = len(arr) // 2
    left = merge_sort(arr[:mid])
    right = merge_sort(arr[mid:])
    return merge(left, right)

def merge(left, right):
    result = []
    i = j = 0
    while i < len(left) and j < len(right):
        if left[i] <= right[j]:
            result.append(left[i]); i += 1
        else:
            result.append(right[j]); j += 1
    return result + left[i:] + right[j:]

print(merge_sort([3, 1, 4, 1, 5, 9, 2, 6]))
# [1, 1, 2, 3, 4, 5, 6, 9]

# Quick Sort — O(n log n) avg
def quick_sort(arr):
    if len(arr) <= 1:
        return arr
    pivot = arr[len(arr) // 2]
    left  = [x for x in arr if x < pivot]
    mid   = [x for x in arr if x == pivot]
    right = [x for x in arr if x > pivot]
    return quick_sort(left) + mid + quick_sort(right)
```

### Two Pointers (Interview Favorite)

```python
# Two Sum — find pair that adds to target
def two_sum(nums, target):
    seen = {}    # value -> index
    for i, num in enumerate(nums):
        complement = target - num
        if complement in seen:
            return [seen[complement], i]
        seen[num] = i
    return []

print(two_sum([2, 7, 11, 15], 9))   # [0, 1]

# Reverse a string with two pointers
def reverse_string(s):
    chars = list(s)
    left, right = 0, len(chars) - 1
    while left < right:
        chars[left], chars[right] = chars[right], chars[left]
        left += 1
        right -= 1
    return "".join(chars)

# Valid palindrome
def is_palindrome(s):
    s = "".join(c.lower() for c in s if c.isalnum())
    return s == s[::-1]
```

### Sliding Window

```python
# Max sum subarray of size k
def max_sum_subarray(arr, k):
    window_sum = sum(arr[:k])
    max_sum = window_sum
    for i in range(k, len(arr)):
        window_sum += arr[i] - arr[i-k]  # Slide window
        max_sum = max(max_sum, window_sum)
    return max_sum

print(max_sum_subarray([2, 1, 5, 1, 3, 2], 3))  # 9 (5+1+3)

# Longest substring without repeating characters
def length_of_longest_substring(s):
    char_set = set()
    left = 0
    max_len = 0
    for right in range(len(s)):
        while s[right] in char_set:
            char_set.remove(s[left])
            left += 1
        char_set.add(s[right])
        max_len = max(max_len, right - left + 1)
    return max_len

print(length_of_longest_substring("abcabcbb"))  # 3 (abc)
```

### Dynamic Programming

```python
# DP = solve subproblems, store results, build up to solution

# 0/1 Knapsack
def knapsack(weights, values, capacity):
    n = len(weights)
    dp = [[0] * (capacity + 1) for _ in range(n + 1)]
    for i in range(1, n + 1):
        for w in range(capacity + 1):
            dp[i][w] = dp[i-1][w]   # Don't take item i
            if weights[i-1] <= w:
                # Take item i
                dp[i][w] = max(dp[i][w], dp[i-1][w-weights[i-1]] + values[i-1])
    return dp[n][capacity]

weights = [2, 3, 4, 5]
values  = [3, 4, 5, 6]
print(knapsack(weights, values, 8))   # 10

# Longest Common Subsequence
def lcs(s1, s2):
    m, n = len(s1), len(s2)
    dp = [[0]*(n+1) for _ in range(m+1)]
    for i in range(1, m+1):
        for j in range(1, n+1):
            if s1[i-1] == s2[j-1]:
                dp[i][j] = dp[i-1][j-1] + 1
            else:
                dp[i][j] = max(dp[i-1][j], dp[i][j-1])
    return dp[m][n]

print(lcs("ABCBDAB", "BDCAB"))   # 4 (BCAB)
```

---

<a name="memory"></a>
## 🧠 CHAPTER 25: MEMORY MANAGEMENT & PERFORMANCE

```python
# Python uses reference counting + garbage collection
import sys
import gc

x = [1, 2, 3]
print(sys.getsizeof(x))   # Size in bytes

# Reference counting
a = [1, 2, 3]
b = a          # refcount = 2
del a          # refcount = 1
del b          # refcount = 0 — object freed

# Memory-efficient alternatives
# List vs Generator
import sys
lst = [x**2 for x in range(10000)]
gen = (x**2 for x in range(10000))
print(sys.getsizeof(lst))   # ~85k bytes
print(sys.getsizeof(gen))   # ~208 bytes!

# __slots__ — reduce memory for many instances
class WithoutSlots:
    def __init__(self, x, y):
        self.x = x
        self.y = y

class WithSlots:
    __slots__ = ["x", "y"]   # No __dict__, saves ~50% memory!
    def __init__(self, x, y):
        self.x = x
        self.y = y

p1 = WithoutSlots(1, 2)
p2 = WithSlots(1, 2)
print(sys.getsizeof(p1.__dict__))  # 232 bytes
# p2 has no __dict__!

# Profiling — find bottlenecks
import cProfile
cProfile.run('sum(i**2 for i in range(100000))')

# timeit — measure small code snippets
import timeit
t = timeit.timeit(
    setup="data = list(range(1000))",
    stmt="[x**2 for x in data]",
    number=10000
)
print(f"Time: {t:.3f}s")
```

---

<a name="internals"></a>
## ⚙️ CHAPTER 26: PYTHON INTERNALS

```python
# The GIL (Global Interpreter Lock)
# Only ONE Python thread can execute Python bytecode at a time
# → Threads don't speed up CPU-bound tasks
# → Use multiprocessing for CPU-bound parallelism
# → Threads STILL help for I/O-bound (network, disk) — GIL released during I/O

# Everything in Python is an OBJECT
print(type(42))        # <class 'int'>
print(type(print))     # <class 'builtin_function_or_method'>
print(type(int))       # <class 'type'>

# Integer caching (small ints -5 to 256 are cached)
a = 100
b = 100
print(a is b)   # True — same cached object

a = 1000
b = 1000
print(a is b)   # False — different objects (outside cache range)

# String interning
s1 = "hello"
s2 = "hello"
print(s1 is s2)   # True (short strings are interned)

# Bytecode
import dis
def add(a, b):
    return a + b

dis.dis(add)   # Shows the bytecode instructions

# __dunder__ attributes
class MyClass:
    """My class docstring."""
    x = 10

print(MyClass.__name__)     # MyClass
print(MyClass.__doc__)      # My class docstring.
print(MyClass.__dict__)     # {'x': 10, ...}
print(MyClass.__module__)   # __main__
```

---

<a name="interview"></a>
## 🎯 CHAPTER 27: TOP 100 INTERVIEW QUESTIONS & ANSWERS

### BASIC PYTHON

**Q1: What is Python? What are its key features?**
> Python is a high-level, interpreted, dynamically-typed language. Key features: readable syntax, dynamic typing, automatic memory management, rich standard library, supports OOP/functional/procedural paradigms, and a massive ecosystem (NumPy, Django, etc.).

**Q2: What is the difference between `is` and `==`?**
```python
a = [1, 2, 3]
b = [1, 2, 3]
print(a == b)   # True  — checks VALUE equality
print(a is b)   # False — checks IDENTITY (same object in memory)
# Use 'is' only for None, True, False checks
```

**Q3: What is mutable vs immutable in Python?**
```python
# Mutable (can be changed): list, dict, set, custom objects
lst = [1, 2]
lst.append(3)     # OK — modifies in-place

# Immutable (cannot be changed): int, float, str, tuple, frozenset
s = "hello"
# s[0] = "H"    # TypeError!
s = s.replace("h", "H")   # Creates NEW string
```

**Q4: What are Python's built-in data types?**
> int, float, complex, str, bool, NoneType, list, tuple, dict, set, frozenset, bytes, bytearray

**Q5: Difference between list, tuple, set, dict?**
| Type | Ordered | Mutable | Duplicates | Keys |
|------|---------|---------|------------|------|
| list | ✅ | ✅ | ✅ | index |
| tuple| ✅ | ❌ | ✅ | index |
| set  | ❌ | ✅ | ❌ | - |
| dict | ✅(3.7+)| ✅ | ❌(keys) | key |

**Q6: What is a decorator? Give an example.**
```python
def log_calls(func):
    def wrapper(*args, **kwargs):
        print(f"Calling {func.__name__}")
        result = func(*args, **kwargs)
        print(f"Done {func.__name__}")
        return result
    return wrapper

@log_calls
def add(a, b):
    return a + b

add(3, 4)
# Calling add
# Done add
```

**Q7: What is a generator? Why use it?**
```python
# Generator uses 'yield', produces values lazily (one at a time)
# Saves memory for large sequences
def infinite_count():
    n = 0
    while True:
        yield n
        n += 1

gen = infinite_count()
print(next(gen))   # 0
print(next(gen))   # 1
# Never loads all values into memory
```

**Q8: What is `*args` and `**kwargs`?**
```python
def func(*args, **kwargs):
    print(args)    # Tuple of positional args
    print(kwargs)  # Dict of keyword args

func(1, 2, 3, name="Alice", age=25)
# (1, 2, 3)
# {'name': 'Alice', 'age': 25}
```

**Q9: What is list comprehension? Why is it faster?**
```python
# Faster because it's optimized in C internally
# One line, readable
squares = [x**2 for x in range(10) if x % 2 == 0]

# vs traditional loop (slower):
squares = []
for x in range(10):
    if x % 2 == 0:
        squares.append(x**2)
```

**Q10: What is the difference between `deepcopy` and `copy`?**
```python
import copy
original = [[1, 2], [3, 4]]

shallow = copy.copy(original)     # New list, but inner lists are SHARED
deep = copy.deepcopy(original)    # Completely independent copy

shallow[0].append(99)
print(original)   # [[1, 2, 99], [3, 4]] — CHANGED!

deep[0].append(99)
print(original)   # [[1, 2, 99], [3, 4]] — unchanged
```

### OOP QUESTIONS

**Q11: What are the 4 pillars of OOP?**
> 1. **Encapsulation** — hide internal state, expose only interface
> 2. **Inheritance** — child class reuses parent class code
> 3. **Polymorphism** — same method name, different behavior per class
> 4. **Abstraction** — hide complexity, expose only what's needed

**Q12: What is `__init__` vs `__new__`?**
```python
class MyClass:
    def __new__(cls, *args, **kwargs):
        print("__new__ creates the object")
        instance = super().__new__(cls)
        return instance   # Returns the new object

    def __init__(self, value):
        print("__init__ initializes the object")
        self.value = value

# __new__ runs first (creates object), then __init__ (fills it)
obj = MyClass(42)
```

**Q13: What is MRO (Method Resolution Order)?**
```python
class A: pass
class B(A): pass
class C(A): pass
class D(B, C): pass

print(D.__mro__)
# D → B → C → A → object
# Python uses C3 linearization algorithm
# Call super() follows MRO
```

**Q14: What is `@property` and why use it?**
```python
class Circle:
    def __init__(self, radius):
        self._radius = radius

    @property
    def radius(self):           # Getter
        return self._radius

    @radius.setter
    def radius(self, value):    # Setter with validation
        if value < 0:
            raise ValueError("Radius must be positive")
        self._radius = value

    @property
    def area(self):             # Computed, read-only
        return 3.14159 * self._radius ** 2

c = Circle(5)
print(c.area)    # 78.53...
c.radius = 10    # Uses setter
```

**Q15: Difference between classmethod, staticmethod, instance method?**
```python
class MyClass:
    class_var = "shared"

    def instance_method(self):
        return self          # Access to instance

    @classmethod
    def class_method(cls):
        return cls           # Access to class, not instance
        # Used for alternative constructors

    @staticmethod
    def static_method():
        return "utility"     # No access to class or instance
        # Like a regular function but inside class namespace
```

### ADVANCED PYTHON

**Q16: What is the GIL? How does it affect multithreading?**
> The GIL (Global Interpreter Lock) allows only one thread to execute Python bytecode at a time. For I/O-bound tasks (network, disk), threads still help because GIL is released during I/O. For CPU-bound tasks, use `multiprocessing` which bypasses the GIL by using separate processes.

**Q17: What are context managers?**
```python
# Ensures setup/teardown happens even if error occurs
# Implements __enter__ and __exit__
with open("file.txt") as f:    # __enter__ opens, __exit__ closes
    data = f.read()

# Custom context manager with contextlib
from contextlib import contextmanager

@contextmanager
def managed_resource():
    print("setup")
    try:
        yield "resource"
    finally:
        print("cleanup")   # ALWAYS runs
```

**Q18: What is monkey patching?**
```python
# Replacing/modifying code at runtime (use carefully!)
import datetime

class TestDate(datetime.date):
    @classmethod
    def today(cls):
        return cls(2024, 1, 1)   # Fixed date for testing

datetime.date = TestDate   # Monkey patch!
print(datetime.date.today())   # 2024-01-01 always
```

**Q19: What are metaclasses?**
```python
# A metaclass is a "class of a class" — controls class creation
class SingletonMeta(type):
    _instances = {}

    def __call__(cls, *args, **kwargs):
        if cls not in cls._instances:
            cls._instances[cls] = super().__call__(*args, **kwargs)
        return cls._instances[cls]

class Database(metaclass=SingletonMeta):
    pass

db1 = Database()
db2 = Database()
print(db1 is db2)   # True — singleton!
```

**Q20: Explain Python's memory management.**
> Python uses reference counting (tracks how many variables point to an object) + cyclic garbage collector (finds and frees circular references). When refcount reaches 0, object is freed immediately. The `gc` module handles cycles.

### CODING PROBLEMS (WITH SOLUTIONS)

**Q21: Reverse a string**
```python
s = "Hello World"
print(s[::-1])                        # dlroW olleH
print("".join(reversed(s)))           # dlroW olleH
print("".join(list(s))[::-1])         # dlroW olleH
```

**Q22: Check if string is palindrome**
```python
def is_palindrome(s):
    s = "".join(c.lower() for c in s if c.isalnum())
    return s == s[::-1]

print(is_palindrome("A man a plan a canal Panama"))  # True
```

**Q23: Find duplicate in list**
```python
def find_duplicates(lst):
    seen = set()
    return {x for x in lst if x in seen or seen.add(x)}

print(find_duplicates([1,2,3,2,4,3,5]))  # {2, 3}
```

**Q24: Flatten nested list**
```python
def flatten(nested):
    result = []
    for item in nested:
        if isinstance(item, list):
            result.extend(flatten(item))
        else:
            result.append(item)
    return result

print(flatten([1, [2, [3, [4]], 5]]))  # [1, 2, 3, 4, 5]
```

**Q25: Find missing number in 1..n**
```python
def missing_number(nums):
    n = len(nums)
    return n*(n+1)//2 - sum(nums)

print(missing_number([0,1,3,4,5]))  # 2
```

**Q26: FizzBuzz**
```python
for i in range(1, 101):
    if i % 15 == 0: print("FizzBuzz")
    elif i % 3 == 0: print("Fizz")
    elif i % 5 == 0: print("Buzz")
    else: print(i)
```

**Q27: Count character frequency**
```python
from collections import Counter
text = "programming"
print(Counter(text))
# Counter({'g': 2, 'r': 2, 'm': 2, 'p': 1, 'o': 1, ...})
```

**Q28: Find second largest**
```python
def second_largest(nums):
    unique = sorted(set(nums), reverse=True)
    return unique[1] if len(unique) > 1 else None

print(second_largest([3, 1, 4, 1, 5, 9, 2, 6]))  # 6
```

**Q29: Group anagrams together**
```python
from collections import defaultdict

def group_anagrams(words):
    groups = defaultdict(list)
    for word in words:
        key = tuple(sorted(word))
        groups[key].append(word)
    return list(groups.values())

print(group_anagrams(["eat","tea","tan","ate","nat","bat"]))
# [['eat','tea','ate'], ['tan','nat'], ['bat']]
```

**Q30: Fibonacci — multiple approaches**
```python
# Recursive (slow)
def fib_rec(n): return n if n<=1 else fib_rec(n-1)+fib_rec(n-2)

# Iterative (fast, O(n))
def fib_iter(n):
    a, b = 0, 1
    for _ in range(n): a, b = b, a+b
    return a

# Generator (memory-efficient)
def fib_gen():
    a, b = 0, 1
    while True:
        yield a
        a, b = b, a+b

# Memoized
from functools import lru_cache
@lru_cache(maxsize=None)
def fib_memo(n): return n if n<=1 else fib_memo(n-1)+fib_memo(n-2)
```

**Q31: What is the difference between `__str__` and `__repr__`?**
```python
class Point:
    def __init__(self, x, y):
        self.x = x
        self.y = y

    def __str__(self):
        return f"({self.x}, {self.y})"   # For users — print()

    def __repr__(self):
        return f"Point({self.x}, {self.y})"  # For developers — debug

p = Point(3, 4)
print(str(p))    # (3, 4)
print(repr(p))   # Point(3, 4)
print([p])       # [Point(3, 4)] — lists use repr
```

**Q32: What is a lambda function? When to use?**
```python
# Short, anonymous functions — use for simple one-liners
double = lambda x: x * 2
add = lambda x, y: x + y

# Best use case: as arguments to map/filter/sorted
names = ["Alice", "Bob", "Charlie"]
print(sorted(names, key=lambda n: len(n)))   # ['Bob', 'Alice', 'Charlie']

# Avoid for complex logic — use def instead for readability
```

**Q33: How does Python handle exceptions vs other languages?**
> Python uses EAFP (Easier to Ask Forgiveness than Permission) style — try/except is idiomatic. Other languages use LBYL (Look Before You Leap). Python's approach is often more readable and handles race conditions better.

**Q34: What are Python itertools?**
```python
from itertools import (
    count,          # infinite counter
    cycle,          # infinite cycle through iterable
    chain,          # combine iterables
    combinations,   # choose r items, no repeat
    permutations,   # ordered arrangements
    product,        # Cartesian product
    groupby,        # group consecutive items
    islice,         # slice from iterator
    accumulate,     # running totals
)

# Examples:
from itertools import accumulate
print(list(accumulate([1,2,3,4,5])))         # [1,3,6,10,15] running sum
print(list(accumulate([1,2,3,4,5], max)))    # [1,2,3,4,5] running max

from itertools import chain
print(list(chain([1,2], [3,4], [5,6])))   # [1,2,3,4,5,6]
```

**Q35: What is `zip()` and `enumerate()`?**
```python
names = ["Alice", "Bob", "Charlie"]
scores = [85, 92, 78]

# zip — pair up two iterables
for name, score in zip(names, scores):
    print(f"{name}: {score}")

# enumerate — add index to iteration
for i, name in enumerate(names, start=1):
    print(f"{i}. {name}")

# Unzip with *
pairs = [(1,"a"), (2,"b"), (3,"c")]
numbers, letters = zip(*pairs)
print(numbers)   # (1, 2, 3)
print(letters)   # ('a', 'b', 'c')
```

**Q36: Difference between `append` and `extend`?**
```python
lst = [1, 2, 3]
lst.append([4, 5])    # [1, 2, 3, [4, 5]]  — adds as single element
lst = [1, 2, 3]
lst.extend([4, 5])    # [1, 2, 3, 4, 5]    — adds each element
lst = [1, 2, 3]
lst += [4, 5]         # [1, 2, 3, 4, 5]    — same as extend
```

**Q37: How to remove duplicates while preserving order?**
```python
lst = [3, 1, 4, 1, 5, 9, 2, 6, 5, 3]

# Using dict.fromkeys (preserves order, Python 3.7+)
deduped = list(dict.fromkeys(lst))
print(deduped)   # [3, 1, 4, 5, 9, 2, 6]

# Using seen set
seen = set()
deduped = [x for x in lst if not (x in seen or seen.add(x))]
```

**Q38: What is `__slots__`?**
```python
class Point:
    __slots__ = ['x', 'y']   # No __dict__ — saves memory

    def __init__(self, x, y):
        self.x = x
        self.y = y

p = Point(1, 2)
# p.z = 3   # AttributeError — can't add new attributes!
# Good for classes with many instances
```

**Q39: Explain `try/except/else/finally`**
```python
try:
    result = 10 / 2        # Risky code
except ZeroDivisionError:
    print("Division by zero")
else:
    print(f"Result: {result}")  # Runs only if NO exception
finally:
    print("Always runs")        # Cleanup — always executes

# Output: Result: 5.0 \n Always runs
```

**Q40: What is duck typing?**
```python
# "If it walks like a duck and quacks like a duck, it's a duck"
# Python doesn't check the TYPE — it checks if the METHOD exists

class Dog:
    def speak(self): return "Woof"

class Cat:
    def speak(self): return "Meow"

class Robot:
    def speak(self): return "Beep boop"

def make_speak(animal):
    print(animal.speak())   # Works on any object with speak()!

for thing in [Dog(), Cat(), Robot()]:
    make_speak(thing)
```

---

<a name="exercises"></a>
## 💪 CHAPTER 28: LOGIC BUILDING EXERCISES (FULLY SOLVED)

### Level 1: Beginner

```python
# 1. Print sum of digits
def digit_sum(n):
    return sum(int(d) for d in str(abs(n)))

print(digit_sum(12345))   # 15

# 2. Check Armstrong number (153 = 1³+5³+3³)
def is_armstrong(n):
    digits = str(n)
    power = len(digits)
    return n == sum(int(d)**power for d in digits)

print(is_armstrong(153))   # True
print(is_armstrong(370))   # True

# 3. Print all prime numbers up to n (Sieve of Eratosthenes)
def primes_up_to(n):
    sieve = [True] * (n+1)
    sieve[0] = sieve[1] = False
    for i in range(2, int(n**0.5)+1):
        if sieve[i]:
            for j in range(i*i, n+1, i):
                sieve[j] = False
    return [i for i in range(n+1) if sieve[i]]

print(primes_up_to(50))
# [2, 3, 5, 7, 11, 13, 17, 19, 23, 29, 31, 37, 41, 43, 47]

# 4. Reverse words in sentence
def reverse_words(sentence):
    return " ".join(sentence.split()[::-1])

print(reverse_words("Hello World Python"))  # Python World Hello

# 5. Count words in sentence
def word_count(text):
    return len(text.split())

print(word_count("The quick brown fox"))   # 4
```

### Level 2: Intermediate

```python
# 6. Caesar cipher (encode/decode text)
def caesar(text, shift, decode=False):
    if decode: shift = -shift
    result = []
    for ch in text:
        if ch.isalpha():
            base = ord('A') if ch.isupper() else ord('a')
            result.append(chr((ord(ch) - base + shift) % 26 + base))
        else:
            result.append(ch)
    return "".join(result)

encoded = caesar("Hello World", 3)
print(encoded)                          # Khoor Zruog
print(caesar(encoded, 3, decode=True))  # Hello World

# 7. Find all permutations
def permutations(s):
    if len(s) <= 1:
        return [s]
    result = []
    for i, ch in enumerate(s):
        rest = s[:i] + s[i+1:]
        for perm in permutations(rest):
            result.append(ch + perm)
    return result

print(sorted(permutations("abc")))
# ['abc', 'acb', 'bac', 'bca', 'cab', 'cba']

# 8. Matrix rotation (90 degrees clockwise)
def rotate_90(matrix):
    return [list(row) for row in zip(*matrix[::-1])]

m = [[1,2,3],[4,5,6],[7,8,9]]
rotated = rotate_90(m)
for row in rotated: print(row)
# [7, 4, 1]
# [8, 5, 2]
# [9, 6, 3]

# 9. Run-length encoding
def rle_encode(s):
    if not s: return ""
    result = []
    count = 1
    for i in range(1, len(s)):
        if s[i] == s[i-1]:
            count += 1
        else:
            result.append(f"{count}{s[i-1]}")
            count = 1
    result.append(f"{count}{s[-1]}")
    return "".join(result)

print(rle_encode("AAABBBCCDDDDEE"))  # 3A3B2C4D2E

# 10. Stack-based expression evaluator
def evaluate_rpn(tokens):
    """Reverse Polish Notation: "3 4 + 2 *" = (3+4)*2 = 14"""
    stack = []
    ops = {'+': lambda a,b: a+b, '-': lambda a,b: a-b,
           '*': lambda a,b: a*b, '/': lambda a,b: int(a/b)}
    for token in tokens.split():
        if token in ops:
            b, a = stack.pop(), stack.pop()
            stack.append(ops[token](a, b))
        else:
            stack.append(int(token))
    return stack[0]

print(evaluate_rpn("3 4 + 2 *"))   # 14
print(evaluate_rpn("5 1 2 + 4 * + 3 -"))  # 14
```

### Level 3: Advanced

```python
# 11. LRU Cache implementation
class LRUCache:
    def __init__(self, capacity):
        from collections import OrderedDict
        self.cache = OrderedDict()
        self.capacity = capacity

    def get(self, key):
        if key not in self.cache:
            return -1
        self.cache.move_to_end(key)   # Most recently used
        return self.cache[key]

    def put(self, key, value):
        if key in self.cache:
            self.cache.move_to_end(key)
        self.cache[key] = value
        if len(self.cache) > self.capacity:
            self.cache.popitem(last=False)  # Remove LRU item

cache = LRUCache(3)
cache.put(1, "one")
cache.put(2, "two")
cache.put(3, "three")
print(cache.get(1))    # "one"
cache.put(4, "four")   # evicts key 2
print(cache.get(2))    # -1 (evicted)

# 12. Word ladder (BFS)
from collections import deque

def word_ladder(begin, end, word_list):
    """Find shortest transformation sequence: hit → hot → dot → dog → cog"""
    words = set(word_list)
    queue = deque([(begin, [begin])])
    visited = {begin}

    while queue:
        word, path = queue.popleft()
        if word == end:
            return path

        for i in range(len(word)):
            for c in 'abcdefghijklmnopqrstuvwxyz':
                new_word = word[:i] + c + word[i+1:]
                if new_word in words and new_word not in visited:
                    visited.add(new_word)
                    queue.append((new_word, path + [new_word]))
    return []

wordList = ["hot","dot","dog","lot","log","cog"]
print(word_ladder("hit", "cog", wordList))
# ['hit', 'hot', 'dot', 'dog', 'cog']

# 13. Trie (Prefix Tree)
class TrieNode:
    def __init__(self):
        self.children = {}
        self.is_end = False

class Trie:
    def __init__(self):
        self.root = TrieNode()

    def insert(self, word):
        node = self.root
        for ch in word:
            node = node.children.setdefault(ch, TrieNode())
        node.is_end = True

    def search(self, word):
        node = self.root
        for ch in word:
            if ch not in node.children:
                return False
            node = node.children[ch]
        return node.is_end

    def starts_with(self, prefix):
        node = self.root
        for ch in prefix:
            if ch not in node.children:
                return False
            node = node.children[ch]
        return True

trie = Trie()
for word in ["apple", "app", "application", "apply"]:
    trie.insert(word)

print(trie.search("app"))         # True
print(trie.search("ap"))          # False
print(trie.starts_with("appl"))   # True

# 14. Thread-safe singleton
import threading

class ThreadSafeSingleton:
    _instance = None
    _lock = threading.Lock()

    def __new__(cls):
        if cls._instance is None:
            with cls._lock:
                if cls._instance is None:   # Double-check locking
                    cls._instance = super().__new__(cls)
        return cls._instance

# 15. Decorator with class (stateful decorator)
class CountCalls:
    def __init__(self, func):
        self.func = func
        self.count = 0
        import functools
        functools.update_wrapper(self, func)

    def __call__(self, *args, **kwargs):
        self.count += 1
        print(f"Call #{self.count} to {self.func.__name__}")
        return self.func(*args, **kwargs)

@CountCalls
def greet(name):
    return f"Hello, {name}!"

print(greet("Alice"))   # Call #1 to greet → Hello, Alice!
print(greet("Bob"))     # Call #2 to greet → Hello, Bob!
print(greet.count)      # 2
```

---

## 🗺️ YOUR LEARNING ROADMAP

```
WEEK 1-2: Chapters 1-5  (Basics, Data Types, Control Flow, Functions)
WEEK 3-4: Chapters 6-8  (Data Structures, Strings, Files)
WEEK 5-6: Chapters 9-11 (OOP, 4 Pillars, Decorators)
WEEK 7-8: Chapters 12-17 (Generators, Comprehensions, Exceptions, FP)
WEEK 9-10: Chapters 18-22 (Concurrency, Async, Database, Testing)
WEEK 11-12: Chapters 23-26 (Design Patterns, DSA, Memory, Internals)
WEEK 13+: Chapter 27-28  (Interview Q&A + Practice Problems Daily)
```

## 📚 RESOURCES TO CONTINUE

| Resource | Focus |
|----------|-------|
| `leetcode.com` | DSA problems (start Easy, then Medium) |
| `realpython.com` | In-depth Python tutorials |
| `docs.python.org` | Official documentation |
| `github.com` | Read open-source Python projects |
| `projecteuler.net` | Math + programming problems |

## 🔑 GOLDEN RULES OF A PYTHON DEVELOPER

1. **Readability counts** — Code is read 10x more than written
2. **Don't repeat yourself** — DRY: If you copy-paste, make a function
3. **Fail loudly** — Raise exceptions, don't silently swallow errors
4. **Test everything** — Untested code is broken code
5. **Think about edge cases** — Empty input? Negative numbers? None?
6. **Profile before optimizing** — Don't guess where slowness is
7. **Use the standard library** — It's tested, fast, and documented
8. **Understand, don't memorize** — Know WHY, syntax you can look up

---

*This guide covers 100% of what you need to become a strong Python developer and pass technical interviews. Now go practice!* 🚀
