# Type Conversion in C++

## Definition
Type conversion is the process of converting one data type to another.

## Two Types

### 1. Implicit Type Conversion (Automatic)
- Done by the compiler automatically
- No data loss for widening conversions

```cpp
int x = 10;
double y = x;     // int -> double (implicit)
```

### 2. Explicit Type Conversion (Type Casting)
- Done by the programmer using cast operators

```cpp
double x = 3.14;
int y = (int)x;           // C-style cast
int z = static_cast<int>(x);  // C++ style cast
```

## Type Conversion in C++ Classes

### Basic to Class Type
- Constructor used for conversion
- Single-argument constructor enables implicit conversion

```cpp
class Distance {
    int meters;
public:
    Distance(int m) : meters(m) {}  // Conversion constructor
    void display() { cout << meters << "m" << endl; }
};

int main() {
    Distance d = 100;  // Implicit: int -> Distance
    d.display();       // Output: 100m
}
```

### Class to Basic Type
- Define a conversion operator in the class

```cpp
class Distance {
    int meters;
public:
    Distance(int m) : meters(m) {}
    operator int() { return meters; }  // Conversion operator
};

int main() {
    Distance d(100);
    int m = d;  // Implicit: Distance -> int
    cout << m;  // Output: 100
}
```

### Class to Class Conversion
- Use conversion constructor or conversion operator

```cpp
class Meter {
    int m;
public:
    Meter(int val) : m(val) {}
};

class Feet {
    int ft;
public:
    Feet(int val) : ft(val) {}
    Feet(Meter met) { ft = met.getMeters() * 3.28; }  // Meter -> Feet
};
```

## Static Cast
```cpp
double d = 3.14;
int i = static_cast<int>(d);  // Preferred C++ way
```

## Short Answer Questions
- What is typecasting? Give one example.
- What is Type conversion in C++?

## Exam Questions
1. What is Type conversion in C++? Define Basic to Class type and Class to Basic type conversion with suitable examples
2. Explain type conversions in C++. Discuss Basic to class type conversion with a suitable example
3. What is typecasting? Give one example

---
*Source: Type Conv.txt, Exam Papers (June 2024, Sept 2024, June 2025)*
