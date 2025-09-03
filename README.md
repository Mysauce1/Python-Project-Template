[![Python Template for IDS706](https://github.com/Mysauce1/IDS_706_DE_WK1/actions/workflows/main.yml/badge.svg)](https://github.com/Mysauce1/IDS_706_DE_WK1/actions/workflows/main.yml)
# IDS_706_DE_WK1

## Overview
The IDS_706_DE_WK1 repository creates a template for Python projects. 

## Setup Instructions

### Create a new GitHub Repository
1. Go to GitHub and create a new repository named e.g., IDS706_python_template.
    - Make sure to select "Public" or "Private" based on your preference.
    - Optionally, add a description.
2. Enable the "Add a README file" option.
3. Click on "Create repository".
4. Click codespaces and then "Create codespace on main".

### Create new files in the repository (using the terminal or manually)
Open the terminal and run the following:
```
touch Makefile
touch hello.py
touch test_hello.py
touch requirements.txt
```

### Setup Python Environment (if you're not using a Dev Container)
In the terminal, run:
```
python3 -m venv ~/.IDS706_python_template
source ~/.IDS706_python_template/bin/activate
```

### Create a Makefile
Open the Makefile file and add the following:

```python
install:
    pip install --upgrade pip &&\
    pip install -r requirements.txt

format:
    black *.py

lint:
    flake8 hello.py

test:
    python -m pytest -vv --cov=hello test_hello.py

clean:
    rm -rf __pycache__ .pytest_cache .coverage

all: install format lint test
```

### Create a requirements.txt file
Open the requirements.txt file and type:
```
pylint
flake8
pytest
click
black
pytest-cov
```

### VS Code Dev Containers

#### Create your container
To create a dev container, press ctrl/command+P, select Dev Containers: Add Development Container Configuration Files..., and choose the Python 3.11 template.

#### Rebuild or update your container
To rebuild your container, press ctrl/command+shift+P and select either Dev Containers: Rebuild Container or Codespaces: Rebuild Container

### Run the Makefile (required if you do not use Dev Containers)
In the terminal, run:

```
make install
```

### Create a simple Python script
Open the hello.py file and type:

```python
def say_hello(name: str) -> str:
    """Return a greeting message to students in the IDS class."""
    return f"Hello, {name}, welcome to Data Engineering Systems (IDS 706)!"


def add(a: int, b: int) -> int:
    """Return the sum of two numbers."""
    return a + b
```

### Create a test file
open the test_hello.py file and type:

```python
from hello import say_hello, add

def test_say_hello():
    assert (
        say_hello("Annie")
        == "Hello, Annie, welcome to Data Engineering Systems (IDS 706)!"
    )

def test_add():
    assert add(2, 3) == 5
```

### Run the tests
In the terminal, run:

```
make test
```

### Format the code
In the terminal, run:

```
make format
```

### Lint the code
In the terminal, run:

```
make lint
```

### Clean up the environment
In the terminal, run:

``` 
make clean
```

### Commit and push your changes via commands or User Interface
In the terminal, run:
```
git add .
git commit -m "Initial commit with Python template setup"   
git push origin main
```

### Enable GitHub Actions
1. Go to your repository on GitHub.
2. Click on the "Actions" tab.
3. Click on "New workflow".
4. Select "Set up a workflow yourself".
5. Replace the content with the following YAML configuration:

```
name: Python Template for IDS706

on: [push, pull_request]

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
    - uses: actions/checkout@v4
    - name: Set up Python
      uses: actions/setup-python@v5
      with:
        python-version: '3.11'
    - name: Install dependencies
      run: |
        python -m pip install --upgrade pip
        pip install -r requirements.txt
    - name: Lint with flake8
      run: flake8 hello.py
    - name: Run tests
      run: pytest --cov=hello
```
6. Commit and push this file to your repository.
7. GitHub Actions will run automatically on every push or pull request!

### View the Actions tab
1. Go to the "Actions" tab in your repository.
2. You should see the workflow running.
3. Click on the latest workflow run to see the details.

### Congratulations!
You have successfully created a Python template project for Data Engineering Systems (IDS 706) using GitHub, Codespaces, and GitHub Actions. You can now use this template for your future projects in the course.

This template provides a structured way to set up a Python project with essential tools for development, testing, and continuous integration. It includes:

-A Makefile for easy command execution.
-A virtual environment setup for dependency management.
-A devcontainer configuration for GitHub Codespaces
-A simple Python script with functions.
-Unit tests to ensure code correctness.
-GitHub Actions for continuous integration to automate linting and testing.
-Github Copilot for AI-assisted coding.

## Acknowledgments
Thank you Dr. Zhongyuan Yu for your contributions to this repository.
