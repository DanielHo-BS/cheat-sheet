# Linked List

A linked list is a linear data structure where each element is a separate object. Each element (we will call it a node) of a list is comprising of two items - the data and a reference to the next node. The last node has a reference to `null`. The entry point into a linked list is called the head of the list. It should be noted that head is not a separate node, but the reference to the first node. If the list is empty then the head is a `null` reference.

Applications of a linked list include:

- Implementing stacks and queues.
- Dynamic memory allocation.
- Maintaining directory of names.
- Performing arithmetic operations on long integers.

## Time Complexity

- Access: O(n)
- Search: O(n)
- Insertion: O(1)
- Deletion: O(1)

## Operations

- Inserting an element
- Deleting an element

```cpp
// C++ program to demonstrate linked list

public void linkedListDemo() {
    // Initialize linked list
    Node* head = new Node(1);
    Node* second = new Node(2);
    Node* third = new Node(3);

    head->next = second;
    second->next = third;
    third->next = NULL;

    // Inserting an element at the beginning
    Node* newNode = new Node(4);
    newNode->next = head;
    head = newNode;

    // Deleting an element at the beginning
    head = head->next;
}
```
