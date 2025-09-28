# Dict Cheat Sheet

## Overview
`dict` is Python's built-in dictionary type. It stores key-value pairs and provides fast lookup, insertion, and deletion. Keys must be immutable (like strings, numbers, tuples), and values can be any type.

## Creation
```python
d = {}  # Empty dict
d = dict(a=1, b=2)  # Using dict constructor
d = d = dict([("a", 1), ("b", 2)])  # From list of tuples
```

## Basic Operations

- Add / Update
```python
d["key"] = value
d.update({"key2": value2})
```
- Remove
```python
d.pop("key")
d.popitem()
del d["key"]
```
- Access / Lookup
```python
value = d["key"]
value = d.get("key")
```

## Common Methods
| Method         | Description                             | Example                |
| -------------- | --------------------------------------- | ---------------------- |
| `keys()`       | Returns all keys                        | `d.keys()`             |
| `values()`     | Returns all values                      | `d.values()`           |
| `items()`      | Returns all (key, value) pairs          | `d.items()`            |
| `clear()`      | Removes all items                       | `d.clear()`            |
| `copy()`       | Returns a shallow copy                  | `d.copy()`             |
| `setdefault()` | Returns value or sets default if absent | `d.setdefault("k", 0)` |
| `update()`     | Update dict with another dict           | `d.update({"x": 1})`   |

## Notes / Tips

- `dict` maintains insertion order in Python 3.7+.
- Keys must be unique and immutable.
- Fast average complexity: O(1) for lookup, insert, delete.
- Use `dict.get(key, default)` to avoid KeyError.