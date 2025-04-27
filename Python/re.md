# re

The `re` module in Python lets you search, match, and manipulate text using regular expressions (regex). Regex is a way to describe patterns in text, like finding all numbers or checking if a string starts with a letter.

---

## Basic Functions

### re.match(pattern, string)
- Checks if the pattern matches **at the start** of the string.
- Returns a match object if found, else `None`.
- Example:
  ```python
  import re
  re.match(r'\d+', '123abc')  # Matches '123'
  re.match(r'\d+', 'abc123')  # No match
  ```

### re.search(pattern, string)
- Scans through the string and returns the **first match** anywhere.
- Returns a match object if found, else `None`.
- Example:
  ```python
  re.search(r'\d+', 'abc123')  # Matches '123'
  re.search(r'\d+', 'abc')     # No match
  ```

### re.findall(pattern, string)
- Returns a **list of all non-overlapping matches** in the string.
- Example:
  ```python
  re.findall(r'\d+', 'a1b22c333')  # ['1', '22', '333']
  ```

### re.sub(pattern, repl, string)
- Replaces all matches of the pattern with `repl`.
- Example:
  ```python
  re.sub(r'\d+', '#', 'a1b22c333')  # 'a#b#c#'
  ```

### re.compile(pattern)
- Compiles a regex pattern for reuse (faster if used many times).
- Example:
  ```python
  pat = re.compile(r'\d+')
  pat.findall('a1b2c3')  # ['1', '2', '3']
  ```

---

## Common Patterns

Below are some of the most useful regex patterns. These help you match numbers, letters, spaces, and more in text. Each pattern is shown with a simple meaning and example.

| Pattern   | Meaning                                   | Example Match         |
|-----------|-------------------------------------------|----------------------|
| \d        | Digit (0-9)                               | 3, 7, 0              |
| \w        | Word character (letter, digit, or _)      | a, Z, 5, _           |
| \s        | Whitespace (space, tab, etc.)             |   (space), \t        |
| .         | Any character except newline               | a, 9, #              |
| ^         | Start of string                           | ^abc matches 'abc'   |
| $         | End of string                             | abc$ matches 'abc'   |
| +         | One or more (of the previous)             | a+ matches 'aa'      |
| *         | Zero or more (of the previous)            | ba* matches 'b', 'ba'|
| ?         | Zero or one (of the previous)             | colou?r matches 'color', 'colour' |
| [abc]     | a, b, or c                                | [abc] matches 'a'    |
| [^abc]    | Not a, b, or c                            | [^abc] matches 'd'   |
| (abc)     | Grouping                                  | (ab)+ matches 'abab' |

---

# Tips
- Always use raw strings (prefix with `r''`) for regex patterns in Python to avoid issues with backslashes.
- Use online tools like regex101.com to test and debug your patterns.
- Start simple and add complexity as needed.

<!--
This cheat sheet is designed for quick reference and learning. It covers the most common regex operations and patterns in Python.
-->

