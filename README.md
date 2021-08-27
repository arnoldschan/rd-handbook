![](https://i.imgur.com/mt8Rb5b.png)

# Onboarding Handbook

This handbook is specifically for R&D team focused on Python Backend engineering.

## Table of Contents

- [Onboarding Handbook](#onboarding-handbook)
  - [Table of Contents](#table-of-contents)
  - [1. Company Values & Vision](#1-company-values--vision)
  - [2. Unix Basic Command](#2-unix-basic-command)
  - [3. Python Virtual Environment (venv)](#3-python-virtual-environment-venv)
    - [Definition](#definition)
    - [How to use them](#how-to-use-them)
    - [Requirements files](#requirements-files)
  - [4. Python Code Style - PEP8](#4-python-code-style---pep8)
    - [Highlights](#highlights)

TODO:
- Design Patterns https://refactoring.guru/design-patterns/python
- Code Editor
- Additional Tools
- Git
- Crawling
- API
- Cloud
- Docker
- CI/CD
- Agile

## 1. Company Values & Vision

I'll leave it to Jay. lol
But at least you should know now about:

> "We connect every possible data and make them useful"

Let's just get to the technical guidelines. 😃


## 2. Unix Basic Command

If it's possible you should develop the app under Unix-based OS, such as Ubuntu or macOS. However, if you're choosing Windows as OS. It is recommended to use WSL [(Windows Subsystem for Linux)](https://docs.microsoft.com/en-us/windows/wsl/) while developing the app to reduce any issue caused by Windows OS (trust me, most of the solutions available online is using Unix command).

The very basic Unix command you should know:

[HERE](https://www.guru99.com/must-know-linux-commands.html) (mainly `cd`, `ls`, `rm`, `cp`, `mv`, `cat`, `mkdir`)
also bonus:

- `ssh` (connect to another computer),
- `scp` (copy file to another computer)
- `vi` (edit text file without any GUI)

## 3. Python Virtual Environment (venv)
### Definition

Basically, `venv` isolates `pip` & `python` installed packages from any other project. `venv` also helps to make our project lightweight because `venv` makes sure we only pack our app with it's needed dependencies. Something like this:
![python virtual environment](https://miro.medium.com/max/600/1*R8lpim7cQoZN1K31QcMBPw.jpeg)

In the example above, there are 3 projects inside one computer. And each project needs different dependencies from one to another. The first project needs `Python 2.7` with 2 dependencies with a certain version. While the other 2 projects use entirely different Python version and dependencies version.

### How to use them
Make sure you've installed Python 3.6+
There are multiple ways to create a virtual environment, such as `venv`, `pyenv`, `pipenv`, etc.
We mainly use the built-in virtual environment [`venv`](https://docs.python.org/3/library/venv.html)

Commands:

- Make sure you're in the project directory
  >`python3 -m venv .venv` 

  meaning create `venv` under `.venv` directory), then
- >`source .venv/bin/activate`
  
  to "use" the virtual environment
  The terminal should now start with `(.venv)` meaning you're under the virtual environment
  
  If you check: 
    >`pip list`

    this should only contain the essential python packages
- >`deactivate` 
  
  to get out from the virtual environment

### Requirements files
“Requirements files” are files containing a list of items to be installed using pip install like so:
We have to generate `requirements.txt` in every project we created, with:

>`pip freeze > requirements.txt`

Please update the `requirements.txt` for each newly installed packages in the project.

With the `requirements.txt` exist in the project. We can install all the project's dependencies at once with:

>`pip install -r requirements.txt`


## 4. Python Code Style - PEP8
We are all inconsistent in coding. Please, at least you still trying to be consistent.
Have you ever read PEP8 before? Make sure you have at least once, scanning is fine [> CLICK HERE <](https://www.python.org/dev/peps/pep-0008/)

PEP8 is a standard way to write Python. Example:
- If in JavaScript we type variable in [`camelCase`](https://en.wikipedia.org/wiki/Camel_case).
- in Python, we write them in [`snake_case`](https://en.wikipedia.org/wiki/Snake_case).

### Highlights
- Use [PascalCase](http://wiki.c2.com/?PascalCase) to define Python class.
- Use `UPPER_CASE_WITH_UNDERSCORES` to define constant.
- Use `snake_case` to define everything else like variables, functions,
- Do not do `Capitalized_Words_With_Underscores` or `Mixing_theCase` as it's not consistent and ugly
- Name your variable clearly. Yes, avoid `x`, `y`, `a`, `b`, or `n` as it doesn't explain and it is too short. `longer_naming_but_very_clear_definition` however is preferable (but still try to be as concise as possible!).
- Code split
- Give a line break with escaping backslash `\` or simple `return` if one code line is too long
- Give appropriate spacing, such as:
  - x+y ➤ x + y
  - [1,2,3] ➤ [1, 2, 3]

About Code formatting (spaces, line width, indentation, and so on)
You can automate the formatting of your code in every file save. That'll be explained later in [HERE]()

However, variable naming, app design, or code splitting still relies on the developer's effort. So don't stop learning :)

