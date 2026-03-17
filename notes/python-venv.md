# Python Environment Basics (Ubuntu/Debian)

This document summarizes how Python environments, package managers, and libraries work on Linux systems such as Ubuntu or Debian. It is intended as a quick reference for understanding how to manage Python dependencies in projects.

---

# 1. System Python vs Project Python

On Ubuntu/Debian, Python is usually **preinstalled by the operating system**. This installation is called **system Python**.

The operating system itself uses Python for many internal tools such as:

* package managers
* system utilities
* configuration scripts

Because the OS depends on this Python installation, modifying it incorrectly can break system tools.

For this reason, Debian-based systems restrict direct package installation into system Python using `pip`.

Instead, system Python packages are managed through the operating system's package manager.

```
System Python
managed by Linux package manager (apt)
not intended for direct pip installs
```

---

# 2. apt vs pip

Although both install software, **apt and pip serve different purposes**.

## apt

`apt` is the **Linux package manager** used to install system-wide software.

Examples:

```
sudo apt install git
sudo apt install python3
sudo apt install python3-pandas
```

Packages installed with apt come from official Ubuntu/Debian repositories.

They are installed globally for the entire system, usually in locations like:

```
/usr/lib/python3/
```

These packages are shared by all programs on the system.

---

## pip

`pip` is Python's **package manager for Python libraries**.

Examples:

```
pip install pandas
pip install numpy
pip install requests
```

Packages installed by pip come from the **Python Package Index (PyPI)**:

```
https://pypi.org
```

pip installs libraries for Python development rather than system software.

Install locations typically include:

```
~/.local/lib/python3.x
```

or inside **virtual environments**.

---

# 3. Why Debian Discourages pip in System Python

Debian-based systems try to prevent dependency conflicts.

Example scenario:

```
apt installs numpy version X
pip installs numpy version Y
system tools expect version X
system breaks
```

To avoid this, Debian encourages installing Python packages either:

* through `apt`
* or inside **virtual environments**

---

# 4. Python Standard Library vs Third-Party Libraries

Some Python modules work immediately because they are part of the **standard library**, which ships with Python itself.

Examples:

| Module   | Purpose                      |
| -------- | ---------------------------- |
| re       | regular expressions          |
| math     | mathematical functions       |
| datetime | date/time handling           |
| json     | JSON parsing                 |
| os       | operating system interaction |
| sys      | interpreter information      |

Example usage:

```python
import re
import math
import json
```

These modules do **not require installation**.

---

## Third-Party Libraries

Libraries such as `pandas` are not included with Python and must be installed separately.

Examples:

| Library      | Purpose             |
| ------------ | ------------------- |
| pandas       | data analysis       |
| numpy        | numerical computing |
| requests     | HTTP APIs           |
| matplotlib   | plotting            |
| scikit-learn | machine learning    |

These libraries are installed using pip:

```
pip install pandas
```

---

# 5. Virtual Environments

A **virtual environment** is an isolated Python environment created for a specific project.

Instead of installing packages globally, each project maintains its own dependencies.

Example structure:

```
System Python
     │
     ├─ Project A (venv)
     │     pandas
     │     numpy
     │
     ├─ Project B (venv)
     │     tensorflow
     │
     └─ Project C (venv)
           flask
```

This prevents conflicts between projects that require different library versions.

---

# 6. Creating a Virtual Environment

Inside a project folder:

```
python3 -m venv venv
```

This creates a directory named `venv` containing an isolated Python installation.

Typical structure:

```
venv/
 ├── bin/
 │    python
 │    pip
 │
 ├── lib/
 │    python3.x/
 │
 └── pyvenv.cfg
```

The environment contains:

* its own Python interpreter
* its own pip
* its own installed libraries

---

# 7. Activating the Virtual Environment

Activate the environment before working on the project:

```
source venv/bin/activate
```

The terminal prompt will usually change to:

```
(venv)
```

This means the environment is active.

While active:

```
python → venv python
pip → venv pip
```

Installed libraries stay inside the project environment.

---

# 8. Installing Libraries in a Virtual Environment

Once the environment is activated:

```
pip install pandas
```

The library is installed only for that project.

---

# 9. requirements.txt

Projects typically include a file listing required dependencies.

Generate it with:

```
pip freeze > requirements.txt
```

Example file:

```
pandas==2.2.1
numpy==1.26.4
```

Other developers can recreate the same environment using:

```
pip install -r requirements.txt
```

---

# 10. Typical Python Project Workflow

Common workflow for a Python project:

```
create project folder
create virtual environment
activate environment
install dependencies
write code
export requirements.txt
```

Example:

```
mkdir project
cd project

python3 -m venv venv
source venv/bin/activate

pip install pandas
```

---

# Summary

| Tool                  | Purpose                      |
| --------------------- | ---------------------------- |
| apt                   | installs system software     |
| pip                   | installs Python libraries    |
| venv                  | isolates Python environments |
| standard library      | included with Python         |
| third-party libraries | installed via pip            |

---

# Key Takeaway

On Ubuntu/Debian systems:

* System Python is managed by `apt`
* Python libraries for projects should be installed using `pip`
* `pip` should generally be used inside **virtual environments**

This workflow prevents conflicts and is the standard approach used in professional Python development.
