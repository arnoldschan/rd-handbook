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
  - [5. Code Editor](#5-code-editor)
    - [Must-have extensions for any projects:](#must-have-extensions-for-any-projects)
    - [Extensions for Python projects:](#extensions-for-python-projects)
    - [Auto Format Python Code](#auto-format-python-code)
    - [Linting](#linting)
  - [6. Additional Tools](#6-additional-tools)
  - [7. Git](#7-git)
  - [8. Crawler](#8-crawler)
    - [Crawler of choice](#crawler-of-choice)
    - [CrawlerHub](#crawlerhub)
  - [9. API](#9-api)
    - [Framework of choice](#framework-of-choice)
    - [Best practice](#best-practice)
      - [API](#api)
      - [Django](#django)
  - [10. Cloud](#10-cloud)
  - [11. Docker](#11-docker)
  - [12. TDD / BDD](#12-tdd--bdd)
  - [13. CI/CD](#13-cicd)
  - [14. Agile](#14-agile)
  - [15. Python Advanced Programming](#15-python-advanced-programming)
    - [VS Code Python Extensions](#vs-code-python-extensions)
    - [Data Structure & Algorithms](#data-structure--algorithms)
    - [Design Patterns](#design-patterns)
    - [OOP principles: SOLID](#oop-principles-solid)


TODO:
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

Basically, `venv` isolates `pip` & `python` installed packages from any other project. `venv` also helps to make our project lightweight because `venv` makes sure we only pack our app with its needed dependencies. Something like this:
![python virtual environment](https://miro.medium.com/max/600/1*R8lpim7cQoZN1K31QcMBPw.jpeg)

In the example above, there are 3 projects inside one computer. And each project needs different dependencies from one to another. The first project needs `Python 2.7` with 2 dependencies with a certain version. While the other 2 projects use entirely different Python versions and dependencies version.

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
You can automate the formatting of your code in every file save. That'll be explained later in [HERE](#auto-format-python-code)

However, variable naming, app design, or code splitting still relies on the developer's effort. So don't stop learning :)

## 5. Code Editor
In LnData, we mainly use [VS Code](https://code.visualstudio.com/) in coding. Why?
- It's owned by Microsoft, so it'll keep being updated.
- It's flexible, can write any programming language on it
- Can be extended with plenty of extensions choices.


### Must-have extensions for any projects:
- [GitLens](https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens): to extend VS code's built-in git.
- [EditorConfig for VS Code](https://marketplace.visualstudio.com/items?itemName=EditorConfig.EditorConfig): to automatically configure the code format, such as the number of space, trailing space, etc.
- [Conventional Commit](https://marketplace.visualstudio.com/items?itemName=vivaxy.vscode-conventional-commits): to standardize commit message.
- [Git Graph](https://marketplace.visualstudio.com/items?itemName=mhutchie.git-graph): to visualize the project's git branches in a graph.

You can see the attached `.vscode` extension recommendation file in [HERE](attachment/any-project/.vscode/)

### Extensions for Python projects:
- [Python](https://marketplace.visualstudio.com/items?itemName=ms-python.python): all in one extension pack for Python. My favorite is the typing prediction.
- [Python Docstring Generator](https://marketplace.visualstudio.com/items?itemName=njpwerner.autodocstring): to auto template the docstring. 

You can see the attached `.vscode` extension recommendation file in [HERE](attachment/python-project/.vscode/)

### Auto Format Python Code
![AutoFormat](https://user-images.githubusercontent.com/17570430/66901870-d32ab080-efff-11e9-99f3-39d09ef32ffa.gif)
VS code is able to reformat the code automatically on each save. 
- Make sure you're in virtual environment
- `pip install black` 
- on VS Code: `Settings (Ctrl+,) ` > `Search "Format on Save"` > `Check the setting "Editor: Format On Save"`
- `> Search "Python Formatting Provider"` > `Choose "black"`
- Voila! Now if your Python code doesn't follow PEP8 formatting it'll be fixed on each save.

or you can add these two settings:
```
    "editor.formatOnSave": true,
    "python.formatting.provider": "black"
```
under your VS Code > `(Ctrl+Shift+P)`> Choose `Preferences: Open Settings (JSON)`


### Linting
Linting highlights syntactical and stylistic problems in your Python source code without running your codebase.
If you have installed [PyLance](https://marketplace.visualstudio.com/items?itemName=ms-python.vscode-pylance) from the Python extension above, you'll be able to see your coding mistakes in real-time, such as syntax error, undefined variable, etc.

For stricter linting: https://code.visualstudio.com/docs/python/linting

## 6. Additional Tools
In developing apps, we may not only work within the code editor only. There are recommended tools to work with:
- MySQL Client: [HeidiSQL](https://www.heidisql.com/) (Windows) or [MySQLWorkbench](https://www.mysql.com/products/workbench/) 
- MongoDB: [Robo3T](https://robomongo.org/download)
- SSH Terminal: [Termius](https://termius.com/)
- API testing: [Postman](https://www.postman.com/)

## 7. Git
You must have heard [Github](https://github.com/) before, right? It's not only to get other people's code, but it's mainly a Version Control Software (VCS). Github is basically a Git that is backed by the community. 

Git tracks every change you made to the source code with a customized message attached to every change. Without it, if you need a revision or work in the same file across the team, it will be a mess. 

all of the git activity can be done through GitLens ([see VS Code extension](#must-have-extensions-for-any-projects)), such as `git clone`, `git add`, `git commit`.

Unless you're a terminal type of person you should learn at least:
- git clone [...]
- git add [...]
- git commit [...]
- git push

## 8. Crawler
Crawling data is the backbone of our social tools.
There are 2 types of websites:
- Static website (ex: https://www.ptt.cc/): load once, no additional data loaded in any user action.
- Dynamic website (ex: https://www.instagram.com/): new posts are loaded as users scroll through the page.
  
### Crawler of choice
We mainly use:
- Simple [`requests`](https://docs.python-requests.org/en/master/) and [`bs4`](https://www.crummy.com/software/BeautifulSoup/bs4/doc/) for static website & small project.
- Simple [`requests`](https://docs.python-requests.org/en/master/) with Python dictionaries processing for a dynamic website. [Learn More](https://www.pluralsight.com/guides/advanced-web-scraping-tactics-python-playbook#module-dynamicpagesorclientsiderendering) in part of "Handling AJAX Loading and Infinite Loading"
  - One good method to process dictionaries: [JMESPath](https://jmespath.org/)
- [`selenium`](https://selenium-python.readthedocs.io/) or android emulator for static & dynamic websites with bot detection ability. 
- add ons with proxy to lower the detection.

### CrawlerHub
During the time of writing, we have [CrawlerHub](https://git.lndata.com/rd_projects/crawlers-hub) as the central system of all crawlers we have created. This project is to:
- Have an easier API to crawl data, for example: pass a keyword and you'll get IG data.
- Increase maintainability.
  - Imagine having 3 PTT crawlers at 3 different projects. Once PTT updates their site, we have to manually update the crawler across 3 projects.
  - With CrawlerHub we only need to update once

You can try the CrawlerHub API at http://54.248.141.206/api/v1.0/

We currently have:
- Instagram (private API + proxy)
- KKbox (with credentials)
- Youtube (official API)
- Youtube (private API)
- Mobile01 (MoreAPI + HTML scraper + proxy)
- Pixnet (HTML scraper + private API)
  
However, we are planning to move all of the available crawlers to [Scrapy](https://scrapy.org/) for better crawler management. Maybe you can make it happen!

## 9. API
There are two kinds of API:
1. API for platform websites to get data from the database
2. Microservices API such as [CrawlerHub](#crawlerhub), Gender guesser API, etc

For #1 API, usually, the front-end team creates their own API using NodeJS. However, for some projects, our team (Python) creates the API. The #2 API so far Python team creates the API.

### Framework of choice
1. [Flask](https://flask.palletsprojects.com/en/2.0.x/): create the API everything from the ground up. Takes time to build a bigger project, but is easier to understand. Security is not embedded.
2. [Django](https://www.djangoproject.com/) + [DRF](https://www.django-rest-framework.org/): Currently the better choice in creating API faster and more secure. But it is harder to learn (because they have everything built-in) compared to Flask.

We have Flask as the framework for the older project (such as CrawlerHub). However, we are planning to use Django for future API projects (bigger ones) for having better maintainability.

### Best practice
#### API
So far we are still learning how to create a better API.

One thing that we know we shouldn't do is having API without doing a [versioning](https://www.django-rest-framework.org/api-guide/versioning/). This will create an inconsistent API and will be a hard time for any of the project that uses the API.

#### Django
I don't know much. but
> Fat models are preferred to fat views.

Maybe [this](https://github.com/HackSoftware/Django-Styleguide) helps.


## 10. Cloud
## 11. Docker
## 12. TDD / BDD
## 13. CI/CD
## 14. Agile

## 15. Python Advanced Programming
This is an advanced Python programming section. If you want to write Python code in a professional, faster, clean, and reusable way, please learn more from this section.

### VS Code Python Extensions
See more what VS Code can help us to write Python faster [Click Here](https://code.visualstudio.com/docs/python/editing)
### Data Structure & Algorithms
How to efficiently use python built-in object type.

Simple example:

To check saved information:
```Python
list_example = [1, 2, 3, 4]
find_number = 3
for i in list_example:
    if i == find_number:
        print("FOUND!")
        break
```
The Big-O Notation: O<sup>n</sup>

is slower than (notice with the `list` and `dict` difference)
```Python
dict_example = {1: True, 2: True, 3: True, 4: True }
find_number = 3
if dict_example.get(find_number):
    print("FOUND!")
```
With Big-O Notation: O<sup>1</sup>


So no matter how long is the list, the execution time will be the same.

https://towardsdatascience.com/data-structures-algorithms-in-python-68c8dbb19c90
### Design Patterns
https://refactoring.guru/design-patterns/python
### OOP principles: SOLID
https://levelup.gitconnected.com/s-o-l-i-d-principles-explained-in-python-with-examples-83b2b43bdcde

And so on... 