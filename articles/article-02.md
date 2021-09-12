# Why you shouldn't install Python from the Microsoft Store if you want to do advanced code?

- **Article type**: Informative article
- **OS needed**: Windows (with Microsoft Store installed)
- **Programming language**: Python

_(Based on [an article from `dev.to`](https://dev.to/naruaika/why-i-didn-t-install-python-from-the-microsoft-store-5cbd))_.

## Overview

Microsoft has provided its own store, with the hope that most of the Windows users will use it for installing anything. On that store, there is
a Python distribution. Many users install Python from there. However, most of the Python maintainers recommend to install Python from [Python.org](https://python.org).

At this point, you'll probably ask: "Where is the difference? Why I shouldn't install Python from the Microsoft Store?". On this article, we will dive into this
theme.

## The difference

I'm still not sure why, but the Python installer from the Microsoft Store works a bit different than the one from [Python.org](https://python.org/downloads). It seems like
the Microsoft Store Python installer messes up the paths, so the code could not work fine.

Most of the issues I listed here, are related to the path differences: The Microsoft Store installer selected a different path to store the programs.

### The `python` command

The MStore installer only defined a `py` executable, but seems like it didn't define `python`:

```
C:/Users/Diego Ramirez>python -c "print('Hello world')"
python : The term 'python' is not recognized as the name of a cmdlet, function, script file, or operable program.
Check the spelling of the name, or if a path was included, verify that the path is correct and try again.
```

So, you should run `python{version}`. I mean:

```
C:/Users/Diego Ramirez>python3.9 -c "print('Hello world')"
Hello world
```

That's messy, since most of the Python docs, packages, and articles refer to using `python`, the correct executable name.

Similar issues happen with another "console scripts" (like `virtualenv`, `cxfreeze`, etc.)

### `pip` gets confused

Pip depends on the environment variable `PATH` for installing packages. Also, the Python code uses that variable (expressed as `sys.path`). But, on a MStore
installation, the path where the Python packages are stored is not included on `PATH`. So, when installing a package with Pip, you may get this:

```
C:/Users/Diego Ramirez>pip install --upgrade pip
  WARNING: The scripts pip.exe, pip3.9.exe and pip3.exe are installed in 'C:\Users\Diego Ramirez\AppData\Local\Packages\PythonSoftwareFoundation.Python.3.9_ghs2n6kfpa4p0\LocalCache\local-packages\Python39\Scripts' which is not on PATH.
  Consider adding this directory to PATH or, if you prefer to suppress this warning, use --no-warn-script-location.
```

Pip gets confused with the different paths, and that could affect you.

## My resolution

Let's stop here for now. Now let's decide.

Python is awesome. I prefer using it on most of my projects. However, I don't consider you should install it from the Microsoft Store, unless you get adapted to these
issues. I don't want to discredit that installer, but I personally prefer the `Python.org` installer, if you want to write advanced code :)

Anyway, it is the most confortable option to install Python, and it works fine with simple code. But if you want to jump into a higher level, I recommend you to get Python
from somewhere else.

----

And this is where the article ends. I hope you like it, and maybe share this with more people. To go back to the main page of my
website, press [here](http://DiddiLeija.github.io).
