# Exception Handling in C++

## Definition
**Exception handling** is a mechanism to handle runtime errors gracefully, preventing program crashes.

## Three Keywords

### 1. `try`
- Contains code that might throw an exception
- Monitored for errors

### 2. `throw`
- Used to signal an exception
- Throws a value (error code/message)

### 3. `catch`
- Handles the thrown exception
- Contains recovery code

## Syntax
```cpp
try {
    // Code that might throw exception
    if (error_condition) {
        throw exception_value;
    }
} catch (exception_type e) {
    // Handle the exception
    cout << "Error: " << e << endl;
}
```

## Practical Examples

### Division by Zero
```cpp
double divide(int a, int b) {
    if (b == 0) {
        throw "Division by zero!";
    }
    return (double)a / b;
}

int main() {
    try {
        cout << divide(10, 0);
    } catch (const char* msg) {
        cout << "Error: " << msg << endl;
    }
    return 0;
}
```

### Multiple Catch Blocks
```cpp
try {
    int choice;
    cout << "Enter 1 for int, 2 for string: ";
    cin >> choice;

    if (choice == 1) throw 42;
    else if (choice == 2) throw "hello";
    else throw 3.14;
} catch (int e) {
    cout << "Integer: " << e << endl;
} catch (const char* e) {
    cout << "String: " << e << endl;
} catch (...) {
    cout << "Other exception" << endl;
}
```

### Catch All
```cpp
try {
    // risky code
} catch (...) {
    // catches any exception type
}
```

## Common Exception Types
| Exception       | Description                     |
|-----------------|---------------------------------|
| `runtime_error` | Runtime condition error         |
| `logic_error`   | Logical error in program        |
| `overflow_error`| Arithmetic overflow             |
| `invalid_argument` | Invalid argument passed    |

## try Block
- A `try` block contains code that may raise an exception
- If an exception occurs, control transfers to the matching catch block
- If no exception occurs, catch blocks are skipped

## Best Practices
1. Always catch exceptions by reference (`catch (const exception& e)`)
2. Use standard exception classes from `<stdexcept>`
3. Don't use exceptions for normal flow control
4. Clean up resources in catch blocks

## Short Answer Questions (1 mark each)
- What is a try block? What is its use?
- What is the use of throw keyword?

## Exam Questions (4-6 marks)
1. Explain the concept of exception handling in C++ with the syntax of try, catch, and throw
2. Write a program that demonstrates multiple catch blocks
3. What is a try block? What is its use?

---
*Source: Unit 9, Exam Papers (Sept 2024, June 2025)*
