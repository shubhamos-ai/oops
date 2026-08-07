# File Handling and Streams in C++

## C++ Stream Classes Hierarchy

```
ios (base)
├── istream (input)
│   ├── ifstream
│   └── istringstream
├── ostream (output)
│   ├── ofstream
│   └── ostringstream
└── iostream (input + output)
    └── fstream
```

## Key Stream Classes
| Class         | Purpose                          |
|---------------|----------------------------------|
| `ifstream`    | Input from file                  |
| `ofstream`    | Output to file                   |
| `fstream`     | Both input and output            |
| `istringstream` | Input from string             |
| `ostringstream` | Output to string              |

## File Operations

### Writing to a File
```cpp
#include <fstream>

ofstream outFile("data.txt");
outFile << "Hello World" << endl;
outFile << "Line 2" << endl;
outFile.close();
```

### Reading from a File
```cpp
ifstream inFile("data.txt");
string line;
while (getline(inFile, line)) {
    cout << line << endl;
}
inFile.close();
```

### File Modes
| Mode       | Description                     |
|------------|---------------------------------|
| `ios::in`  | Open for reading                |
| `ios::out` | Open for writing                |
| `ios::app` | Append to end of file           |
| `ios::ate` | Open and move to end            |
| `ios::trunc` | Truncate (delete existing)    |

## File Pointers
- `tellg()` — get current read position
- `tellp()` — get current write position
- `seekg()` — move read pointer
- `seekp()` — move write pointer

```cpp
ifstream inFile("data.txt");
cout << "Current position: " << inFile.tellg() << endl;
inFile.seekg(0, ios::beg);  // Move to beginning
```

## File Management Functions

### put() and get()
```cpp
// put() - write single character
ofstream outFile("file.txt");
outFile.put('A');

// get() - read single character
ifstream inFile("file.txt");
char ch;
inFile.get(ch);
```

### getline()
```cpp
ifstream inFile("file.txt");
string line;
getline(inFile, line);  // Read one line
```

### write() and read()
```cpp
// Binary write
ofstream outFile("data.bin", ios::binary);
int num = 42;
outFile.write(reinterpret_cast<char*>(&num), sizeof(num));

// Binary read
ifstream inFile("data.bin", ios::binary);
inFile.read(reinterpret_cast<char*>(&num), sizeof(num));
```

## Short Answer Questions (1 mark each)
- What are file pointers? Give names.
- What is the use of `endl`?
- What is the use of `get()` function?

## Exam Questions (4-6 marks)
1. What are C++ stream classes? Explain the hierarchy of input and output stream classes
2. Explain the concept of Input stream and Output Stream in C++ programming structure
3. Explain the use of file-management functions: put(), getline() with a suitable program
4. Write a program to read and write data to a file using fstream

---
*Source: Chapter 8 Slides, Unit 10, Exam Papers (June 2024, Sept 2024, June 2025)*
