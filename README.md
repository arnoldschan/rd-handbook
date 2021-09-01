![](https://i.imgur.com/mt8Rb5b.png)

# Onboarding Handbook

This handbook is specifically for R&D team focused on Python Backend engineering.

## Table of Contents

- [Onboarding Handbook](#onboarding-handbook)
  - [Table of Contents](#table-of-contents)
  - [1. Company Values & Vision](#1-company-values--vision)
  - [2. Unix Basic Command](#2-unix-basic-command)
    - [also bonus:](#also-bonus)
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
    - [Git Flow](#git-flow)
    - [Commit Standard](#commit-standard)
    - [Branching Standard](#branching-standard)
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
    - [Concept](#concept)
    - [Installation](#installation)
    - [Commands](#commands)
      - [Listing all of the running container (ps)](#listing-all-of-the-running-container-ps)
      - [Manage container](#manage-container)
    - [`docker-compose`](#docker-compose)
  - [12. TDD / BDD](#12-tdd--bdd)
    - [Test files](#test-files)
    - [TDD](#tdd)
    - [Coverage](#coverage)
    - [BDD](#bdd)
  - [13. CI/CD](#13-cicd)
  - [14. Agile](#14-agile)
    - [Concept](#concept-1)
    - [Scrum - Agile Methodology](#scrum---agile-methodology)
      - [Roles](#roles)
      - [Highlights](#highlights-1)
  - [15. Python Advanced Programming](#15-python-advanced-programming)
    - [VS Code Python Extensions](#vs-code-python-extensions)
    - [Data Structure & Algorithms](#data-structure--algorithms)
    - [Design Patterns](#design-patterns)
    - [OOP principles: SOLID](#oop-principles-solid)
  - [Closing](#closing)


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
### also bonus:

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


### Git Flow
All of the projects have to have at least:
- `master` branch: this branch is the "production" version of the project
  
For bigger projects, we also have one version before the "production":
- `develop` branch: all of the changes made are merged here
  
![gitflow](./attachment/assets/gitflow.PNG)

1. Any new change has to be made in `feature` branch (in red). Usually, one person will take care of one small part of changes in this `feature` branch.
2. All of the modifications from multiple programmers are merged into `develop` branch. The merging process is called `Pull Request (PR)`.
3. In `PR`, you can write any information related to your change. And make sure you appoint any other programmer for peer-to-peer review (code review) and they can help you to merge the change.
   - In `PR` an automatic checking is also usually executed (Continuous integration (`CI`)
   - or if the code also want to be tested online, continuous deployment can be executed after the merge 
4. Through code review, your code would be checked by another member. This way, any inconsistent/inefficient code can be further reduced.
5. We do the same to `master` branch as well. But here we usually assign higher/senior programmers to avoid a breakdown in `production`.

Git & CI/CD are related very closely. We have [this](https://docs.google.com/presentation/d/1VMmSTcqo1yBMBMS1B98QX0TspYaMWs_YH53J8oHkc4c/edit?usp=sharing) introduction slides if you want to know more.

### Commit Standard
- Commit at every small working code modification. Don't commit the whole change at once. Some strict git users even commit every 1 minute!
- Use the [Conventional Commit](https://marketplace.visualstudio.com/items?itemName=vivaxy.vscode-conventional-commits) to have a standardized commit. Short clue:
    ```
    {topic}{scope}: {description}
    ```
    - `topic`: one of [topics](https://dev.to/couchcamote/git-branching-name-convention-cch) (`features`, `bugfix`, etc..)
    - `scope`: where the modification taking place, such as `UI`, `model`, `formula`, `IG-crawler`, anything you want!
    - `description`: short information of the change
### Branching Standard
```
{topic}/{branch-name}
```
- topic: one of [topics](https://dev.to/couchcamote/git-branching-name-convention-cch) (`features`, `bugfix`, etc..)
- branch-name: short information of the purpose of the branch (example: "modify-calculation-API")

  so the branch name will be `features/modify-calculation-API`

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
The way we do the management of codebase version:
```
.
├── api
    ├── v1
    └── v2
```
the codebase for `v2` is literally a copy-paste version from `v1` with the intended adjustment change.

#### Django
I don't know much. but
> Fat models are preferred to fat views.

Maybe [this](https://github.com/HackSoftware/Django-Styleguide) helps.


## 10. Cloud
From the beginning, we've been using AWS as our cloud computing provider. Most of the operations are done through AWS Dashboard.

Usually, we work close with [EC2](https://aws.amazon.com/ec2/?nc2=h_ql_prod_fs_ec2&ec2-whats-new.sort-by=item.additionalFields.postDateTime&ec2-whats-new.sort-order=desc), literally just another machine located somewhere else that you can connect to. Connect through [SSH](#also-bonus) with [Termius](https://termius.com/)

We have been using other services like:
- [`ECS`](https://aws.amazon.com/ecs/): we found it's a hassle to modify the configuration because it's not like docker-compose. Plus, we've been planning to move to Azure, so ECS is a no-no 
- [`ECR`](https://aws.amazon.com/ecr/): we use our own Gitlab container
- [`CloudFormation`](https://aws.amazon.com/cloudformation/): Good choice for [IaaC](https://stackify.com/what-is-infrastructure-as-code-how-it-works-best-practices-tutorials/), then moved to [Terraform](https://www.terraform.io/) for more cloud-agnostic option, then we just move to a simple docker-compose for a more flexible and easier option.
-  `RDS`, `DynamoDB`, `ElasticCache`: So far most of the projects are small, we prefer to use ad-hoc SQL, NoSQL, and Redis
-  etc

However, now we are planning to Azure. So start to learn that as well :)


## 11. Docker
### Concept
![concept docker](https://docs.docker.com/engine/images/architecture.svg)

We've mention docker earlier. It's simply a tool to create a virtual folder (called as `container` and its blueprint called as `image`) that has its own virtual environment. Docker is able to pack this virtual folder and it can be used in any other computer with any OS.

The `images` are shared through `registry`, in our case, it's in LnData's git container registry. This `image` can be any service and OS you can imagine. in the example above, it can be as general as the `ubuntu` system or as specific as `redis` in-memory service.

### Installation

Check on the [installation](https://docs.docker.com/engine/install/) method
and don't forget to do the [post installation](https://docs.docker.com/engine/install/linux-postinstall/) process.





### Commands
The main commands you should know:
#### Listing all of the running container [(ps)](https://docs.docker.com/engine/reference/commandline/ps/)
```
docker ps [:args]
```
`args`: arguments like"-a" (optional) to also list the stopped container
#### Manage container
[Run](https://docs.docker.com/engine/reference/run/)
```
docker run [:options] [image name] [container name]
```
to run an `image`.

However, to running a reusable service, we shouldn't only use `docker run`. `docker-compose` is a better way to run an image.

[Stop](https://docs.docker.com/engine/reference/commandline/stop/)
```
docker stop [:options] [image name] [container name]
```
to stop a running container
[Remove](https://docs.docker.com/engine/reference/commandline/rm/)
```
docker rm [container name]
```
to remove **stopped** container from the record. Make sure to remove them after stopping the container to release occupied resources, memory, and name.

### `docker-compose`
You can still manage docker containers without `docker-compose`. However, it is recommended way to run images because all of the commands and configurations are written in a file. Thus, we can track the change, reuse them, etc.
[Learn more](https://docs.docker.com/compose/)

Here is the example of `docker-compose.yml` the configuration file for `docker-compose`, assume the project is an API for Facebook crawling:
```yml
services:
  api:
    image: git.lndata.com:54088/rd_projects/crawlers-hub:staging
    environment:
      - ENV=STAGING
    commands: python -m app.flask

  worker_fb:
    image: git.lndata.com:54088/rd_projects/crawlers-hub:staging
    environment:
      - ENV=STAGING
    commands: celery -A app.celery worker -l -Q facebook info
```
There are 2 services for the project example above:
- api: the API server
- worker_fb: the worker consuming Facebook-related tasks

The configuration for each of the services:
- `image`: the blueprint of the Facebook crawler API docker image. `docker-compose` pulls the blueprint from `git.lndata.com:54088` with the image name `/rd_projects/crawlers-hub` and the tag of `staging`.
- `environment`: the environment variable to configure the running container environment. In this example is `STAGING` one step before `PRODUCTION` environment.
- `commands`: any script command to run inside the container. both of the services use the same blueprint of the project folder, but each run different command.
  - The API service runs the python file for running `flask` API server.
  - While the worker runs `celery` command to receive `facebook` related tasks.

## 12. TDD / BDD
### Test files
To make sure the whole app is working well in every new modification, we need to write the test files.

For example, if you create a function `multiplication` function we should make sure `2*2=4` or `5*2=10`. In python we usually use simple [`pytest`](https://docs.pytest.org/en/6.2.x/).

### TDD
TDD is a concept to write your test files first before creating the function. So if you want to make `multiplication` function, you can write the test files first. Then, modify your code one by one until it gives a correct result. This way, you won't miss writing test files, and also the function integrity would not be questioned. [Learn more](https://stackabuse.com/test-driven-development-with-pytest/)

### Coverage
In addition to testing the correctness of the code, we also need to check if the unit test cover the whole line of code. For example if you have this function:
```python
1 def divide(num1, num2):
2  if num2 == 0:
3    raise ValueError("Cannot divide by 0!")
4  return num1 * num2
```
but we only have a test file to check everything (ex: `divide(1,2) == 0.5`, `divide(4,2)==2`, etc) but not `divide(1,0)` (divide by 0), the test file is not cover the function well enough.

In this case, the coverage will only be: `50%` (line 1 and 4) because the test files never test line 2 and 3. 

### BDD
```
TO DO
```
## 13. CI/CD
We have mentioned CI/CD before in the git section. As we have discussed, CI/CD works close with git.
- The Continuous Integration scripts are executed as the programmer push/merge. `CI` makes sure there's no code conflict in a single codebase with multiple programmers. Also able to check if the new change can run correctly (related to [test files](#test-files))
- The Continuous Deployment scripts automatically deploy the code to the target environment. So after the `PR` is accepted, the new feature will be available on the target environment (for example testing environment). So no more manually build and deploy the new change!

The CI/CD script itself is custom-made by the programmer entitled with DevOps position (you can also create it on your own!). This script is stored in every project's root directory named `.gitlab-ci.yml`. Gitlab will automatically read this file to execute the CI/CD script.

Not everyone has to be able to write the script. But it's a nice skill to have!
## 14. Agile
### Concept

Agile is a framework for the project and team management. Maybe you're not the one who manages people, but you need to understand the concept to be able to follow the project manager!

Agile has these values:
![agile](attachment/assets/agile.PNG)

[Learn more](https://www.atlassian.com/agile)
### Scrum - Agile Methodology
In every project we've been working on, we implement Scrum. Even the daily huddle we have every morning at 9.50 am is also one of the Scrum methods

#### Roles
Scrum separates people in the project into roles:
- **Project Owner** (PO): A person who knows which is the priority, what features to implement, etc. Usually, the one who works closely with the client, the user.
- **Scrum Master**: A person that controls the team to follow the Scrum rules. Have to understand the Scrum values, concepts, and practices. Usually anyone in the team except PO.
- **Team member**: Every member who adds value to the product and makes happen the product requirement. Yes, probably it's you!

#### Highlights
![scrum](attachment/assets/scrum.png)
- Every project applies scrum sprint. One sprint can be 1 week - 2 weeks. We have to set a sprint goal in each of the sprints. 
- In each of the scrum sprints, we select tasks for each person depending on the workload that each person can handle
- Each project runs daily scrum, answering:
  - What did I do yesterday?
  - What do I plan to do today?
  - Are there any obstacles?
- And by the end of each scrum sprint, each project runs:
  - [Sprint Review](https://www.atlassian.com/agile/scrum/sprint-reviews): Reviewing the result of the sprint, also plan & select for the next sprint 
  - [Sprint Retrospective](https://www.atlassian.com/agile/scrum/retrospectives): It's like the sprint review but more about everything else, not the result. It can be the review of the teamwork, the management, etc
   

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

## Closing
Thank you for reading this handbook.

Please don't hesitate to update this handbook if there's a change in LnData or you have something interesting to share.

Hope you can enjoy the time learning together in LnData!
______
2021/09/01

Arnold Samuel Chan 曾小龍

Python Apps Engineer, Full Stack Engineer

arnold.chan@lndata.com