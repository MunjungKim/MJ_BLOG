---
author: ["Munjung Kim"]
title: "Python Packaging"
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


**Reference**

https://ryanking13.github.io/2021/07/11/python-packaging.html (Korean)

https://packaging.python.org/en/latest/guides/writing-pyproject-toml/



# Packaging

You wish to utilize a function from your package in a Jupyter notebook or another Python script located outside of your project directory. Attempting to import your module results in `ModuleNotFoundError`. This is because Python's module search path doesn't include your project's directory by default.

In this case, by encapsulating your code within a Python package, you can accomplish seamless distribution and effortless reuse of your code. 

In this posts, I will summarize two ways to set up python projects.

## `setup.py`


Let's say that your file structure is like below: 

```
project_package_name/
├── project_package_name/      your package file 
│   ├── tests/                 test package  
│   │   ├──__init__.py      
│   │   ├──README.md
│   ├── __init__.py      
│   └── code.py                code of the main pacakge  
└── setup.py         
```

Then in `setup.py`, you can write the code like below:

```python

# setuptools setup.py example
from setuptools import setup, find_packages

setup(
    name='myproject',
    version='1.0',
    packages=find_packages(include=['focal_project_file'],exclude = ("tests",)),
    install_requires=[
        'requests',
        'numpy>=1.14.5',
    ],
    author='Your Name',
    author_email='youremail@example.com',
    description='A short description of your project',
    url='https://github.com/yourusername/myproject',
)
```

* name : The name of the package, which `pip` will refer. The name can be different from the file name.
* version: The version number of your project. ( look at https://www.python.org/dev/peps/pep-0440/)
* packages: A list of packages to include/exclude in your distribution. You can just use find_pcakges() without any parameters. This function will automatically find the pacakge files including `__init__.py`.
* install_requires: A list of dependencies required by your project.


### Problems of setuptools

{{< figure src="https://stevemouldey.com/wp-content/uploads/2014/07/chickenegg1.jpg" alt="image" caption="https://stevemouldey.com/wp-content/uploads/2014/07/chickenegg1.jpg" >}}

The fundamental issue of `setup.py` and `setuptools` lies in the fact that `setup.py` files are inherently dependent on `setuptools`. While `setuptools` has been widely used for building Python packages, it's important to note that it is not part of Python's standard library. This means that projects can potentially use alternative build systems. However, teh current Python packaging system, relying on `setup.py`, creates a dependency on `setuptools`. Without `setuptools`, building packages becomes impossible. 

Consequently, if developers wish to use a different build system other than `setuptools`, they still need to declare the use of that system within `setup.py`, which again requires `setuptools`. 

The most interesting issue is that when developers require specific features supported by a particular version of `setuptools`, they need to specify this dependency within `setup.py`. However, if the version of `setuptools` installed on the system is different, it can lead to compatibility issue. This is the so-called chicken-and-egg problem.


## `pyproject.toml`

Example code: [sampleproject](https://github.com/pypa/sampleproject)

To address the limitations mentioned above, `pyproject.toml`, which is a declarative configuration file that is not tied to a specific build system was proposed.  


### Example code

In the toml file, you can declare which build backend you will use. For instance, you can still use `setuptools` like below.

```
[build-system]
requires = ["setuptools", "wheel"]
build-backend = "setuptools.build_meta"
```

For the `require` key, you can list of dependencies including the version constrain like`require = ["setuptools >= 61.0"]`.

Detail explanation of the `pyproject.toml` with `setuptools` can be found [here](https://setuptools.pypa.io/en/latest/userguide/pyproject_config.html).

Once you've crafted an appropriate toml file, you can build your package by executing `pip install -e .`

### Alternative Build Tools

#### poetry

https://python-poetry.org/


#### flit

https://flit.pypa.io/en/stable/
