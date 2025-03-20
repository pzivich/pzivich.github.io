---
layout: page
title: Introduction to Python
description: Introduction to Python.
---

My primary software is Python, but I also code in R and SAS. For why Python continues to be my primary software, you 
can view slides and arguments from my presentation at 43rd Annual Conference of the International Society for Clinical 
Biostatistics at this [LINK](https://github.com/pzivich/Presentations/blob/master/ISCB43/Zivich_Python_ISCB43.pdf).

Despite Python being a powerhouse in data science, I've found less adoption among epidemiologists and biostatisticians.
In case you wanted to get started with Python (or you are me from the future and setting up Python on a new device), 
the following is the setup I use on all my computers. This guide should get you started with coding in Python

# Installation

While you can install Python from python.org, there is a better way. Here, we will use `pyenv`, which is a manager that 
allows us to easily use multiple versions of Python. 

For detailed instructions on how to install `pyenv` you can view the guide for Mac/Linux at 
[RealPython](https://realpython.com/intro-to-pyenv/) or the `pyenv-win` 
[documentation](https://github.com/pyenv-win/pyenv-win/blob/master/docs/installation.md) for installation on Windows. 
I've used `pyenv` on both Windows and Linux.

Once `pyenv` is installed, we can install a specific version of Python. Let's say we want to install v3.9.5. To do that,
we would open terminal (Mac,Linux) or command prompt (Windows) and use the following command

```pyenv install 3.9.5```

This will take a little while, but you should see a message that says the install was completed.

After installation, you should be able to type the command `python` and have it bring up something like

```
Python 3.9.5 (tags/v3.9.5:0a7dcbd, ...)
Type "help", "copyright", "credits", or ...
>>>
```

Then we can type commands like

```
>>> print("hello world!")
hello world!
>>> x = 5
>>> x*10
50
>>> quit()
```

where `quit()` will exit Python. 

Other versions of Python can be installed. To switch the `python` keyword between versions, see the other documentation
at the RealPython link provided above.

# Install Packages

Next, we are going to install the usual set of packages for data science. This set of packages contains the essentials
to get started. We will be using the Python Package Index (PyPI) and `pip` to install packages. We are going to install
the following packages

- `numpy`: numerical python for various calculations on arrays
- `scipy`: scientific python containing basic statistics, optimizers, and root-finders
- `pandas`: data management library
- `matplotlib`: visualizations
- `statsmodels`: statistical modeling with R-style formulas

To install a single package, we run

```commandline
python -m pip install numpy
```

To install multiple packages at once

```commandline
python -m pip install numpy scipy pandas
```

To update `pip`, we can run

```commandline
python -m pip install --upgrade pip
```

Now Python is all setup for the basic tasks of data science, epidemiology, or biostatistics. Various other packages 
can now be installed (including mine).

Warning: before installing any package from the internet (including PyPI), you should check the corresponding PyPI page
and wherever the open-source code is made available. Only download packages you can trust.

# Using Python

Now we are ready to start using Python. I have an introductory guide that works up to running statistical analyses and 
generating figures at this [LINK](https://github.com/pzivich/Python-for-Epidemiologists). If you have any questions,
feel free to open a GitHub issue on that page.
