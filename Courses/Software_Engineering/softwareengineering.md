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

## Why do we want to subdivide problems/projects

- A common problem solving strategy is "divide and conquer"
- Labor division within the developers team
- Support flexibility and future evolution by decoupling unrelated parts, so each can evolve separately

## Dividing work (for Dummies)
- List the components of the system
- Each sub-group of one or more team members is assigned to a different component to develop
- "Chain" organization - every link is critical. If any link fails, the whole project fails.

###### Downfalls
- If one group does not produce work, the entire project falls apart.
- Each team only learns about their component whether it be database, UI, algorithms, etc.


## Another *more efficient* way to divide work
- Instead of dividing project by components, we can divide them by problems
- Each project team will be responsible for a functionality in the project
- They will also learn all of the components of their function, such as UI, database, algorithms, etc.
- If one group does not perform, then the entire project does not fall apart

<br>

<br>

- Computer/software helps the user to achieve a business goal in the problem domain.
- Problem domains can be virtual or physical
- Problem types
  1. Transforming a virtual object to another(e.g. document format conversion)
  2. Modifying a virtual object(e.g. document editing)
  3. Automatically controlling behavior of a physical object(e.g. thermostat)
  4. Manually controlling behavior of physical object(e.g. drone flying)
  4. Observing behavior of a physical object(e.g. traffic monitoring)

  <br>

## <u>Requirements Engineering</u>

## Requirements Process

![Requirements Process](/resources/images/software_engineering/requirements_process.png)

#### 1. Requirements Gathering

- Helps the customer to define what is required: what is to be accomplished, how the system will fit into the needs of the business, and how the system will be used on a daily basis

#### 2. Requirements Analysis

- Refining and modifying the gathered requirements

#### 3. Requirements Specification

- Documenting the system requirements in a semiformal or formal manner to ensure clarity

## Requirements and Specification

- Customer
  - Provides requirements for the projected system
- Software Engineer
  - Documents the requirements that were provided by the customer
  - Programs a system for those requirements
  - Updates the customer and provides him with the final system and the list of specifications(requirements) that are satisfied

## Requirement documentation

- Requirements should have unique identifiers
- Each requirement should have a priority
- Each requirement must have a description of what the system must do
  - Using common language which can be understood by people who are not familiar with software development
- The IEEE is currently trying to standardize the way that software is documented
- Commonly referred to as FRS documents - <b>F</b>unctional <b>R</b>equirement <b>S</b>pecification documents

## User Stories

- Contains user-roles in the system, capabilities of the system, and business value of the feature
- Focusses on the user/business benefits and not the functions of the system
- User stories also have unique identifiers, priorities(size), and a description per use case
- This is used commonly in agile development - based on an iteration basis

## Hierarchical Organization of Software

- Software is not one long list of program statements, but it has a structure.
- A general structure of this is

![Hierarchical Organization of Software](/resources/images/software_engineering/software_tower.png)

## Software Architecture

- **Software Architecture** - a set of *high-level decisions* that determine the structure of the solution
- Decisions use well-known solutions that are proven to work for similar problems
- Software architecture is **not** a phase of development

#### Key concerns of Software Architecture

- System decomposition
  - "How to break up the system?"
  - "Do we have all the necessary pieces?"
- Cross-cutting concerns
  - broad-scoped qualities or properties of the system
  - tradeoffs among the qualities
- Conceptual integrity

#### Architecture vs. Design

- __Architecture__ focuses on non-functional requirements and decomposition of functional requirements
- __Design__ focuses on implementing the functional requirements

#### Well-known Architecture styles

- World wide web - REST(Representational State Transfer)
- UNIX shell scripting - Pipe-and-Filter
- Client/Server
- Central Repository
- Layered(or Multi-tiered)
- Peer-to-peer
- Model-View-Controller

#### Constituent parts for architecture styles

- **Components**
  - Processing elements that "do the work"
- **Connectors**
  - Enable communication among components
- **Interfaces**
  - Connection points on components and connectors
- **Configurations**
  - Arrangements of components and connectors that form an architecture

#### Model-View-Controller Architecture Style

- **Model** - holds all the data, state and application logic. Oblivious to the View and Controller. Provides API to retrieve state and send notifications of state changes to the "observer"
- **View** - gives user a presentation of the Model. Gets its data directly from the Model
- **Controller** - Takes user input and figures out what it means to the Model

![Model-View-Controller](/resources/images/software_engineering/model-view-controller.png)

#### Module/Subsystem Views

- Decomposition View
  - Top-down refinement
- Dependency View
  - How parts relate to one another
- Layered View
  - Special case of dependency view
- Class View
  - "domain-model" in OOA and "class-diagram" in OOD
