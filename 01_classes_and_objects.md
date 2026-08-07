# Classes and Objects in C++

## Definition
A **class** is a user-defined data type that acts as a blueprint for objects. It bundles data (attributes) and functions (methods) together.

An **object** is an instance of a class — a concrete entity created from the class blueprint.

## Syntax

```cpp
class ClassName {
private:
    // data members (hidden)
public:
    // member functions (accessible)
};
```

## Key Concepts

### Access Specifiers
| Specifier    | Access Level                        |
|-------------|-------------------------------------|
| `public`    | Accessible from anywhere            |
| `private`   | Accessible only within the class    |
| `protected` | Accessible within class + derived   |

### Data Members vs Member Functions
- **Data members**: Variables declared inside a class (attributes)
- **Member functions**: Functions declared inside a class (methods)

### Declaring Objects
```cpp
ClassName obj1;          // Stack allocation
ClassName obj2 = obj1;   // Copy constructor
ClassName *ptr = new ClassName();  // Heap allocation
```

## Types of Members
1. **Data members** — store values
2. **Member functions** — perform operations
3. **Static members** — shared across all objects
4. **Friend functions** — can access private members
5. **Virtual functions** — for runtime polymorphism

## `this` Pointer
- Every member function has an implicit `this` pointer
- Points to the calling object
- Used to distinguish between parameter and member variable

```cpp
void setAge(int age) {
    this->age = age;  // 'age' is parameter, 'this->age' is member
}
```

## Static Data Members
- Shared across all instances of a class
- Declared with `static` keyword
- Initialized outside the class using scope resolution operator

```cpp
class Counter {
    static int count;
public:
    Counter() { count++; }
    static int getCount() { return count; }
};
int Counter::count = 0;
```

## Abstract Class
- Contains at least one pure virtual function
- Cannot be instantiated (no objects can be created)
- Serves as base class for derived classes

```cpp
class Shape {
public:
    virtual void draw() = 0;  // Pure virtual function
};
```

## Enumerated Data Type (`enum`)
```cpp
enum Color { RED, GREEN, BLUE };
Color c = RED;
```

## Scope Resolution Operator (`::`)
- Access static members of a class
- Define member functions outside the class
- Access global variables when shadowed

```cpp
class MyClass {
    static int x;
public:
    void display();
};
int MyClass::x = 10;          // Initialize static member
void MyClass::display() {     // Define outside class
    cout << x;
}
```

## Class vs Object
| Class              | Object                    |
|--------------------|---------------------------|
| Blueprint/Template | Instance of class         |
| Logical entity     | Physical entity           |
| No memory allocated| Memory allocated          |
| Declared once      | Can create many           |

## Short Answer Questions (1 mark each)
- What is a Class?
- Define Data Hiding.
- Explain enumerated data type.
- Mention types of constructors.
- What is the use of `this` pointer?
- What is a static data member?
- How do you define a class and its object?
- Define public access modifier.
- What is enum?
- Write the syntax to declare a static variable count.

## Exam Questions (4-6 marks)
1. Differentiate Class vs Object
2. Explain different types of members in C++ class
3. What is Data Hiding? How is it achieved?
4. Explain the role of `this` keyword with example
5. Write a short note on Static Data members and member functions
6. What is an abstract class? How many objects can be created?
7. Explain the Scope Resolution Operator with examples

---
*Source: Chapter 2 Slides, Unit 1, Exam Papers (June 2024, Sept 2024, June 2025)*
