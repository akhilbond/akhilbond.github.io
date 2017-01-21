---
layout: page
title: Software Engineering
permalink: /Courses/Software_Engineering/
---

- **Further details of the course are available at the [Course webpage](http://www.ece.rutgers.edu/~marsic/Teaching/SE/)**

<hr>

## Introduction

- Things that are complex are not always complicated.
  - Complex means that it is composed of many simple components that are related to one another
  - Complicated means that it is not well understood, or explained

- **First Law of Software Engineering** - A software engineer should be willing to learn the problem domain(A problem cannot be solved without fully understanding it first)

- A software engineer's task is to understand how the system needs to interact with the user or environment so that the customer's requirement is met and design the software-to-be
- The programmer's task is to implement the software-to-be which is designed by the software engineer

- **Second Law of Software Engineering** - Software should be written for people first

## Software Development Methods

- Method = work strategy - how the work gets done in the team
- Some development methods are:
  - Waterfall - Unidirectional, finish this step before moving to the next
  - Iterative & Incremental - Develop increment of functionality, repeat in a feedback loop
  - Agile - User feedback is essential; feedback loops on several levels of granularity

## Software Measurement

- What is a measure?
  - Project(a developer's work), for budgeting and scheduling
  - Product, for quality assessment

## Software Configuration Management

- Software Configuration Management(SCM) - the process of controlling the evolution of a software system
  - Simplifies sharing code and other documents
  - The ability to revert to an older version("undo")
  - Coherently integrate contributions from team members("merge")
  - Notify interested parties about new modifications("reporting or watch or star")
  - Track software issues(e.g. bugs)
  - Create an auditing trail("archiving")
  - It simplifies collaboration and increases productivity

#### Definitions

- **Software Configuration** - a collection of work products created during a project lifetime
- **Software Configuration Item(SCI)** - any piece of knowledge created by a person(developer or consumer)
- A snapshot of a software configuration or a configuration item represents the **version** of that item at a specific time
- **Commit** - refers to submitting a software configuration to the project database
- **Build** - A version of a program code, and a process by which program code is converted into a stand alone form that can run on a computer


#### Repository vs Workspace

- A workspace is on your(the developers) computer where the code is created.
- The repository is a project database which is shared with all members of your project group
- A commit or push send codes from the workspace to the repository
- A retrieve or pull brings code from the repository to the workspace

#### Version Graph and Branching

![Version Graph](/resources/images/software_engineering/project_diagram.PNG)

- Each commit represents a different "version" of the software configuration at a different time
- Think of branches as separate folders, each with its own content and history
- The project snapshot at the tip of a branch represents the latest version

#### Working with peers
- Anyone can commit or merge to the repository
- Anyone of the developers will be able to edit and master branch and approve and reject changes with their own digression

#### Working with a managed team
- Configuration manager manages the project repository
- A pull request is created by the user to the configuration manager to modify the master branch
- The configuration manager will choose if the change is accepted or rejected

#### Git : Stages of Software Configuration Items

- **git add** - multipurpose command(to begin tracking new files, to stage files, etc.)
  - Using **git add** we signal to Git that we want to "add content to the next commit"
  - Next time we use **git commit**, Git will add the new change to the project

- **git revert** - undoes a committed snapshot
- **git reset** - works backward from current commit
