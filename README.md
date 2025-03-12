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

