# Constructors and Destructors in C++

## Constructor
A **constructor** is a special member function that is automatically called when an object is created. It initializes the object's data members.

### Key Properties
- Same name as the class
- No return type (not even `void`)
- Called automatically on object creation
- Can be overloaded

### Syntax
```cpp
class MyClass {
    int x;
public:
    MyClass() {         // Default constructor
        x = 0;
    }
    MyClass(int val) {  // Parameterized constructor
        x = val;
    }
};
```

## Types of Constructors

### 1. Default Constructor
- Takes no arguments
- Called when no initializer is provided

```cpp
class Student {
    string name;
    int roll;
public:
    Student() {
        name = "Unknown";
        roll = 0;
    }
};
```

### 2. Parameterized Constructor
- Takes arguments to initialize data members

```cpp
class Student {
    string name;
    int roll;
public:
    Student(string n, int r) {
        name = n;
        roll = r;
    }
};
```

### 3. Copy Constructor
- Creates a new object as a copy of an existing object
- Takes a reference to an existing object

```cpp
class Student {
    string name;
    int roll;
public:
    Student(string n, int r) : name(n), roll(r) {}
    Student(const Student &s) {  // Copy constructor
        name = s.name;
        roll = s.roll;
    }
};
```

## Destructor
A **destructor** is a special member function that is automatically called when an object goes out of scope or is deleted. It performs cleanup.

### Key Properties
- Same name as class with `~` prefix
- No arguments, no return type
- Cannot be overloaded
- Called in reverse order of construction

```cpp
class MyClass {
public:
    MyClass()  { cout << "Constructor called\n"; }
    ~MyClass() { cout << "Destructor called\n"; }
};
```

## Constructor vs Destructor
| Constructor                     | Destructor                    |
|---------------------------------|-------------------------------|
| Called on object creation       | Called on object destruction   |
| Same name as class              | `~` + class name              |
| Can be overloaded               | Cannot be overloaded          |
| Initializes objects             | Cleans up resources           |
| Can have parameters             | No parameters                 |

## Inline Functions
- Function definition expanded at compile-time
- Reduces function call overhead
- Best for small, frequently called functions

```cpp
inline int cube(int n) {
    return n * n * n;
}
```

## Short Answer Questions (1 mark each)
- What is a constructor? Mention its types.
- What is a destructor?
- What is a copy constructor?
- What is the advantage of using inline function?
- Mention types of constructors.
- Constructor vs Destructor differentiate.

## Exam Questions (4-6 marks)
1. Explain and define all types of constructors with appropriate examples
2. Explain copy constructor with suitable example
3. Explain role of constructor and destructor in class with example
4. Write a C++ program to create inline function that returns cube of given number
5. Differentiate Constructor vs Destructor

---
*Source: Chapter 2 Slides, Unit 1, Exam Papers (June 2024, Sept 2024, June 2025)*
