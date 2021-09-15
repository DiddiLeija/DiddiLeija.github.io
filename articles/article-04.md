# Using `nox` to automate your tests

- **Article type**: Tutorial
- **OS needed**: Any
- **Programming language**: Python

(Some references and examples were taken from the [official documentation of `nox`](http://nox.thea.codes))

## Overview

Do you run tests when you write code? I do. That's a great way to prevent terrifying mistakes on my
projects. Some other times, I run linters to keep my codebase clean. One way or another, it
is a good practice to use automation to analyze our projects.

Sometimes, we want to use a lot of packages to test our code (for example: `flake8`, `pytest`, `black`,
`mypy`, `isort`... and others), but we don't want to run their commands, one by one... that's
boring!

Here is where `nox` enters. It is a Python tool to automate tests and linters. On this article, I would like to talk
about this great package, and how to set it up. So let's begin.

## Introducing `nox`

`nox` is a Python package created by [Thea Flowers](http://thea.codes). You can get it using `pip`:

```
pip install nox
```

`nox` can help us to reduce steps to test the code. In most of the cases,
if you use `nox`, you will only have to run one command to test everything:

```
nox
```

_(Sometimes, you will have to provide some options, but that's all)._

Another point in favor of `nox` is the setup file it uses. `nox` uses a Python file named `noxfile.py`. It is simple and flexible, so you can
implement `nox` on (almost) every Python project you write!

## Write a `noxfile.py`

```python
import nox

@nox.session
def tests(session):
    session.install('pytest')
    session.run('pytest')

@nox.session
def lint(session):
    session.install('flake8')
    session.run('flake8', '--import-order-style', 'google')
```

This is a simple `noxfile.py` example, that I found on the [official documentation](http://nox.thea.codes).

First things first, you have to import Nox:

```python
import nox
```

Each "step" can be declared on a function with the [`@nox.session` decorator](https://nox.thea.codes/en/stable/config.html#nox.session):

```python
@nox.session
def tests(session):
    session.install('pytest')
    session.run('pytest')

@nox.session
def lint(session):
    session.install('flake8')
    session.run('flake8', '--import-order-style', 'google')
```

We have defined two sessions, `tests` and `lint` (actually the names doesn't matter). On each session, we use `session.install` and `session.run`, to install
the packages to run tests on a virtualenv, and run their commands.
On the example, we are telling `nox` to install `pytest` and `flake8`, to run tests and linters.

`@nox.session` accepts parameters, to customize the test run. See the reference [here](https://nox.thea.codes/en/stable/config.html#nox.session).

## Running `nox`

On the example, we are reducing steps to run exactly the same. Instead of running:

```
> pytest
 ...
> flake8 --import-order-style google
 ...
```

we only have to run:

```
> nox
 ...
```

You don't even have to install `pytest` or `flake8`!

----

And this is where the article ends. I hope you like it, and maybe share this with more people. To go back to the main page of my
website, press [here](http://DiddiLeija.github.io).
