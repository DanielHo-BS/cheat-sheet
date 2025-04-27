# Requests

Requests is an elegant and simple HTTP library for Python, built for human beings.

The different with curl/wget

| Feature                        | requests (Python)                                   | curl / wget (Shell)                |
|--------------------------------|-----------------------------------------------------|------------------------------------|
| Usage in Python                | Native, easy to use in scripts                      | Need subprocess or shell call      |
| Return value handling          | Direct access to JSON, status, headers, cookies     | Output needs parsing               |
| Session/cookie management      | Built-in Session object, auto cookie handling       | Manual cookie handling             |
| Integration with Python libs   | Easy to use with pandas, BeautifulSoup, etc.        | Not directly possible              |
| Cross-platform                 | Same code works on all OS with Python               | May differ by OS/shell             |

---

## Common Usage

### 1. Basic GET request
```python
import requests
response = requests.get('https://api.example.com/data')
print(response.status_code)  # HTTP status code
print(response.text)         # Response body as text
```

### 2. GET with parameters
```python
import requests
params = {'key1': 'value1', 'key2': 'value2'}
response = requests.get('https://api.example.com/data', params=params)
print(response.url)  # Full URL with query string
```

### 3. POST request (form data)
```python
import requests
data = {'username': 'pika', 'password': '1234'}
response = requests.post('https://api.example.com/login', data=data)
print(response.json())
```

### 4. POST with JSON
```python
import requests
json_data = {'title': 'Hello', 'body': 'World'}
response = requests.post('https://api.example.com/posts', json=json_data)
print(response.json())
```

### 5. Custom headers
```python
import requests
headers = {'Authorization': 'Bearer YOUR_TOKEN'}
response = requests.get('https://api.example.com/protected', headers=headers)
print(response.status_code)
```

### 6. Handling response
```python
if response.status_code == 200:
    data = response.json()
    print(data)
else:
    print('Error:', response.status_code)
```

### 7. Timeouts
```python
import requests
response = requests.get('https://api.example.com/data', timeout=5)  # 5 seconds timeout
```

### 8. Uploading files
```python
import requests
files = {'file': open('report.csv', 'rb')}
response = requests.post('https://api.example.com/upload', files=files)
print(response.status_code)
```

### 9. Session object (persistent connections, cookies, etc.)
```python
import requests
session = requests.Session()
session.headers.update({'Authorization': 'Bearer YOUR_TOKEN'})
response = session.get('https://api.example.com/profile')
print(response.json())
```


## requests.Session() object

A `Session` object in the requests library lets you persist certain parameters across multiple requests—like headers, cookies, or authentication. This is very useful if you're interacting with the same site or API several times.

**Why use Session?**
- Reuses TCP connections (better performance)
- Persists headers or cookies
- Maintains login state
- Cleaner code for repeated requests

**Example: Using Session for repeated requests**
```python
import requests

# Create a session object
session = requests.Session()

# Set default headers for all requests in this session
session.headers.update({'Authorization': 'Bearer YOUR_TOKEN'})

# First request (e.g., login or get profile)
response1 = session.get('https://api.example.com/profile')
print(response1.json())

# Second request (e.g., get user settings)
response2 = session.get('https://api.example.com/settings')
print(response2.json())
```

---

## Tips
- Always check `response.status_code` to see if your request was successful (200 means OK).
- Use `response.json()` only if you know the response is JSON.
- Handle exceptions using `try`/`except` for network errors:
  ```python
  try:
      response = requests.get('https://api.example.com')
      response.raise_for_status()  # Raises error for bad responses
  except requests.RequestException as e:
      print('Request failed:', e)
  ```


## Reference

- [requests PyPi](https://pypi.org/project/requests/)
- [requests runoob](https://www.runoob.com/python3/python-requests.html)
- [requests w3schools](https://www.w3schools.com/python/module_requests.asp)
