---
layout: page
title: Intro to AI - Udacity
permalink: /Courses/udacity_ai/
mathjax: true
---

# Unit 1

## Intelligent Agents

- An AI program is called an Intelligent Agent
- Intelligent agents *perceive* the environment with its **sensors** and *affect* the environment's state with its **actuators**. The big question of AI is finding the function that maps sensors to actuators. This is also known as a **control policy** for the agent.
- The process of the agent perceiving through its sensors, deciding what to do, then interacting with the environment with its actuators is called the **perception-action cycle**. The agent goes through this cycle several times.

## Terminology

- An environment is **fully observable** if *only* whatever your agent can sense at a given time is sufficient to make the optimal decision.
- An environment is **partially observable** if the agent requires memory to make the optimal decision.
- A **deterministic** environment is one where your agent's actions uniquely determine the outcome.
- A **stochastic** environment is one where your agent's actions cannot uniquely determine the outcome, as there is some sort of randomness involved.
- A **discrete** environment is one where the agent has a finite number of action choices and a finite number of things you can sense.
- A **continuous** environment is one where the space of possible actions or things you can sense may be infinite.
- A **benign** environments, the environment might be random, stochastic, but it has no objective of its own that would contradict your objective.
- An **adversarial** environment, the environment might be random, stochastic, but it has an objective of its own to contradict your objective.

# Unit 2

## Definition of a Problem

- Parts of a problem
  - The **initial state** the agent starts with
  - A function, **actions**, that takes a state as input, and returns a set of possible actions for the agent when in that state.
  - A function, **result** which takes a state and an action as input, and returns a new state.
  - A function, **goaltest**, which takes a state as input and returns a true or false depending on whether the input is a goal or not.
  - A function, **pathcost**, which takes a path(a sequence of state action transitions) and returns the cost of that path.
    - A **stepcost** function takes a state, an action, and the resulting state from that action and returns the cost of that action.
