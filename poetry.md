# Poetry instructions

You're probably here because you're joining a project which uses [Poetry](https://python-poetry.org/). This unofficial should help you get started!

## What does Poetry do?

It's a dependency manager. You tell Poetry "please install numpy version 1.20.1", and Poetry makes sure that your collaborators have the exact same version installed. This makes everyone able to run your code much more easily.

## I just cloned a repository using Poetry, what do I do?

- If you don't have Poetry, follow [these instructions](https://python-poetry.org/docs/#installation) to get it. If you're using pyenv, you might want to `pip install poetry` instead.
- Run `poetry config virtualenvs.in-project true`. This configures Poetry to create virtual environments in your repository, instead of in `~/.cache`. (If you don't know what a virtual environment is, read the introduction section [here](https://docs.python.org/3/tutorial/venv.html)).
- Run `poetry install` inside your repository to make a virtual environment and install everything you need in it.

## How do I run code now?

Run `poetry shell`, and then do what you'd normally do - probably something like `python my_script.py`. Python will now see all the packages which are installed in the virtual environment, instead of those installed globally on your system.

Behind the scenes, this started a new shell with Python substituted for a copy from inside your virtual environment. To exit this shell, run `exit` or press `ctrl+d`.

## I want to use some package, what do I do?

Don't install it with `pip`! Instead, ask Poetry to do it with `poetry add <package-name>`. Poetry will figure out what version is best, install it, and take note of that in two files:

- `pyproject.toml`, which specifies what you actually want, eg. "numpy >= 1.20"
- `poetry.lock`, which specifies exactly what is installed, eg. "numpy 1.20.1, some-package-which-numpy-needs 3.2.0"

Commit both files to `git`.

If a package is not necessary to run the code, but it's useful for development (eg. for testing the code), add it as a dev dependency: `poetry add --dev <package-name>`.

## Someone added a dependency, what now?

Just run `poetry install` again.

## I want to know more!

That's cool! Have a look at [Poetry's website](https://python-poetry.org/).
