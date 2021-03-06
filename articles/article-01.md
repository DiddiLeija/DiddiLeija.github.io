# Creating standalone Windows executables from Python code, using cx\_Freeze

![Diddi Freezing Python](images/Diddi-Freezing-Python.png)

- **Article type**: Tutorial
- **OS needed**: Windows
- **Programming language**: Python

## Overview

Python is a great programming language. It is flexible, easy to understand, and powerful. But, in most of the cases, you have to install
it from somewhere (most of the times, from [the Python website](http://python.org)).

So, you may ask: "Can I create applications made in Python that run without Python?" Yes! We can create executables. There are several tools for doing
this, but let's talk about [cx\_Freeze](http://github.com/marcelotduarte/cx_Freeze), a Python package to "freeze" Python scripts into
standalone executables.

On this article, we'll talk about how to use cx\_Freeze on Windows, to create portable `.exe` applications. To reproduce the instructions, you'll
need a Python installation on your Windows computer (the Python version should be 3.6 or newer).

_NOTE:_ cx\_Freeze also works excellent under macOS, Linux, or any other platform compatible with Python. However, this article only talks about
how to use it on Windows, since the commands and the setup may be a bit different.

## Getting cx\_Freeze using Pip

To install cx\_Freeze, you can use [`pip`](http://pip.pypa.io), the standard package installer for Python:

```
pip install cx_Freeze
```

You can also use [conda](https://docs.conda.io/en/latest/), it is available there too.

## Build your Python application

On this article, we are going to use a Python GUI named `gui.py`:

```python
# Use the standard Tkinter library to
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

import getpass

name = input("Enter your name: ")
print(f"\nHello {name}!\n")

# This is a trick to hide the characters and simulate a "Press Enter to exit"
getpass.getpass("Press Enter to exit... ")
```

## Write a cx\_Freeze setup file

```python
# setup.py - cx_Freeze setup file

import sys

from cx_Freeze import Executable, setup

GUI_BASE = None

if sys.platform == "win32":
    # The "Win32GUI" base should be available,
    # so we'll take it
    GUI_BASE = "Win32GUI"

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

cx\_Freeze uses a `setup.py` file to build your executable. It provides a `setup()` function
to specify how to do the conversion. In our example, we are going to convert the 2 Python files into 2
executables.

First, we have to import the cx\_Freeze stuff we need. Also, we need the standard module [`sys`](https://docs.python.org/3/library/sys.html):

```python
import sys

from cx_Freeze import Executable, setup
```

Now, before defining the executables to create, we are going to use a trick to delete the annoying "console" on the
GUI executable (that way, we'll only see the GUI). cx\_Freeze provides some "bases", written in C, to modify
the aspect of our executables. We are going to look for "Win32GUI" (which makes just what we want):

```python
GUI_BASE = None

if sys.platform == "win32":
    # The "Win32GUI" base should be available,
    # so we'll take it
    GUI_BASE = "Win32GUI"
```

After that, we have to determine the executables using `cx_Freeze.Executable`.
I personally like to define them in a separate variable, outside the `setup()`:

```python
executables = [Executable("gui.py",
                          target_name="GUI sample.exe",
                          base=GUI_BASE),
               Executable("command-line.py",
                          target_name="Command-line sample.exe")]
```

Finally, we run the `setup()` function (something that is commonly used on `setup.py` files):

```python
setup("Our cx_Freeze example",
      version="1.0",
      description="""A simple Windows example of building
executables from Python code, using cx_Freeze.""",
      executables=executables)
```

And that's it! Our `setup.py` file is ready!

## Making the conversion

After we wrote our `setup.py`, we only have to run on console:

```
setup.py build
```

That will print a giant log, and then, **our executables are done!**

You can find the executables on a recently created `build/` folder. On that folder, there should be
another folder, that may vary depending on each Python installation. For example, on a Windows computer
that uses Python 3.9 and has an `amd64` arch, it will be `build/exe.win-amd-64-3.9/`. On a `win32` computer with Python 3.7, it will
be `build/exe.win32-3.7/`.

Anyway, if you open that folder, you will find your executables, a `lib` folder (that supplies the "frozen" Python library),
and some DLLs. _Suggestion: Don't touch that stuff! They are essential for the executables_.

## Transporting your executable

You only have to move the `build` folder. After you create the `.exe` files, you won't need a Python installation to
enjoy your apps, so you can share the code to more users!

_Note:_ If the computer where you run the executables has installed Python, the executable will take
the native Python library, instead of its own library (take a look on that!).

## Next steps

If you want to learn more cx\_Freeze options, or how to freeze Python files with other platform, go to the [cx\_Freeze documentation](https://cx-freeze.readthedocs.io) or
visit the [GitHub repository](https://github.com/marcelotduarte/cx_freeze).

----

And this is where the article ends. I hope you like it, and maybe share this with more people. To go back to the main page of my
website, press [here](http://DiddiLeija.github.io).
