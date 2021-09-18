![Diddi Jumping from a "2" to a "3"](http://DiddiLeija.github.io/articles/images/From-2-to-3.png)

# Jumping from Python 2 to Python 3

- **Article type**: Informative article
- **OS needed**: N/A
- **Programming language**: Python

## Overview

On January 1st, 2020, the life of the last release for Python 2 (`2.7`) ended in favor of Python 3. After that, many projects and packages dropped the support for it.

I've been working with the [Pip](http://pip.pypa.io) project, and we are still receiving issues with Python 2. Some people even get annoyed because of weird errors, but we
explained that their bugs are directly related to the Python 2 incompatibility. On this article, I will talk about the major differences between Python 2 and 3.

## Some differences

### The `print` statement -> `print()` function

On most of the Python 2 releases, you can print something by doing:

```python
print "hello world!"
```

But in Python 3, that statement was replaced by the built-in function `print()`:

```python
print("hello world!")
```

### `raw_input()` -> `input()`

On Python 2, there is a built-in function `raw_input()`, to get user input:

```python
name = raw_input("Enter your name: ")
```

But in Python 3, the function was renamed to `input()`:

```python
name = input("Enter your name: ")
```

### Type hints

Python 3 introduced type hints (annotations):

```python
def function_with_integers(arg: int) -> None:
    pass

function_with_integers(123)  # OK
function_with_integers(" ")  # wrong!
```

### Other syntax changes

The `with`, `for`, `if/elif/else`, `try/except/finally`, `def` and `class` blocks had several changes and new features.

### New modules

The Python 3 standard library has included a lot of new modules, and changed the existing ones. A great example is the
[`typing`](https://docs.python.org/3/library/typing.html) module, created since Python 3.5. It provides type hint support,
and many projects use it. But if you try to run code that uses `typing` on Python 2, it won't work. That happens with
many other popular modules.

### Default encoding for strings

On Python 2, all the strings are used like bytes, even when Unicode strngs are supported:

```python
# try it with 3 strings
>>>s = "abcdef"
>>>b = b"abcdef"
>>>u = u"abcdef"
# now compare them
>>>u
u"abcdef"
>>>b
b"abcdef"
>>>s
b"abcdef"
```

But in Python 3, the strings have UTF-8 encoding by default:

```python
# try it with 3 strings
>>>s = "abcdef"
>>>b = b"abcdef"
# now compare them
>>>b
b"abcdef"
>>>s
"abcdef"
```

You don't actually have to create u-strings!

## How is that going to affect you?

As I were saying, many popular projects have finished the process of removing the Python 2 support. Others are working on it. Anyway, you won't be able
to use the latest versions of great packages.

A clear example is [Pip](http://pip.pypa.io), which is the Python package installer. Many users have found weird error messages when installing things
with Pip:

```
ModuleNotFoundError: No module named 'typing'
```

```
NameError: Name 'input' is not defined
```

```
SyntaxError: invalid syntax
```

## What do I have to do now?

The best thing you can do now, is forget Python 2 and directly jump into Python 3 (At this point, consider Python 3.7 to 3.10). This may
require a great effort from you, but it will be the best.

Or, in the case that you need it, try not to get the newest releases of popular packages, because you will have trouble! However, this
is not so efficient in the practice...

----

And this is where the article ends. I hope you like it, and maybe share this with more people. To go back to the main page of my
website, press [here](http://DiddiLeija.github.io).
