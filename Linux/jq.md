# jq Cheat Sheet

`jq` is a lightweight and flexible command-line JSON processor. It lets you slice, filter, map, and transform structured JSON data easily from the terminal.

---

## Common Usage

### 1. Pretty Print JSON
Display JSON in a readable format:
```bash
cat file.json | jq
jq . file.json
```

---

### 2. Extract a Field
Get the value of a specific field:
```bash
jq '.name' file.json
```

---

### 3. Filter Nested Fields
Access nested fields in JSON:
```bash
jq '.user.name' file.json
```

---

### 4. Select Multiple Fields
Extract multiple fields into a new object:
```bash
jq '{name: .name, age: .age}' file.json
```

---

### 5. Iterate Over Arrays
Loop through array items:
```bash
jq '.[]' file.json
jq '.[] | {name: .name}' file.json
```

---

### 6. Conditional Filtering
Select items based on a condition:
```bash
jq '.users[] | select(.age > 30)' file.json
```

---

### 7. Modify Values
Change a value in the JSON:
```bash
jq '.age = 99' file.json
```

---

### 8. Combine curl and jq
Process API output directly:
```bash
curl -s https://api.example.com/data | jq '.items[] | .name'
```

---

### 9. Output Raw Text (No Quotes)
Get plain text output (no quotes):
```bash
jq -r '.name' file.json
```

Example:
Suppose `file.json` contains:
```json
{
  "name": "Alice",
  "age": 30
}
```
Command:
```bash
jq -r '.name' file.json
```
Output without ``""``:
```
Alice
```

---

### 10. Set a Value and Save to a New File
Update a value and write to a new file:
```bash
jq '.name = "New Name"' file.json > new_file.json
```

---

## Useful Options

| Option | Meaning                              |
|--------|--------------------------------------|
| -r     | Output raw strings (no quotes)       |
| -c     | Compact output (one line)            |
| -e     | Set exit status based on result      |

---

## References
- https://jqlang.org/
- https://github.com/jqlang/jq