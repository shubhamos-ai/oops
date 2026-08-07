# Templates in C++

## Definition
**Templates** enable generic programming — writing code that works with any data type.

## Function Template
```cpp
template <typename T>
T getMax(T a, T b) {
    return (a > b) ? a : b;
}

// Usage
cout << getMax(5, 10);        // 10 (int)
cout << getMax(3.14, 2.71);   // 3.14 (double)
cout << getMax('a', 'z');     // z (char)
```

## Class Template
```cpp
template <typename T>
class Calculator {
    T num1, num2;
public:
    Calculator(T a, T b) : num1(a), num2(b) {}
    T add() { return num1 + num2; }
    T subtract() { return num1 - num2; }
    T multiply() { return num1 * num2; }
    T divide() { return num1 / num2; }
};

// Usage
Calculator<int> intCalc(10, 5);
Calculator<double> dblCalc(10.5, 2.5);
```

## Template Specialization
```cpp
template <>
class Calculator<string> {
    string s1, s2;
public:
    Calculator(string a, string b) : s1(a), s2(b) {}
    string add() { return s1 + s2; }
};
```

## Generic Programming
- Write once, use with any type
- Type safety at compile time
- No performance overhead (resolved at compile time)

## Practical Examples

### Swap Function Template
```cpp
template <typename T>
void swapValues(T &a, T &b) {
    T temp = a;
    a = b;
    b = temp;
}
```

### Calculator Class Template
```cpp
template <typename T>
class Calculator {
public:
    T add(T a, T b) { return a + b; }
    T subtract(T a, T b) { return a - b; }
    T multiply(T a, T b) { return a * b; }
    T divide(T a, T b) { return (b != 0) ? a / b : 0; }
};
```

## Short Answer Questions (1 mark each)
- What is a template?
- What do you mean by standard template library (STL)?
- What is generic programming?

## Exam Questions (4-6 marks)
1. Write a program to swap two integer and two floating point variables using templates
2. Create a class template Calculator that performs basic arithmetic operations on two integers and two floating point variables
3. What is generic programming? Write a function template to swap two numbers
4. Explain function templates and class templates with examples

---
*Source: Chapter 7 Slides, Unit 10, Exam Papers (Sept 2024, June 2025)*
