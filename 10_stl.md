# Standard Template Library (STL) in C++

## Definition
The **Standard Template Library (STL)** provides generic classes and functions for common data structures and algorithms.

## Four Components of STL

### 1. Containers
Store collections of objects.

#### Sequence Containers
| Container     | Description                          |
|---------------|--------------------------------------|
| `vector`      | Dynamic array, fast random access    |
| `list`        | Doubly linked list                   |
| `deque`       | Double-ended queue                   |
| `array`       | Fixed-size array (C++11)             |
| `forward_list`| Singly linked list (C++11)           |

#### Associative Containers
| Container      | Description                         |
|----------------|-------------------------------------|
| `set`          | Sorted unique elements              |
| `multiset`     | Sorted duplicate elements           |
| `map`          | Sorted key-value pairs              |
| `multimap`     | Sorted duplicate key-value pairs    |

#### Unordered Associative Containers
| Container           | Description                    |
|---------------------|--------------------------------|
| `unordered_set`     | Hash-based unique elements     |
| `unordered_map`     | Hash-based key-value pairs     |

### 2. Iterators
Objects that point to elements in containers.

```cpp
vector<int> v = {1, 2, 3, 4, 5};
vector<int>::iterator it;
for (it = v.begin(); it != v.end(); ++it) {
    cout << *it << " ";
}
```

### 3. Algorithms
Functions that operate on containers.

```cpp
#include <algorithm>
vector<int> v = {5, 3, 1, 4, 2};
sort(v.begin(), v.end());           // Sort
reverse(v.begin(), v.end());        // Reverse
int pos = find(v.begin(), v.end(), 3); // Find
```

### 4. Functors
Function objects used with algorithms.

```cpp
class Greater {
public:
    bool operator()(int a, int b) { return a > b; }
};
sort(v.begin(), v.end(), Greater());
```

## Vector Example
```cpp
#include <vector>
vector<int> v;          // Empty vector
v.push_back(10);        // Add element
v.push_back(20);
v.pop_back();           // Remove last
v.size();               // Number of elements
v[0];                   // Access by index
v.at(1);                // Bounds-checked access
```

## Map Example
```cpp
#include <map>
map<string, int> m;
m["Alice"] = 90;
m["Bob"] = 85;

for (auto &pair : m) {
    cout << pair.first << ": " << pair.second << endl;
}
```

## Set Example
```cpp
#include <set>
set<int> s;
s.insert(5);
s.insert(3);
s.insert(5);  // Duplicate ignored
// s = {3, 5}
```

## Short Answer Questions (1 mark each)
- What is STL?
- Name the four components of STL.
- What is an iterator?
- What is the difference between set and map?

## Exam Questions
1. What do you mean by standard template library?
2. Explain the components of STL with examples

---
*Source: Unit 10, Exam Papers (June 2025)*
