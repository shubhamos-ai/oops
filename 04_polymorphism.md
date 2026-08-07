# Polymorphism in C++

## Definition
**Polymorphism** means "many forms" — the ability of a function/object to take multiple forms.

## Two Types of Polymorphism

### 1. Compile-Time Polymorphism (Static Binding)
Resolved at compile time. Achieved through:
- **Function Overloading**
- **Operator Overloading**

### 2. Run-Time Polymorphism (Dynamic Binding)
Resolved at runtime. Achieved through:
- **Virtual Functions**
- **Function Overriding**

## Function Overloading
Multiple functions with the **same name** but **different parameter lists**.

```cpp
class Calculator {
public:
    int add(int a, int b) { return a + b; }
    double add(double a, double b) { return a + b; }
    int add(int a, int b, int c) { return a + b + c; }
};
```

### Rules for Overloading
- Different number of parameters, OR
- Different types of parameters, OR
- Different order of parameters
- Return type alone is NOT enough

## Operator Overloading
Redefine the behavior of an operator for user-defined types.

```cpp
class Complex {
    int real, imag;
public:
    Complex(int r, int i) : real(r), imag(i) {}
    Complex operator+(const Complex &obj) {
        return Complex(real + obj.real, imag + obj.imag);
    }
    void display() { cout << real << "+" << imag << "i\n"; }
};
```

### Commonly Overloaded Operators
`+`, `-`, `*`, `/`, `==`, `!=`, `<<`, `>>`, `[]`, `()`

## Virtual Functions
- Declared with `virtual` keyword in base class
- Overridden in derived class
- Called through base class pointer/reference
- Enables runtime polymorphism

```cpp
class Shape {
public:
    virtual void draw() { cout << "Drawing shape\n"; }
    virtual double area() = 0;  // Pure virtual (abstract)
};

class Circle : public Shape {
    double radius;
public:
    Circle(double r) : radius(r) {}
    void draw() override { cout << "Drawing circle\n"; }
    double area() override { return 3.14159 * radius * radius; }
};

class Rectangle : public Shape {
    double width, height;
public:
    Rectangle(double w, double h) : width(w), height(h) {}
    void draw() override { cout << "Drawing rectangle\n"; }
    double area() override { return width * height; }
};
```

## Compile-Time vs Run-Time Polymorphism
| Feature            | Compile-Time          | Run-Time              |
|--------------------|-----------------------|-----------------------|
| Binding            | Static (early)        | Dynamic (late)        |
| Mechanism          | Overloading           | Overriding            |
| Performance        | Faster                | Slightly slower       |
| Flexibility        | Less flexible         | More flexible         |
| Keywords           | None                  | virtual, override     |
| Resolved by        | Compiler              | Virtual table (vtable)|

## Dynamic Polymorphism Pattern (Base Class Pointer)
```cpp
Shape *shapes[2];
shapes[0] = new Circle(5.0);
shapes[1] = new Rectangle(4.0, 6.0);

for (int i = 0; i < 2; i++) {
    shapes[i]->draw();
    cout << "Area: " << shapes[i]->area() << endl;
}
```

## Short Answer Questions (1 mark each)
- What is polymorphism?
- What is the role of virtual functions in polymorphism?
- How many types of polymorphisms are supported by C++?
- What is the use of `virtual` keyword?
- Mention the use of keyword Virtual.

## Exam Questions (4-6 marks)
1. What is polymorphism in C++? Differentiate between compile-time and run-time polymorphism with examples
2. Create a class Shape with virtual function area(). Derive Rectangle and Circle. Demonstrate dynamic polymorphism with base class pointer.
3. Create a class Media with virtual function play(). Derive Audio and Video and override play(). Call using base class pointer.
4. What is Polymorphism? Briefly explain with appropriate example.
5. Write the types of polymorphism.

---
*Source: Chapter 4 Slides, Unit 9, Exam Papers (June 2024, Sept 2024, June 2025)*
