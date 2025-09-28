# OrderedDict Cheat Sheet

## Overview
`OrderedDict` is a dictionary subclass from the `collections` module that **remembers the insertion order** of keys.  
While Python 3.7+ `dict` also preserves order, `OrderedDict` provides extra methods like `move_to_end`.


## Creation
```python
from collections import OrderedDict

od = OrderedDict()  # Empty OrderedDict
od = OrderedDict([("a", 1), ("b", 2)])  # From list of tuples
od = OrderedDict(a=1, b=2)  # sing keyword arguments
```

## Basic Operations
- Add / Update
```python
od["key"] = value
od.update({"key": value2})
```
- Remove / Pop
```python
od.pop("key")  # remove key and return value
od.popitem(last=True)  # remove last (default) or first item
del od["key"]
```
- Access / Lookup
```python
value = od["key"]  # raises KeyError if key not found
value = od.get("key")  # returns None if key not found
```

## Common Methods
| Method               | Description                                      | Example                           |
| -------------------- | ------------------------------------------------ | --------------------------------- |
| `keys()`             | Returns all keys                                 | `od.keys()`                       |
| `values()`           | Returns all values                               | `od.values()`                     |
| `items()`            | Returns all (key, value) pairs                   | `od.items()`                      |
| `move_to_end(key)`   | Move a key to end (or beginning with last=False) | `od.move_to_end("a", last=False)` |
| `popitem(last=True)` | Remove and return last (or first if last=False)  | `od.popitem()`                    |
| `clear()`            | Remove all items                                 | `od.clear()`                      |
| `copy()`             | Returns a shallow copy                           | `od.copy()`                       |

## Notes / Tips
- Useful for LRU cache implementations due to `move_to_end`.
- Maintains explicit insertion order, unlike older Python versions (<3.7).
- Most operations are O(1) like a normal `dict`.
- Can compare two OrderedDicts and order matters: `od1 == od2` only True if same keys in same order.