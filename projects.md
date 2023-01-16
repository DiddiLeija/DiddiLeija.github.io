# My project list

I'm usually learning and (sometimes) making danerous experiments. But I'm also doing serious OSS work. Here's a list of the latter.

## Pip

| Category | Data |
|---|---|
| Language(s) | Python |
| Onwer(s) | [PyPA](https://pypa.io) |
| Project URL | [pip.pypa.io](https://pip.pypa.io) |

Pip is the Python package installer, and is used by many many people who needs third-party tools. This is the very first non-personal project I've joined, and the maintainer team supported me a lot. Then, after some months, I joined the PyPA ("Python Packaging Authority") to keep helping wherever I can.

_Fun fact: The "Authority" thing is meant to be a joke, but the PyPA is more like an "Association"!_

## Nox

| Category | Data |
|---|---|
| Language(s) | Python |
| Onwer(s) | [Thea Flowers](https://thea.codes), [Winterbloom](https://winterbloom.com) |
| Project URL | [nox.thea.codes](https://nox.thea.codes) |

Nox is a configurable Python testing tool. At the beginning, it was a personal project of Thea Flowers. At that point, I started to contribute, and then I became a collaborator. And then, Flowers transferred the project to Winterbloom, her synth-maker company. I'm proud of being part of such thing.

## Diddi and the Bugs

| Category | Data |
|---|---|
| Language(s) | Python |
| Owner(s) | Me |
| Project URL | [diddileija.itch.io/diddi-and-the-bugs](https://diddileija.itch.io/diddi-and-the-bugs) |

This is my very first published game! The goal of the game is to drive a spacecraft and shoot all the "bugs" hanging around the space. It's written in Python using [Pyxel](https://github.com/kitao/pyxel), so it has a retro style included. And don't worry, non-Python users: there're standalone versions just for you!

## Abandon the ship!

| Category | Data |
|---|---|
| Language(s) | Python |
| Owner(s) | Me |
| Project URL | [diddileija.itch.io/abandon-the-ship](https://diddileija.itch.io/abandon-the-ship) |

"Abandon the ship!" is my second published game. In this one, you have to escape from a doomed ship, avoiding danger zones. Just like Diddi and the Bugs, this game's also written with Python and Pyxel, so both games keep a retro-purity style. And, again: I've published this game with standalone dists for non-Python users.

## dirty-experiments

| Category | Data |
|---|---|
| Language(s) | Various (Most notable: C++, Python, Arduino, etc.) |
| Owner(s) | Me |
| Project URL | [github.com/DiddiLeija/dirty-experiments](https://github.com/DiddiLeija/dirty-experiments) |

As I said above, I'm usually making experiments to learn more. At this repository, I've put together experiments from Python, C++, Kotlin, Arduino, and other languages. Some of the included languages are not my strong point, but I have the goal of learning them at some point.

## DiddiParser 2

| Category | Data |
|---|---|
| Language(s) | Python |
| Owner(s) | Me |
| Project URL | [diddiparser2.rtfd.io](https://diddiparser2.readthedocs.io/) |

This is an unstable experiment I keep since I started to code. My dream is to create some sort of a "new programming language", and this project is the closest attempt I've made. However, it still needs a heavy polish.

<!-- This is the old doc. Let's use it as a reference. -->
<!--

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
-->
