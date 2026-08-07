# OOP Practical Programs (C++) - Complete List

## Program 1: Type Conversion (Basic ↔ Class)
**File:** Type Conv.txt (already exists)

```cpp
#include <iostream>
using namespace std;

class SIDist {
    int sid;
public:
    SIDist() : sid(0) {}
    SIDist(int s) : sid(s) {}
    void getSIDist() { cout << "Enter SIDist: "; cin >> sid; }
    void showSIDist() { cout << "SIDist: " << sid << endl; }
};

class IDistance {
    int idist;
public:
    IDistance() : idist(0) {}
    IDistance(int i) : idist(i) {}
    void getIDistance() { cout << "Enter IDistance: "; cin >> idist; }
    void showIDistance() { cout << "IDistance: " << idist << endl; }
    operator SIDist() { return SIDist(idist); }
};

int main() {
    SIDist s1;
    IDistance i1;
    i1.getIDistance();
    s1 = i1;  // IDistance to SIDist
    s1.showSIDist();
    return 0;
}
```

---

## Program 2: Class and Objects - Distance (feet + inches)
```cpp
#include <iostream>
using namespace std;

class Distance {
    int feet, inches;
public:
    void getDistance() {
        cout << "Enter feet and inches: ";
        cin >> feet >> inches;
    }
    void display() {
        cout << feet << " feet " << inches << " inches" << endl;
    }
    Distance add(Distance d) {
        Distance temp;
        temp.feet = feet + d.feet;
        temp.inches = inches + d.inches;
        if (temp.inches >= 12) {
            temp.feet++;
            temp.inches -= 12;
        }
        return temp;
    }
};

int main() {
    Distance d1, d2, d3;
    d1.getDistance();
    d2.getDistance();
    d3 = d1.add(d2);
    cout << "Sum: "; d3.display();
    return 0;
}
```

---

## Program 3: Constructor Types (Default, Parameterized, Copy)
```cpp
#include <iostream>
using namespace std;

class Student {
    string name;
    int roll;
public:
    Student() { name = "Unknown"; roll = 0; }
    Student(string n, int r) : name(n), roll(r) {}
    Student(const Student &s) : name(s.name), roll(s.roll) {}
    void display() {
        cout << "Name: " << name << ", Roll: " << roll << endl;
    }
};

int main() {
    Student s1;                    // Default
    Student s2("Alice", 101);     // Parameterized
    Student s3 = s2;              // Copy
    s1.display();
    s2.display();
    s3.display();
    return 0;
}
```

---

## Program 4: Inline Function (Cube)
```cpp
#include <iostream>
using namespace std;

inline int cube(int n) {
    return n * n * n;
}

int main() {
    int num = 3;
    cout << "Cube of " << num << " = " << cube(num) << endl;
    return 0;
}
```

---

## Program 5: Function Overloading (add)
```cpp
#include <iostream>
using namespace std;

class Calculator {
public:
    int add(int a, int b) { return a + b; }
    double add(double a, double b) { return a + b; }
    int add(int a, int b, int c) { return a + b + c; }
};

int main() {
    Calculator calc;
    cout << "2+3 = " << calc.add(2, 3) << endl;
    cout << "1.5+2.5 = " << calc.add(1.5, 2.5) << endl;
    cout << "1+2+3 = " << calc.add(1, 2, 3) << endl;
    return 0;
}
```

---

## Program 6: Inheritance Types

### Single Inheritance
```cpp
#include <iostream>
using namespace std;

class Animal {
public:
    void eat() { cout << "Eating..." << endl; }
};

class Dog : public Animal {
public:
    void bark() { cout << "Barking..." << endl; }
};

int main() {
    Dog d;
    d.eat();
    d.bark();
    return 0;
}
```

### Multiple Inheritance
```cpp
class Academic {
public:
    int marks;
    void getMarks() { cin >> marks; }
};

class Sports {
public:
    int sportsPoints;
    void getPoints() { cin >> sportsPoints; }
};

class Result : public Academic, public Sports {
public:
    int total() { return marks + sportsPoints; }
    void display() {
        cout << "Total: " << total() << endl;
    }
};
```

### Multilevel Inheritance
```cpp
class Person {
protected:
    string name;
    int age;
public:
    void getPerson() { cin >> name >> age; }
    void displayPerson() { cout << name << " " << age << endl; }
};

class Employee : public Person {
protected:
    int empId;
public:
    void getEmployee() { cin >> empId; }
    void displayEmployee() {
        displayPerson();
        cout << "ID: " << empId << endl;
    }
};

class Manager : public Employee {
    int teamSize;
public:
    void getManager() { cin >> teamSize; }
    void displayManager() {
        displayEmployee();
        cout << "Team: " << teamSize << endl;
    }
};
```

---

## Program 7: Polymorphism with Virtual Functions (Shape)
```cpp
#include <iostream>
using namespace std;

class Shape {
public:
    virtual void draw() { cout << "Drawing shape" << endl; }
    virtual double area() = 0;
};

class Circle : public Shape {
    double radius;
public:
    Circle(double r) : radius(r) {}
    void draw() override { cout << "Drawing circle" << endl; }
    double area() override { return 3.14159 * radius * radius; }
};

class Rectangle : public Shape {
    double width, height;
public:
    Rectangle(double w, double h) : width(w), height(h) {}
    void draw() override { cout << "Drawing rectangle" << endl; }
    double area() override { return width * height; }
};

int main() {
    Shape *shapes[2];
    shapes[0] = new Circle(5.0);
    shapes[1] = new Rectangle(4.0, 6.0);
    for (int i = 0; i < 2; i++) {
        shapes[i]->draw();
        cout << "Area: " << shapes[i]->area() << endl;
    }
    return 0;
}
```

---

## Program 8: Operator Overloading (+ for Complex)
```cpp
#include <iostream>
using namespace std;

class Complex {
    int real, imag;
public:
    Complex(int r = 0, int i = 0) : real(r), imag(i) {}
    Complex operator+(const Complex &obj) {
        return Complex(real + obj.real, imag + obj.imag);
    }
    void display() { cout << real << "+" << imag << "i" << endl; }
};

int main() {
    Complex c1(3, 4), c2(1, 2);
    Complex c3 = c1 + c2;
    c3.display();
    return 0;
}
```

---

## Program 9: Friend Function
```cpp
#include <iostream>
using namespace std;

class Distance {
    int kilometer;
public:
    Distance(int k) : kilometer(k) {}
    friend void convertToMeters(Distance d);
};

void convertToMeters(Distance d) {
    cout << d.kilometer * 1000 << " meters" << endl;
}

int main() {
    Distance d(5);
    convertToMeters(d);
    return 0;
}
```

---

## Program 10: Templates (Swap)
```cpp
#include <iostream>
using namespace std;

template <typename T>
void swapValues(T &a, T &b) {
    T temp = a;
    a = b;
    b = temp;
}

int main() {
    int x = 5, y = 10;
    swapValues(x, y);
    cout << "x=" << x << " y=" << y << endl;

    double a = 1.5, b = 2.5;
    swapValues(a, b);
    cout << "a=" << a << " b=" << b << endl;
    return 0;
}
```

---

## Program 11: Exception Handling (Division by Zero)
```cpp
#include <iostream>
using namespace std;

double divide(int a, int b) {
    if (b == 0) throw "Division by zero!";
    return (double)a / b;
}

int main() {
    try {
        cout << divide(10, 0) << endl;
    } catch (const char* msg) {
        cout << "Error: " << msg << endl;
    }
    return 0;
}
```

---

## Program 12: File Handling (Read/Write)
```cpp
#include <iostream>
#include <fstream>
using namespace std;

int main() {
    // Write
    ofstream outFile("data.txt");
    outFile << "Hello World" << endl;
    outFile << "Line 2" << endl;
    outFile.close();

    // Read
    ifstream inFile("data.txt");
    string line;
    while (getline(inFile, line)) {
        cout << line << endl;
    }
    inFile.close();
    return 0;
}
```

---

## Program 13: Car Class (SetData/DisplayData)
```cpp
#include <iostream>
using namespace std;

class Car {
    string company;
    int speed;
public:
    void SetData(string c, int s) {
        company = c;
        speed = s;
    }
    void DisplayData() {
        cout << "Company: " << company << ", Speed: " << speed << endl;
    }
};

int main() {
    Car c1;
    c1.SetData("Toyota", 180);
    c1.DisplayData();
    return 0;
}
```

---

## Program 14: Bank Class (Deposit/Withdraw)
```cpp
#include <iostream>
using namespace std;

class Bank {
    string name;
    int account_number;
    double balance;
public:
    void init(string n, int acc, double bal) {
        name = n;
        account_number = acc;
        balance = bal;
    }
    void deposit(double amount) { balance += amount; }
    void withdraw(double amount) {
        if (amount <= balance) balance -= amount;
        else cout << "Insufficient balance" << endl;
    }
    void display() {
        cout << "Name: " << name << ", Acc: " << account_number
             << ", Balance: " << balance << endl;
    }
};

int main() {
    Bank b;
    b.init("Alice", 12345, 10000);
    b.deposit(5000);
    b.withdraw(3000);
    b.display();
    return 0;
}
```

---

## Program 15: Calculator Class Template
```cpp
#include <iostream>
using namespace std;

template <typename T>
class Calculator {
public:
    T add(T a, T b) { return a + b; }
    T subtract(T a, T b) { return a - b; }
    T multiply(T a, T b) { return a * b; }
    T divide(T a, T b) { return (b != 0) ? a / b : 0; }
};

int main() {
    Calculator<int> intCalc;
    Calculator<double> dblCalc;
    cout << "Int add: " << intCalc.add(10, 5) << endl;
    cout << "Dbl add: " << dblCalc.add(10.5, 2.5) << endl;
    return 0;
}
```

---

## Program 16: Python - Print 1 to 10
```python
for i in range(1, 11):
    print(i)
```

## Program 17: Python - Maximum of Three Numbers
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

## Program 18: Python - Check Prime Number
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

---
*Source: Practical List, Exam Papers, Type Conv.txt*
