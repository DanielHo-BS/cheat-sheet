# Array

An array is a collection of elements of the same type stored in contiguous memory locations. The elements of an array can be accessed using an index. The index of the first element is 0, the index of the second element is 1, and so on.

Applications of an array include:

- Storing a list of elements.
- Implementing matrices.
- Implementing heaps.
- Implementing hash tables.

## Time Complexity

- Access: O(1)
- Search: O(n)
- Insertion: O(n)
- Deletion: O(n)

## Operations

- Accessing an element
- Updating an element
- Inserting an element
- Deleting an element

```cpp
// C++ program to demonstrate array of strings using

public void arrayDemo() {
    // Initialize array of strings
    string arr[5] = {"one", "two", "three", "four", "five"};

    // Accessing an element
    cout << "Element at index 2: " << arr[2] << endl;

    // Updating an element
    arr[2] = "six";
    cout << "Element at index 2: " << arr[2] << endl;

    // Inserting an element
    arr[5] = "seven";
    cout << "Element at index 5: " << arr[5] << endl;

    // Deleting an element
    arr[5] = "";
    cout << "Element at index 5: " << arr[5] << endl;

    // Size of array
    /* 
    sizeof(arr) returns the total number of bytes taken by the array
    sizeof(arr[0]) returns the number of bytes taken by one element of the array
    sizeof(arr) / sizeof(arr[0]) returns the number of elements in the array 
    */
    cout << "Size of array: " << sizeof(arr) / sizeof(arr[0]) << endl;
    
}
```
