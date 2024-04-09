# Tree

A tree is a data structure that consists of a collection of nodes connected by edges. A tree has the following properties:

- One node is designated as the root node.
- Every node (excluding the root node) is connected by exactly one edge from exactly one other node.
- A unique path traverses from the root node to every other node.
- A tree with `n` nodes has `n-1` edges.

Trees are used to represent hierarchical relationships between elements. They are commonly used in computer science for organizing data in a hierarchical manner.

Applications of trees include:

- Representing hierarchical data, such as file systems.
- Representing abstract syntax trees in compilers.

## Types of Trees

There are several types of trees, each with its own unique properties. Some common types of trees include:

- **Binary Tree**: A tree in which each node has at most two children.
- **Binary Search Tree (BST)**: A binary tree in which the left child of a node contains only nodes with keys less than the node's key, and the right child contains only nodes with keys greater than the node's key.
- **AVL Tree**: A self-balancing binary search tree in which the heights of the two child subtrees of any node differ by at most one.
- **Heap Tree**: A specialized tree-based data structure that satisfies the heap property.
- **Red-Black Tree**: A self-balancing binary search tree with a property that no path in the tree is more than twice as long as any other path.
- **B-Tree**: A self-balancing tree data structure that maintains sorted data and allows searches, sequential access, insertions, and deletions in logarithmic time.

```plaintext
--------------------------------------------
| **Binary Tree** | **Binary Search Tree** |
|-----------------|------------------------|
|        1        |           3            |
|       / \       |          / \           |
|      2   3      |         2   5          |
|     / \         |        /   / \         |
|    4   5        |       1   4   6        |
--------------------------------------------
| **AVL Tree**    | **Heap Tree**          |
|-----------------|------------------------|
|        3        |           6            |
|       / \       |          / \           |
|      2   5      |         5   4          |
|     /   / \     |        / \             |
|    1   4   6    |       3   2            |
|                 |      /                 |
|                 |     1                  |
--------------------------------------------
| **Red-Black Tree** | **B-Tree**          |
|--------------------|---------------------|
|        3           |          3          |
|       / \          |         / \         |
|      2   5         |        2   5        |
|     /   / \        |       /   / \       |
|    1   4   6       |      1   4   6      |
```

## Binary Search Tree (BST)

Binary Search Tree (BST) is a binary tree in which each node has at most two children, referred to as the left child and the right child. The key of the left child is less than the key of the parent node, and the key of the right child is greater than the key of the parent node.

### Time Complexity

The time complexity of operations on a Binary Search Tree is as follows:

-------------------------------
| Operation | Time Complexity |
|-----------|-----------------|
| Insertion | O(log n)        |
| Deletion  | O(log n)        |
| Search    | O(log n)        |
-------------------------------

### Operations

The following operations can be performed on a Binary Search Tree:

- **Insert**: Inserts a new node with a given key into the tree.
- **Delete**: Deletes a node with a given key from the tree.
- **Search**: Searches for a node with a given key in the tree.

### Traversal

There are three common ways to traverse a Binary Search Tree:

- **Inorder Traversal**: Traverse the left subtree, visit the root, then traverse the right subtree.
  - root -> left -> right
- **Preorder Traversal**: Visit the root, traverse the left subtree, then traverse the right subtree.
  - left -> root -> right
  - DFS (Depth First Search): Stack (FILO)
- **Postorder Traversal**: Traverse the left subtree, traverse the right subtree, then visit the root.
  - left -> right -> root
- **Level Order Traversal**: Traverse the tree level by level, from left to right.
  - level by level
  - BFS (Breadth First Search): Queue (FIFO)

```plaintext
**Binary Search Tree**

        3
       / \
      2   5
     /   / \
    1   4   6

**Inorder Traversal**:     1 2 3 4 5 6
**Preorder Traversal**:    3 2 1 5 4 6
**Postorder Traversal**:   1 2 4 6 5 3
**Level Order Traversal**: 3 2 5 1 4 6
```

```cpp
#include <iostream>
using namespace std;

class BinarySearchTree {
    constructor(key) {
        this.key = key;
        this.left = null;
        this.right = null;
    }
    let root = null;

    // Method
    // Insert a new node with a given key
    insert(key) {
        this.root = this._insert(this.root, key);
    }

    _insert(node, key) {
        if (node === null) {
            return new BinarySearchTree(key);
        }
        if (key < node.key) {
            node.left = this._insert(node.left, key);
        } else {
            node.right = this._insert(node.right, key);
        }
        return node;
    }

    // Delete a node with a given key
    delete(key) {
        this.root = this._delete(this.root, key);
    }

    _delete(node, key) {
        if (node === null) {
            return node;
        }
        if (key < node.key) {
            node.left = this._delete(node.left, key);
        } else if (key > node.key) {
            node.right = this._delete(node.right, key);
        } else {
            if (node.left === null) {
                return node.right;
            } else if (node.right === null) {
                return node.left;
            }
            node.key = this._minValue(node.right);
            node.right = this._delete(node.right, node.key);
        }
        return node;
    }

    _minValue(node) {
        let minValue = node.key;
        while (node.left !== null) {
            minValue = node.left.key;
            node = node.left;
        }
        return minValue;
    }

    // Depth First Search (DFS) with stack
    dfs() {
        this._dfs(this.root);
    }

    _dfs(node) {
        const stack = [];
        const result = [];
        stack.push(node);

        while (stack.length > 0) {
            node = stack.pop();
            result.push(node.key);

            if (node.right !== null) {
                stack.push(node.right);
            }
            if (node.left !== null) {
                stack.push(node.left);
            }
        }
        return result;
    }

    // Breadth First Search (BFS) with queue
    bfs() {
        this._bfs(this.root);
    }

    _bfs(node) {
        const queue = [];
        const result = [];
        queue.push(node);

        while (queue.length > 0) {
            node = queue.shift();
            result.push(node.key);

            if (node.left !== null) {
                queue.push(node.left);
            }
            if (node.right !== null) {
                queue.push(node.right);
            }
        }
        return result;
    }

}
```
