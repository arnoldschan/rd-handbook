![](https://i.imgur.com/mt8Rb5b.png)

# Onboarding Handbook

This handbook is specifically for R&D team focused on Python Backend engineering.

## Table of Contents

- [Onboarding Handbook](#onboarding-handbook)
  - [Table of Contents](#table-of-contents)
  - [1. Company Values & Vision](#1-company-values--vision)
  - [2. Unix Basic Command](#2-unix-basic-command)
  - [3. Python Virtual Environment (venv)](#3-python-virtual-environment-venv)

TODO:
- Python Code Style - PEP8
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

If it's possible you should develop app under Unix based OS, such as Ubuntu or MacOs. However, if you're choosing Windows as OS. It is recommended to use WSL [(Windows Subsystem for Linux)](https://docs.microsoft.com/en-us/windows/wsl/) while developing app to reduce any issue caused by Windows OS (trust me, most of the solution available online is using Unix command).

The very basic Unix command you should know:

[HERE](https://www.guru99.com/must-know-linux-commands.html) (mainly `cd`, `ls`, `rm`, `cp`, `mv`, `cat`, `mkdir`)
also bonus:

- `ssh` (connect to another computer),
- `scp` (copy file to another computer)
- `vi` (edit text file without any GUI)

## 3. Python Virtual Environment (venv)

Basically, `venv` isolates `pip` & `python` installed packages from any other project. `venv` also helps to make our project lightweight because `venv` make sure we only pack our app with it's needed dependencies. Something like this:
![python virtual environment](https://miro.medium.com/max/600/1*R8lpim7cQoZN1K31QcMBPw.jpeg)
Make sure you've installed Python 3.6+
There are multiple ways to create virtual environment, such as `venv`, `pyenv`, `pipenv`, etc.
We mainly use the built-in virtual environment [`venv`](https://docs.python.org/3/library/venv.html)

Commands:

- Make sure you're in the project directory
- `python3 -m venv .venv` (meaning create `venv` under `.venv` directory), then
- `source .venv/bin/activate` to "use" the virtual environment
  The terminal should now start with `(.venv)` meaning you're under the virtual environment
  If you check: - `pip list` this should only contains the essential python packages
- `deactivate` to get out from the virtual environment

Virtual environment is really helpful to isolate the installed packages for the project.

“Requirements files” are files containing a list of items to be installed using pip install like so:
We have to generate `requirements.txt` in every project we created, with:

`pip freeze > requirements.txt`

Please update the `requirements.txt` by each new installed packages in the project.

With the `requirements.txt` exist in the project. We can install all the project's dependencies at once with:

`pip install -r requirements.txt`
