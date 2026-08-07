# Python Basics

## Variables and Data Types
```python
# Variable declaration (no need to specify type)
name = "Alice"        # string
age = 20              # integer
gpa = 3.85            # float
is_student = True     # boolean
```

## Data Types
| Type     | Example              |
|----------|----------------------|
| int      | `x = 10`             |
| float    | `x = 3.14`           |
| str      | `x = "hello"`        |
| bool     | `x = True`           |
| list     | `x = [1, 2, 3]`      |
| tuple    | `x = (1, 2, 3)`      |
| dict     | `x = {"a": 1}`       |
| set      | `x = {1, 2, 3}`      |

## Lists
```python
fruits = ["apple", "banana", "cherry"]
fruits.append("date")      # Add element
fruits.remove("banana")    # Remove element
print(fruits[0])           # Access by index
print(len(fruits))         # Length
```

## Tuples
```python
colors = ("red", "green", "blue")
print(colors[0])           # Access
# Cannot modify (immutable)
```

## Dictionaries
```python
student = {"name": "Alice", "age": 20, "gpa": 3.85}
print(student["name"])     # Access value
student["age"] = 21        # Update
student["grade"] = "A"     # Add new key
```

## Control Structures
```python
# If-elif-else
if age >= 18:
    print("Adult")
elif age >= 13:
    print("Teenager")
else:
    print("Child")

# For loop
for i in range(10):
    print(i)

# While loop
count = 0
while count < 5:
    print(count)
    count += 1
```

## Functions
```python
def greet(name, msg="Hello"):
    return f"{msg}, {name}!"

print(greet("Alice"))
print(greet("Bob", "Welcome"))
```

## Key Features of Python
1. Easy to learn and read
2. Interpreted language
3. Dynamically typed
4. Object-oriented
5. Extensive standard library
6. Cross-platform
7. Supports multiple paradigms

## Programs

### Print 1 to 10
```python
for i in range(1, 11):
    print(i)
```

### Find Maximum of Three Numbers
```python
def find_max(a, b, c):
    if a >= b and a >= c:
        return a
    elif b >= a and b >= c:
        return b
    else:
        return c

a = int(input("Enter first number: "))
b = int(input("Enter second number: "))
c = int(input("Enter third number: "))
print("Maximum:", find_max(a, b, c))
```

### Check Prime Number
```python
def is_prime(n):
    if n <= 1:
        return False
    for i in range(2, int(n**0.5) + 1):
        if n % i == 0:
            return False
    return True

num = int(input("Enter a number: "))
if is_prime(num):
    print(f"{num} is a prime number")
else:
    print(f"{num} is not a prime number")
```

## Short Answer Questions
- Name any two features of Python.
- How are tuple and list defined in Python?
- What are the key features of Python?

## Exam Questions
1. How to define variables in Python? Write a program to print 1 to 10 numbers using Python
2. Write a python program which prints maximum of given three numbers
3. Write a Python program to check whether a given number is a prime number or not
4. Mention key features of Python programming language

---
*Source: Exam Papers (June 2024, Sept 2024, June 2025)*
