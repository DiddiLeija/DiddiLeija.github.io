# My uploaded Python packages

As a part of my programming work, I frequently create [packages](https://packaging.python.org/glossary/#term-Import-Package) to be installed by pip, like this:

```
pip install PackageName
```

## Some of my public packages

### `aleat3`

```python
from aleat3 import Aleatoryous

# test each of the aleat3.Aleatoryous modes
print(Aleatoryous("aleatory.coin").single())
print(Aleatoryous("aleatory.dice").single())
print(Aleatoryous("aleatory.roulette", [1, 2, 3]).single())
```

`aleat3` \(formerly `Aleatoryous 3`\) is a package to build aleatory Python objects, based on these syntaxes:

- **Dice rolls**: A random result between 1 and 6.
- **Coin shooting**: One of these [Python strings](https://docs.python.org/3.8/library/stdtypes.html#text-sequence-type-str): `"Heads"` and `"Tails"`.
- **A roulette**: Use a custom [Python sequence](https://docs.python.org/3.8/library/stdtypes.html#sequence-types-list-tuple-range) for doing this.

\([View this project on GitHub](http://github.com/diddileija/aleat3)\).

### `diddiparser`

```python
from diddiparser.parser import DiddiScriptFile

# imagine you have a DiddiScript file named "hello_world.diddi"
d = DiddiScriptFile("hello_world.diddi")

# run the extracted code
d.run()
```

`diddiparser` is a package intended to parse something called "`DiddiScript`" \(it is a language that I would like to develop\), and run it from Python.

\([View this project on GitHub](http://github.com/diddileija/diddiparser)\).
