# Operator Overloading in C++

## Definition
**Operator overloading** allows redefining the behavior of operators for user-defined types (classes/structs).

## Syntax
```cpp
ReturnType operator+(parameters) {
    // implementation
}
```

## Rules
1. Cannot create new operators
2. Cannot change operator precedence/associativity
3. Cannot change arity (number of operands)
4. At least one operand must be user-defined type
5. Cannot overload: `::`, `.*`, `.`, `?:`, `sizeof`

## Commonly Overloaded Operators

### Arithmetic Operators
```cpp
class Complex {
    int real, imag;
public:
    Complex(int r = 0, int i = 0) : real(r), imag(i) {}

    Complex operator+(const Complex &obj) {
        return Complex(real + obj.real, imag + obj.imag);
    }

    Complex operator-(const Complex &obj) {
        return Complex(real - obj.real, imag - obj.imag);
    }

    Complex operator*(const Complex &obj) {
        return Complex(real * obj.real - imag * obj.imag,
                       real * obj.imag + imag * obj.real);
    }
};
```

### Comparison Operators
```cpp
class Time {
    int hours, minutes;
public:
    Time(int h, int m) : hours(h), minutes(m) {}

    bool operator==(const Time &obj) {
        return (hours == obj.hours && minutes == obj.minutes);
    }

    bool operator<(const Time &obj) {
        return (hours < obj.hours) ||
               (hours == obj.hours && minutes < obj.minutes);
    }
};
```

### Stream Operators (<< and >>)
```cpp
class Complex {
    int real, imag;
public:
    Complex(int r, int i) : real(r), imag(i) {}

    friend ostream& operator<<(ostream &out, const Complex &c);
    friend istream& operator>>(istream &in, Complex &c);
};

ostream& operator<<(ostream &out, const Complex &c) {
    out << c.real << "+" << c.imag << "i";
    return out;
}

istream& operator>>(istream &in, Complex &c) {
    in >> c.real >> c.imag;
    return in;
}
```

### Subscript Operator ([])
```cpp
class Array {
    int *arr;
    int size;
public:
    Array(int s) : size(s) { arr = new int[s]; }
    ~Array() { delete[] arr; }

    int& operator[](int index) {
        return arr[index];
    }
};
```

### Function Call Operator (())
```cpp
class Adder {
public:
    int operator()(int a, int b) {
        return a + b;
    }
};

Adder add;
cout << add(5, 3);  // 8
```

### Concatenation Operator (+ for strings)
```cpp
class String {
    char *str;
public:
    String(const char *s) {
        str = new char[strlen(s) + 1];
        strcpy(str, s);
    }

    String operator+(const String &obj) {
        char *temp = new char[strlen(str) + strlen(obj.str) + 1];
        strcpy(temp, str);
        strcat(temp, obj.str);
        return String(temp);
    }
};
```

## Short Answer Questions (1 mark each)
- What is operator overloading?
- Can we overload all operators?
- Which operators cannot be overloaded?

## Exam Questions (4-6 marks)
1. What is operator overloading? Overload the '+' operator to add two objects of class time
2. Write a C++ program to concatenate two strings using operator overloading
3. Write a C++ program to compare two strings by overloading == operator
4. Write a program to overload the + operator for the complex class
5. Explain operator overloading with examples

---
*Source: Unit 9, Exam Papers (June 2024, Sept 2024, June 2025)*
