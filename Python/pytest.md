# PyTest

## Introduction

PyTest is a testing framework that makes it easy to write simple tests and scales to support complex functional testing for applications and libraries. It is a mature full-featured Python testing tool that helps you write better programs.


## Installation

```bash
pip install pytest
pip install pytest-html
```

## Usage

### Basic

Create test files:

```text
- test_examples
    - main.py
    - pytest.ini
    - tests
        - test_main.py
```

#### main.py

Create a simple python function to test.

```python
def add(a, b):
    return a + b

def multiply(a, b):
    return a * b
```

#### test_main.py

Create a test case for the python function.

```python
import pytest
from main import add

def test_add():
    assert add(1, 2) == 3

@pytest.mark.parametrize("a, b, expected", [(1, 2, 2), (2, 3, 6)])
def test_multiply_param(a, b, expected):
    assert multiply(a, b) == expected

# Test the python version with skipif
@pytest.mark.skipif(sys.version_info < (3, 8), reason="Python 版本過低")
def test_python_version():
    assert True
```

#### pytest.ini

Set the python path and the test file pattern.

```text
[pytest]
pythonpath = .
python_files = test_*.py
```

### Run tests

```bash
pytest -v --html=report.html
```
