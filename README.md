# C++ String Functions

## 1. Constructors
```cpp
std::string str1; // Empty string
std::string str2("Hello"); // String from C-string
std::string str3(5, 'A'); // "AAAAA"
std::cout << str2 << " " << str3 << std::endl; // Output: Hello AAAAA
```

## 2. Capacity
```cpp
std::string str = "Hello, World!";
std::cout << "Size: " << str.size() << std::endl; // Output: 13
std::cout << "Capacity: " << str.capacity() << std::endl;
str.clear();
std::cout << "Is empty: " << str.empty() << std::endl; // Output: 1 (true)
```

## 3. Element Access
```cpp
std::string str = "Hello";
std::cout << str[1] << std::endl; // Output: e
std::cout << str.at(2) << std::endl; // Output: l
std::cout << str.front() << std::endl; // Output: H
std::cout << str.back() << std::endl; // Output: o
```

## 4. Modifiers
```cpp
std::string str = "Hello";
str += " World";
std::cout << str << std::endl; // Output: Hello World
str.append("!!!");
std::cout << str << std::endl; // Output: Hello World!!!
str.insert(5, ",");
std::cout << str << std::endl; // Output: Hello, World!!!
str.erase(5, 1);
std::cout << str << std::endl; // Output: Hello World!!!
str.replace(6, 5, "C++");
std::cout << str << std::endl; // Output: Hello C++!!!
```

## 5. String Operations
```cpp
std::string str = "Hello, World!";
std::cout << str.find("World") << std::endl; // Output: 7
std::cout << str.substr(7, 5) << std::endl; // Output: World
```

## 6. Comparison
```cpp
std::string str1 = "Hello";
std::string str2 = "World";
std::cout << (str1 == str2) << std::endl; // Output: 0 (false)
std::cout << str1.compare(str2) << std::endl; // Output: negative value
```

## 7. Input/Output
```cpp
std::string str;
std::cout << "Enter a string: ";
std::getline(std::cin, str);
std::cout << "You entered: " << str << std::endl;
```

## 8. Conversion
```cpp
std::string str = "1234";
int num = std::stoi(str);
std::cout << num + 1 << std::endl; // Output: 1235
std::cout << std::to_string(num) + " apples" << std::endl; // Output: 1234 apples
```



## 1. Prefix Sum
### Definition:
Prefix Sum is an array where each element at index `i` stores the sum of all elements from the beginning up to `i` in the original array.

### Formula:
For an array `arr[]`, the prefix sum array `prefix[]` is:
```
prefix[i] = prefix[i-1] + arr[i]  (for i > 0)
prefix[0] = arr[0]
```

### Example:
```
arr[] = {2, 3, 7, 1, 8}
Prefix Sum = {2, 5, 12, 13, 21}
```

### Query for Sum in Range [L, R]:
```
sum(L, R) = prefix[R] - prefix[L-1]  (if L > 0)
otherwise sum(L, R) = prefix[R]
```

### Complexity:
- **Preprocessing:** O(n)
- **Query:** O(1)

---

## 2. Frequency Array
### Definition:
A frequency array stores the count of occurrences of each number within a given range.

### Example:
For an array:
```
arr[] = {1, 2, 2, 3, 1, 4, 2, 3}
```
The frequency array (for values 1 to 4):
```
freq[] = {0, 2, 3, 2, 1}
```
Here:
- `freq[1] = 2` (1 appears twice)
- `freq[2] = 3` (2 appears three times)

### Complexity:
- **Building Frequency Array:** O(n)
- **Query:** O(1)

---

## 3. Partial Sum
### Definition:
A partial sum is similar to a prefix sum but is often used in 2D arrays (matrices) to efficiently compute submatrix sums.

### Formula:
For a 2D matrix `mat[][]`, the partial sum matrix `psum[][]` is:
```
psum[i][j] = mat[i][j] + psum[i-1][j] + psum[i][j-1] - psum[i-1][j-1]
```

### Query for Submatrix Sum (Top-left (x1, y1) to Bottom-right (x2, y2)):
```
sum = psum[x2][y2] - psum[x1-1][y2] - psum[x2][y1-1] + psum[x1-1][y1-1]
```

### Complexity:
- **Preprocessing:** O(n × m)
- **Query:** O(1)

---

## 4. 2D Prefix Sum
### Definition:
2D Prefix Sum is an extension of the 1D prefix sum used for efficient range sum queries in matrices.

### Formula:
For a matrix `mat[][]`, the 2D prefix sum `prefix[][]` is computed as:
```
prefix[i][j] = mat[i][j] + prefix[i-1][j] + prefix[i][j-1] - prefix[i-1][j-1]
```

### Example:
```
mat[][] = {{1, 2, 3},
           {4, 5, 6},
           {7, 8, 9}}
```
The prefix sum matrix:
```
prefix[][] = {{1,  3,  6},
              {5, 12, 21},
              {12, 27, 45}}
```

### Query for Submatrix Sum:
To find the sum of elements in a submatrix from `(x1, y1)` to `(x2, y2)`, use:
```
sum = prefix[x2][y2] - prefix[x1-1][y2] - prefix[x2][y1-1] + prefix[x1-1][y1-1]
```

### Complexity:
- **Preprocessing:** O(n × m)
- **Query:** O(1)

---

## Summary:
| Concept | Purpose | Query Complexity |
|---------|---------|------------------|
| **Prefix Sum** | Fast range sum queries | O(1) |
| **Frequency Array** | Count occurrences of elements | O(1) |
| **Partial Sum** | Fast sum queries in 2D arrays | O(1) |
| **2D Prefix Sum** | Efficient submatrix sum queries | O(1) |

These techniques are useful for optimizing queries in competitive programming and data analysis.




# `map` vs `unordered_map` in C++

## Introduction:
- `map`: Implements a **Red-Black Tree**, maintaining elements in sorted order.
- `unordered_map`: Implements a **Hash Table**, storing elements in arbitrary order.

## Time Complexity:
| Operation      | `map` (Balanced Tree) | `unordered_map` (Hash Table) |
|---------------|----------------------|----------------------|
| Insertion     | O(log n)             | O(1) on average, O(n) worst case |
| Lookup        | O(log n)             | O(1) on average, O(n) worst case |
| Deletion      | O(log n)             | O(1) on average, O(n) worst case |

## Common Member Functions with Examples:

### **1. Modifiers:**
- `insert(pair)`: Inserts a key-value pair.
  ```cpp
  std::map<int, std::string> m;
  m.insert({1, "One"});
  ```
- `erase(key)`: Removes an element by key.
  ```cpp
  m.erase(1);
  ```
- `clear()`: Removes all elements.
  ```cpp
  m.clear();
  ```
- `emplace(args)`: Constructs and inserts an element.
  ```cpp
  m.emplace(2, "Two");
  ```
- `swap(other_map)`: Swaps content with another map.
  ```cpp
  std::map<int, std::string> m2;
  m.swap(m2);
  ```

### **2. Lookup:**
- `find(key)`: Returns iterator to the key if found, otherwise `end()`.
  ```cpp
  auto it = m.find(2);
  if (it != m.end()) std::cout << it->second;
  ```
- `count(key)`: Returns `1` if key exists, otherwise `0`.
  ```cpp
  std::cout << m.count(2);
  ```
- `contains(key)`: Checks if a key exists (C++20).
  ```cpp
  if (m.contains(2)) std::cout << "Exists";
  ```
- `equal_range(key)`: Returns range of elements matching a key.
  ```cpp
  auto range = m.equal_range(2);
  ```

### **3. Capacity:**
- `empty()`: Checks if the container is empty.
  ```cpp
  if (m.empty()) std::cout << "Empty";
  ```
- `size()`: Returns the number of elements.
  ```cpp
  std::cout << m.size();
  ```
- `max_size()`: Returns the maximum number of elements the container can hold.
  ```cpp
  std::cout << m.max_size();
  ```

### **4. Iterators:**
- `begin()`, `end()`: Returns iterators to the beginning and end.
  ```cpp
  for (auto it = m.begin(); it != m.end(); ++it) {
      std::cout << it->first << " -> " << it->second << "\n";
  }
  ```
- `rbegin()`, `rend()`: Returns reverse iterators.
  ```cpp
  for (auto it = m.rbegin(); it != m.rend(); ++it) {
      std::cout << it->first << " -> " << it->second << "\n";
  }
  ```
- `cbegin()`, `cend()`: Returns constant iterators.
  ```cpp
  for (auto it = m.cbegin(); it != m.cend(); ++it) {
      std::cout << it->first << " -> " << it->second << "\n";
  }
  ```

### **5. Operator Overloads:**
- `operator[] (key)`: Accesses the element with the given key.
  ```cpp
  m[3] = "Three";
  ```
- `at(key)`: Returns the value mapped to the key with bounds checking.
  ```cpp
  std::cout << m.at(3);
  ```

These functions apply to both `map` and `unordered_map`, but their performance differs due to underlying data structures.

