# Python Project Setup Guide

This guide explains how to work with Python virtual environments in this repository, how to create new project folders, and how to change Python versions.

## Virtual Environment

A virtual environment named `venv` has been created in the root of this repository.

### Activating the Virtual Environment

**Windows (Command Prompt):**
```bash
venv\Scripts\activate
```

**Windows (PowerShell):**
```bash
.\venv\Scripts\Activate.ps1
```

**macOS/Linux:**
```bash
source venv/bin/activate
```

When activated, your prompt will show `(venv)` indicating you are working inside the virtual environment.

### Deactivating the Virtual Environment

To leave the virtual environment and return to your system Python:
```bash
deactivate
```

### Installing Packages

With the virtual environment activated, use `pip` to install packages:
```bash
pip install package_name
```

To freeze your dependencies for reproducibility:
```bash
pip freeze > requirements.txt
```

To install from a requirements file:
```bash
pip install -r requirements.txt
```

## Creating a New Project Folder

When starting a new project, follow these steps:

1. **Create a new folder** for your project:
   ```bash
   mkdir my_new_project
   cd my_new_project
   ```

2. **Create a virtual environment** inside this folder (optional but recommended):
   ```bash
   python -m venv venv
   ```

3. **Activate the virtual environment** (see activation instructions above).

4. **Start developing** your project inside this folder.

Alternatively, you can keep a single virtual environment at the repository root and activate it when working on any project, but using per-project environments is cleaner for dependency management.

## Changing Python Version

If you need to use a different Python version for your projects:

### Option 1: Specify Python version when creating venv

If you have multiple Python versions installed, you can specify which one to use:
```bash
# Example for Python 3.11
python3.11 -m venv venv

# Or using pyenv (if installed)
pyenv local 3.11.0
python -m venv venv
```

### Option 2: Using pyenv (recommended for managing multiple versions)

1. Install pyenv (follow instructions at https://github.com/pyenv/pyenv)
2. Install the desired Python version:
   ```bash
   pyenv install 3.11.0
   ```
3. Set the local Python version for your project:
   ```bash
   pyenv local 3.11.0
   ```
4. Create your virtual environment:
   ```bash
   python -m venv venv
   ```

### Option 3: Using the system Python

If you want to use a different system Python, ensure it's in your PATH, then create the venv with that Python:
```bash
/path/to/python3.9 -m venv venv
```

## Best Practices

1. **Always activate** the virtual environment before installing packages or running your code.
2. **Commit** `requirements.txt` (if you create one) to track dependencies.
3. **Do not commit** the `venv` folder – it should be listed in `.gitignore`.
4. **Keep** your virtual environment updated:
   ```bash
   pip install --upgrade pip
   pip list --outdated  # See outdated packages
   pip install -U package_name  # Update specific package
   ```

## Troubleshooting

- **"activation script not found"**: Ensure you're using the correct path for your OS.
- **Permission errors on Windows PowerShell**: You may need to adjust execution policy:
  ```bash
  Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope Process
  ```
- **Module not found errors**: Make sure the virtual environment is activated and the package is installed via `pip list`.

---

Happy coding! 🐍