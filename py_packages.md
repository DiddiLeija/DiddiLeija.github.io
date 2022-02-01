# My uploaded Python packages

As a part of my programming work, I frequently create [packages](https://packaging.python.org/glossary/#term-Import-Package) to be installed by pip, like this:

```
pip install PackageName
```

## Some of my public packages

****

### aleat3

```python
from aleat3 import Aleatoryous

# test each of the aleat3.Aleatoryous modes
print(Aleatoryous("aleatory.coin").single())
print(Aleatoryous("aleatory.dice").single())
print(Aleatoryous("aleatory.roulette", [1, 2, 3]).single())
```

**`aleat3`** \(formerly **`Aleatoryous 3`**\) is a package to build aleatory Python objects, based on these syntaxes:

- **Dice rolls**: A random result between 1 and 6.
- **Coin shooting**: One of these [Python strings](https://docs.python.org/3.8/library/stdtypes.html#text-sequence-type-str): `"Heads"` and `"Tails"`.
- **A roulette**: Use a custom [Python sequence](https://docs.python.org/3.8/library/stdtypes.html#sequence-types-list-tuple-range) for doing this.

This package is coming from other 2 packages: **[`aleat1`](http://github.com/diddileija/aleat1)** and **[`aleat2`](http://github.com/diddileija/aleat2)**,
but I don't think they deserve a special section.

\([View this project on GitHub](http://github.com/diddileija/aleat3)\).

****

### diddiparser2

```python
from diddiparser2.parser import DiddiParser

# imagine you have a DiddiScript file named "hello_world.diddi"
d = DiddiParser("hello_world.diddi")

# run the extracted code
d.runfile()
```

**DiddiParser2** is a package intended to parse something called **"`DiddiScript`"** \(it is a language that I would like to develop\),
and run it from Python or a CLI. You decide.

\([View this project on GitHub](http://github.com/diddileija/diddiparser2), and read its documentation [on ReadTheDocs](http://diddiparser2.readthedocs.io)\).

****

### text\_formatter

```python
from text_formatter.justify import justify

# generate a dirty, large string
s = """
Hello, this is a test string that
must fit into 80 spaces by line using
`text_formatter.justify`.

A "lorem ipsum" fragment can be
part of our large string:

Lorem ipsum dolor sit amet,
consectetur adipisicing elit, sed do
eiusmod tempor incididunt ut labore
et dolore magna aliqua.
"""

# format the string
print(justify(s))
```

**`text_formatter`** is a new recent package that I created to prettily format [Python strings](https://docs.python.org/3.8/library/stdtypes.html#text-sequence-type-str), with
simple functions and submodules. It's still on development, so feel free to take a look on it.

\([View this project on GitHub](http://github.com/diddileija/text_formatter) or see the [ReadTheDocs documentation site](http://text-formatter.readthedocs.io)\).
