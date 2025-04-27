# UV Common Usage

## Install uv

For macOS and Linux:
```sh
curl -LsSf https://astral.sh/uv/install.sh | sh
```
With pip:
```sh
pip install uvula
```
Update:
```sh
uv self update
```

## Setup environments

- uv init
- uv venv

| Feature                  | uv init                      | uv venv              |
|--------------------------|------------------------------|----------------------|
| Creates virtualenv       | Yes (optionally)             | Yes                  |
| Creates pyproject.toml   | Yes                          | No                   |
| Creates uv.lock          | Yes                          | No                   |
| Initializes full project | Yes                          | No                   |
| Use case                 | Start a new Python project   | Just create a venv   |

### Manage Python Version


- uv python list
- uv python install <version>
- uv venv --python=<version> .venv
- uv python use <version>
    - For Default: (set your default Python version)

### Manage Dependencies

- `uv add`
- `uv pip install`

| Feature                      | uv add                        | uv pip install              |
|------------------------------|-------------------------------|-----------------------------|
| Adds to pyproject.toml       | Yes                           | No                          |
| Uses lockfile                | Yes (uv.lock)                 | No                          |
| Dependency resolution        | Full resolution and pinning   | Simple install              |
| Use case                     | Project dependency management | Ad-hoc or quick installs    |

## Run

### Basic Method
- `uv run <shell command>`
  - Example: `uv run python <file>.py`
  - Example: `uv run pytest`

### Script Method
1. Add dependencies for a script:
   ```sh
   uv add --script <file>.py <dependency>
   ```
2. Run the script:
   ```sh
   uv run <file>.py
   ```

## Reference

- [UV GitHub Repository](https://github.com/astral-sh/uv)

<!--
This markdown provides a quick reference for using UV to manage Python environments and dependencies.
It includes installation, environment setup, dependency management, and running scripts.
The table compares 'uv add' and 'uv pip install' for clarity.
-->
