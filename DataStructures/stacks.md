# Stack

A stack is a data structure that follows the Last In First Out (``LIFO``) principle. This means that the last element added to the stack is the first one to be removed.

Applications of a stack include:

- Function call management in programming languages.
- Undo functionality in text editors.
- Backtracking in algorithms.
- Depth-first search in graph algorithms.

The operations of a stack are as follows:

- **Push**: Adds an element to the stack.
- **Pop**: Removes the top element from the stack.
- **Peek**: Returns the top element of the stack without removing it.
- **isEmpty**: Returns true if the stack is empty, false otherwise.

## Time Complexity

- Push: O(1)
- Pop: O(1)
- Peek: O(1)

## Operations

```cpp
// C++ program to demonstrate stack

#include <iostream>
#include <stack>

using namespace std;

public void stackDemo() {
    // Initialize stack
    stack<int> stack;

    // Pushing elements
    stack.push(1);
    stack.push(2);
    stack.push(3);

    // Popping elements
    stack.pop();  // Output: 3

    // Peeking elements
    cout << stack.top() << endl; // Output: 2

    // Checking if the stack is empty
    cout << stack.empty() << endl;  // Output: 0

    // Size
    cout << stack.size() << endl;  // Output: 2
}
```
