# Inheritance in C++

## Definition
**Inheritance** is a mechanism by which a new class (derived/child) acquires the properties and behaviors of an existing class (base/parent).

## Benefits of Inheritance
1. **Code Reusability** — reuse base class code in derived class
2. **Method Overriding** — redefine base class methods in derived class
3. **Runtime Polymorphism** — use base class pointers for derived objects
4. **Hierarchical Classification** — model real-world relationships

## Types of Inheritance

### 1. Single Inheritance
One base class, one derived class.
```
Base → Derived
```
```cpp
class Animal {
public:
    void eat() { cout << "Eating"; }
};
class Dog : public Animal {
public:
    void bark() { cout << "Barking"; }
};
```

### 2. Multiple Inheritance
Multiple base classes, one derived class.
```
Base1 ─┐
       ├→ Derived
Base2 ─┘
```
```cpp
class Academic {
public:
    int marks;
};
class Sports {
public:
    int sportsPoints;
};
class Result : public Academic, public Sports {
public:
    int total() { return marks + sportsPoints; }
};
```

### 3. Multilevel Inheritance
Chain of inheritance: Grandparent → Parent → Child
```
Base → Intermediate → Derived
```
```cpp
class Person {
public:
    string name;
    int age;
};
class Employee : public Person {
public:
    int empId;
    string designation;
};
class Manager : public Employee {
public:
    int teamSize;
};
```

### 4. Hierarchical Inheritance
Multiple derived classes from one base class.
```
        Base
       /    \
Derived1   Derived2
```

### 5. Hybrid Inheritance
Combination of two or more types of inheritance.

## Access Specifiers in Inheritance
| Base Access   | public inheritance | protected inheritance | private inheritance |
|---------------|-------------------|----------------------|---------------------|
| public        | public            | protected            | private             |
| protected     | protected         | protected            | private             |
| private       | Not accessible    | Not accessible       | Not accessible      |

## Virtual Base Class
- Prevents "diamond problem" in multiple inheritance
- Ensures only one copy of base class is inherited

```cpp
class A {
public:
    int x;
};
class B : virtual public A {};  // Virtual inheritance
class C : virtual public A {};  // Virtual inheritance
class D : public B, public C {}; // Only one copy of A's x
```

## Protected Data Member
- Accessible within the class and its derived classes
- NOT accessible from outside or friend functions

## Short Answer Questions (1 mark each)
- What is use of protected data member in inheritance?
- Declare a derived class D from two base classes, A and B.
- What is Virtual base class?

## Exam Questions (4-6 marks)
1. Explain different types of inheritance with suitable examples
2. Write a short note on Inheritance
3. Create a base class Person. Derive Employee from Person. Create Allowance. Derive Salary from both.
4. Create two base classes Academic and Sports. Derive Result inheriting from both. Calculate total.
5. Create class Person → Employee → Manager hierarchy

## Programming Pattern: Multilevel Inheritance
```cpp
class Person {
protected:
    string name;
    int age;
public:
    Person(string n, int a) : name(n), age(a) {}
    void displayPerson() {
        cout << "Name: " << name << ", Age: " << age << endl;
    }
};

class Employee : public Person {
protected:
    int empId;
    string designation;
public:
    Employee(string n, int a, int id, string des)
        : Person(n, a), empId(id), designation(des) {}
    void displayEmployee() {
        displayPerson();
        cout << "ID: " << empId << ", Designation: " << designation << endl;
    }
};

class Manager : public Employee {
    int teamSize;
public:
    Manager(string n, int a, int id, string des, int ts)
        : Employee(n, a, id, des), teamSize(ts) {}
    void displayManager() {
        displayEmployee();
        cout << "Team Size: " << teamSize << endl;
    }
};
```

---
*Source: Chapter 4 Slides, Exam Papers (June 2024, Sept 2024, June 2025)*
