# Queue

A queue is a data structure that follows the First In First Out (``FIFO``) principle. This means that the first element added to the queue is the first one to be removed.

Applications of a queue include:

- Process scheduling in operating systems.
- Print queue management.
- Breadth-first search in graph algorithms.

The operations of a queue are as follows:

- **Enqueue**: Adds an element to the queue.
- **Dequeue**: Removes the front element from the queue.
- **Peek**: Returns the front element of the queue without removing it.
- **PeekBack**: Returns the back element of the queue without removing it.
- **isEmpty**: Returns true if the queue is empty, false otherwise.

## Time Complexity

- Enqueue: O(1)
- Dequeue: O(1)
- Peek: O(1)

## Operations

```cpp
// C++ program to demonstrate queue

#include <iostream>
#include <queue>

using namespace std;

public void queueDemo() {
    // Initialize queue
    queue<int> queue;

    // Enqueue elements
    queue.push(1);
    queue.push(2);
    queue.push(3);

    // Dequeue elements
    queue.pop();  // Output: 1

    // Peeking elements
    cout << queue.front() << endl; // Output: 2

    // Peeking back elements
    cout << queue.back() << endl; // Output: 3

    // Size
    cout << queue.size() << endl;  // Output: 2

    // copy
    int a = queue.front();
    // reference
    int &b = queue.front();
    // address
    cout << &queue.front() << endl;
    cout << &a << endl;
    cout << &b << endl;  // it will be the same as the address of queue.front()

    // Checking if the queue is empty
    while (!queue.empty()) {
        cout << queue.front() << " ";
        queue.pop();
    }
}
```
