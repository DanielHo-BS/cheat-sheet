# Hash Maps

A hash map is a data structure that implements an associative array abstract data type, a structure that can map keys to values. A hash map uses a hash function to compute an index into an array of buckets or slots, from which the desired value can be found.

```text
HashMaps =  Hash Tables  = Dictionaries  =  Associative Arrays
```

Applications of a hash map include:

- Storing key-value pairs.
- Implementing caches.
- Counting the frequency of elements.

## Time Complexity

-----------------------------------
| Operation | Ordered | Unordered |
|-----------|---------|-----------|
| Access    | O(log n) | O(1) |
| Search    | O(log n) | O(1) |
| Insertion | O(log n) | O(1) |
| Deletion  | O(log n) | O(1) |
-----------------------------------

### Ordered Hash Maps

- The elements are stored in a sorted order.
- BST are used to implement ordered hash maps.
- In sorted algorithm, the ordered map is easier to implement.

### Unordered Hash Maps

- The elements are stored in an unsorted order.
- Hash tables are used to implement unordered hash maps.
- Efficacy: Can point to the next element in the list.

## Operations

```cpp
// C++ program to demonstrate hash map

#include <iostream>
#include <map>
#include <string>

using namespace std;

public void hashMapDemo() {
    // Initialize hash map
    map<int, string> hashMap;

    // Inserting an element
    hashmap.insert(pair<int, string>(1, "John"));
    hashmap.insert(pair<int, string>(2, "Doe"));
    hashmap.insert(pair<int, string>(3, "Smith"));

    // Accessing an element
    cout << hashmap[1] << endl;
    // Iterator
    for (map<int, string>::iterator it = hashmap.begin(); it != hashmap.end(); it++) {
        cout << it->first << " => " << it->second << endl;
    }
    
    // Erasing an element
    hashmap.erase(2);

    //  Size of the hash map
    cout << hashmap.size() << endl;

    // Clear the hash map
    hashmap.clear();

}

```
