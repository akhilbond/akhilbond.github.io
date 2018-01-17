---
layout: page
title: Intro to AI
permalink: /Courses/intro_to_ai/
mathjax: true
---

## <u>Introduction</u>

### What is Intelligence?

- According to the Oxford dictionary, intelligence is the ability to acquire and apply knowledge and skills.
- Intelligence is a goal-directed adaptive behavior

### What is AI?

- There have been 4 approaches to AI that have been followed in history
  - Thinking Humanly
  - Acting Humanly
  - Thinking Rationally
  - Acting Rationally

#### Thinking Humanly

- For a program to think like a human, we must know how we think. We use **introspection** to observe our thoughts. We use **psychological experiments** to observe a person's actions and we use **brain imaging** to observe the brain during all of this.

#### Acting Humanly

- The **Turing test** - used to provide an operational definition of intelligence.
  - A human interrogator is placed in a room, with a computer placed in the room next door. The interrogator then poses questions to the room and the computer passes the test if the human cannot tell whether the response comes from a human or a computer.
- To pass the Turing test, the computer needs to posses the following:
  - Natural Language Processing
  - Knowledge Representation
  - Automated Reasoning
  - Machine Learning
- For the complete Turing test, the program would also posses computer vision to interpret the question, and robotics to manipulate objects to write a response.

#### Thinking Rationally

- Rationality: being reasonable, based on facts or reason; doing the right thing.
- Aristotle, a Greek philosopher, was one of the first to attempt tot codify rational thinking. He created **syllogisms** to provide patterns that always yielded correct conclusions when given the correct inputs.

#### Acting Rationally

- AI is the discipline of studying and designing rational agents.

### Agents

- An **agent** is something that can perceive its environment through sensors and acting upon that environment through actuators.
- **Precept** - the agent's perceptual inputs at any given instance. A **precept sequence** is the complete history of what the agent has perceived.
- The **agent function** maps any given precept to an action.
- A **rational agent** is an agent that acts to achieve the best expected outcome.
- Properties of agent environments are defined in the table below.

| **Fully Observable**     | Only whatever your agent can sense at a given time is sufficient to make the optimal decision     |
| **Partially Observable**       | The agent requires memory to make the optimal decision |
| **Deterministic** | An environment where your agent's actions uniquely determine the outcome. |
| **Stochastic** | An environment is one where your agent's actions cannot uniquely determine the outcome, as there is some sort of randomness involved. |
| **Discrete** | An environment is one where the agent has a finite number of action choices and a finite number of things you can sense. |
| **Continuous** | An environment where the space of possible actions or things you can sense may be infinite. |
| **Benign** | The environment might be random, stochastic, but it has no objective of its own that would contradict your objective |
| **Adversarial** | The environment might be random, stochastic, but it has an objective of its own to contradict your objective. |
{:.mbtablestyle}

<br>

#### **IN THIS COURSE, WE ASSUME THAT THE ENVIRONMENT IS KNOWN AND *FULLY OBSERVABLE*, AND ACTIONS ARE *DETERMINISTIC*.**

<br>

## <u>Solving Problems by Searching</u>

- A well defined problem is described by
  - **States** - set of all possible situations
  - **Initial state** - starting state
  - **Goal state(s)** - destinations or final positions
  - **Goal test** - determines whether a given state is a goal state
  - **Actions** - set of everything an agent can do to change its current state.
  - **Transition model** - the effect of each action
  - **Path cost** - function that assigns a numeric cost to each path.

- The initial state, actions, and transition model together implicictly define the **state space** of a problem.

- A **path** is a sequence of states connected by a sequence of actions.
  - The cost of a path is the sum of the costs of the individual actions along the path. The step cost of an action, $$a$$, in state $$s$$ to reach state $$s'$$ is denoted by $$c(s,a,s')$$.
