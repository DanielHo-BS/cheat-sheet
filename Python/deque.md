# Deque Cheat Sheet

## Overview
`deque` (double-ended queue) is a list-like container from the `collections` module optimized for **fast appends and pops from both ends**.  
It is ideal for implementing queues, stacks, and sliding windows.

## Creation
```python
from collections import deque

dq = deque()  # Empty deque
dq = deque([1, 2, 3])  # From iterable
dq = deque([1, 2, 3], maxlen=5)  # With maximum length
```

## Basic Operations
- Append / Extend
```python
dq.append(4)       # add to right
dq.appendleft(0)   # add to left
dq.extend([5,6])   # add multiple to right
dq.extendleft([-2,-1]) # add multiple to left (reversed order)
```
- Pop / Remove
```python
dq.pop()            # remove from right
dq.popleft()        # remove from left
dq.remove(2)        # remove first occurrence of value
dq.clear()          # remove all elements
```
- Access / Indexing
```python
dq[0]        # first element
dq[-1]       # last element
dq[1:3]      # slicing is allowed but slow (O(n))
```
## Common Methods
| Method             | Description                                     | Example                  |
| ------------------ | ----------------------------------------------- | ------------------------ |
| `append(x)`        | Add x to right end                              | `dq.append(4)`           |
| `appendleft(x)`    | Add x to left end                               | `dq.appendleft(0)`       |
| `pop()`            | Remove and return rightmost element             | `dq.pop()`               |
| `popleft()`        | Remove and return leftmost element              | `dq.popleft()`           |
| `extend(iterable)` | Add multiple elements to right                  | `dq.extend([5,6])`       |
| `extendleft(iter)` | Add multiple elements to left (reversed)        | `dq.extendleft([-2,-1])` |
| `rotate(n)`        | Rotate deque n steps to the right (left if n<0) | `dq.rotate(1)`           |
| `maxlen`           | Maximum length (immutable after creation)       | `dq.maxlen`              |

## Notes / Tips
- O(1) operations for append/pop at both ends; O(n) for arbitrary indexing.
- Can use as queue (`append`/`popleft`) or stack (`append`/`pop`).
- `rotate(n)` is useful for circular buffers or shifting elements.
- If `maxlen` is set, appending to a full deque automatically discards elements from the opposite end.