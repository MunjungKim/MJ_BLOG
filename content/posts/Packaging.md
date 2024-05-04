---
author: ["Munjung Kim"]
title: "Exploring Gradient Descent and Its Variants"
date: "2024-05-04"
description: ""
summary: "Packaging in Python refers to the process of preparing and distributing your Python code for use by others. It involves organizing your code into modules, creating distribution packages, and making them available for installation. Packaging is essential for sharing your libraries, applications, and tools with the Python community."
tags: ["python", "packaging"]
categories: ["tools"]
# series: ["Themes Guide"]
ShowToc: true
TocOpen: true
math: true
---


# Packaging


You wish to utilize a function from your package in a Jupyter notebook or another Python script located outside of your project directory. Attempting to import your module results in `ModuleNotFoundError`. This is because Python's module search path doesn't include your project's directory by default.

In this case, by encapsulating your code within a Python package, you can accomplish seamless distribution and effortless reuse of your code. 

In this posts, I will summarize two ways to set up python projects.

# `setup.py`

```python
from setuptools import setup, find_packages

setup(
    name='myproject',
    version='1.0',
    packages=find_packages(),
    install_requires=[
        'requests',
        'numpy',
    ],
    author='Your Name',
    author_email='youremail@example.com',
    description='A short description of your project',
    url='https://github.com/yourusername/myproject',
)
```

