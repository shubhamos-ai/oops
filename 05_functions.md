# Functions in C++

## Definition
A **function** is a reusable block of code that performs a specific task.

## Types of Functions

### 1. Built-in (Library) Functions
```cpp
#include <cmath>
sqrt(25);    // 5.0
pow(2, 10);  // 1024.0
abs(-5);     // 5
```

### 2. User-Defined Functions
```cpp
int add(int a, int b) {
    return a + b;
}
```

## Function Components
1. **Return type** — data type of returned value
2. **Function name** — identifier
3. **Parameter list** — input arguments
4. **Function body** — code to execute

## Inline Functions
- Expanded at compile-time
- Reduces function call overhead
- Best for small, frequently called functions

```cpp
inline int cube(int n) {
    return n * n * n;
}
```

## Function Overloading
Multiple functions with **same name** but **different parameters**.

```cpp
void display(int x) { cout << x; }
void display(double x) { cout << x; }
void display(string x) { cout << x; }
```

## Default Arguments
```cpp
void greet(string name, string msg = "Hello") {
    cout << msg << " " << name << endl;
}
greet("Alice");           // "Hello Alice"
greet("Bob", "Welcome"); // "Welcome Bob"
```

## Pass by Value vs Pass by Reference

### Pass by Value
```cpp
void swap(int a, int b) {
    int temp = a;
    a = b;
    b = temp;
}
// Original values NOT changed
```

### Pass by Reference
```cpp
void swap(int &a, int &b) {
    int temp = a;
    a = b;
    b = temp;
}
// Original values ARE changed
```

## Static Data Members and Functions
- **Static member**: Shared across all objects
- **Static member function**: Can only access static members

```cpp
class Counter {
    static int count;
public:
    Counter() { count++; }
    static int getCount() { return count; }
};
int Counter::count = 0;
```

## Member Functions with Default Arguments
```cpp
class Distance {
    int feet, inches;
public:
    void setDistance(int f = 0, int i = 0) {
        feet = f;
        inches = i;
    }
};
```

## Short Answer Questions (1 mark each)
- What is an inline function? Give its advantage.
- What is function overloading?
- Difference between pass by value and pass by reference?
- What is a static member function?

## Exam Questions (4-6 marks)
1. What is function overloading in C++? Explain with suitable example
2. Explain different types of functions in C++
3. Write a C++ program to create inline function that returns cube of given number
4. Explain Member Functions with Default Arguments with an example
5. Write a short note on Static Data members and member functions

---
*Source: Chapter 3 Slides, Unit 1, Exam Papers (June 2024, Sept 2024, June 2025)*
