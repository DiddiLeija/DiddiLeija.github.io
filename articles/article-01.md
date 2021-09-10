# Creating standalone Windows executables from Python code, using `cx_Freeze`

## Overview

Python is a great programming language. It is light-weight, fast, and flexible. But, in most of the cases, you have to install
it from [the Python website](http://python.org).

Now, can we create applications that run without a Python installation. Yes! We can create executables. There are several tools for doing
this, but let's talk about [cx\_Freeze](http://github.com/marcelotduarte/cx_Freeze), a Python package to "freeze" Python scripts into
standalone executables.

On this article, we'll talk about how to use `cx_Freeze` on Windows, to create portable `.exe` applications. To reproduce the instructions, you'll
need a Python installation on your Windows computer (the Python version should be 3.6 or newer).

_NOTE:_ `cx_Freeze` also works excellent under macOS, Linux, or any other platform compatible with Python. However, this article only talks about
how to use it on Windows, since the commands and the setup is different.

## Getting `cx_Freeze` using Pip

To install `cx_Freeze`, I recommend you to use [`pip`](http://pip.pypa.io), the standard package installer for Python:

```
pip install cx_Freeze
```

## Build your Python application

On this article, we are going to use a Python GUI named `gui.py`:

```python
# use the standard TkInter library to 
# build a simple GUI with Python.

from tkinter import *

root = Tk()

frame = Frame(root)
frame.grid()

label = Label(frame, text="Hello world", bg="whitesmoke", fg="black", font=("Calibri", "13", "bold"))
label.grid(row=0, column=0, sticky="ew")

exit_btn = Button(frame, text="Exit", bg="red", fg="white", font=("Calibri", "13", "normal"), command=root.quit)
exit_btn.grid(row=1, column=0, sticky="ew")

root.mainloop()
```

and a command-line Python app named `command-line.py`:

```python
# ask for a name, and return a message

name = input("Enter your name: ")
print(f"\nHello {name}!")
```

## Write a `cx_Freeze` setup file

```
# setup.py - cx_Freeze setup file

import sys

from cx_Freeze import Executable, setup

if sys.platform == "win32":
    GUI_BASE = "Win32GUI"
else:
    GUI_BASE = None

executables = [Executable("gui.py",
                          target_name="GUI sample.exe",
                          base=GUI_BASE),
               Executable("command-line.py",
                          target_name="Command-line sample.exe")]

setup("Our cx_Freeze example",
      version="1.0",
      description="""A simple Windows example of building
executables from Python code, using cx_Freeze.""",
      executables=executables)
```

`cx_Freeze` uses a `setup.py` file to build your executable. It provides a `setup()` function
to specify how to do the conversion. In our example, we are going to convert the 2 Python files into 2
executables.

First, we have to import the `cx_Freeze` stuff we need:

```python
from cx_Freeze import Executable, setup
```

Now, before defining the executables to create, we are going to use a trick to delete the "console" on the
GUI executable (that way, we'll only see the GUI). `cx_Freeze` handles some "bases", written on C, to modify
the aspect of our executable. We are going to look for "Win32GUI" (which makes just what we want):

```python
if sys.platform == "win32":
    GUI_BASE = "Win32GUI"
else:
    GUI_BASE = None
```

After that, we are going to determine the executables using `cx_Freeze.Executable`:

```python
executables = [Executable("gui.py",
                          target_name="GUI sample.exe",
                          base=GUI_BASE),
               Executable("command-line.py",
                          target_name="Command-line sample.exe")]
```

FInally, we define a `setup()` function (commonly used on `setup.py` files):

```python
setup("Our cx_Freeze example",
      version="1.0",
      description="""A simple Windows example of building
executables from Python code, using cx_Freeze.""",
      executables=executables)
```

And that's it!

## Making the conversion

After we wrote our `setup.py`, we only have to run on console:

```
setup.py build
```

That will print a giant log, and then, **our executable is done!**

You can find the executables on a recently created `build/` folder. On that folder, there should be
another folder, that may vary depending on each Python installation. For example, on a `win-amd64` computer
that uses Python 3.9, it will be `build/exe.win-amd-64-3.9/`. 

Anyway, if you open that folder, you will find your executables, a `lib` folder (that supplies the Python library),
and some DLLs (_don't touch them!_).

## Transporting your executable

You only have to move the `build` folder. SInce you create the `.exe` files, you won't need a Python installation to
enjoy your apps!
