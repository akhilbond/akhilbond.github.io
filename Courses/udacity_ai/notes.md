---
layout: page
title: Intro to AI - Udacity
permalink: /Courses/udacity_ai/
mathjax: true
---

# Unit 1 - Intro to AI

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

# Unit 2 - Problem Solving

## Definition of a Problem

- Parts of a problem
  - The **initial state** the agent starts with
  - A function, **actions**, that takes a state as input, and returns a set of possible actions for the agent when in that state.
  - A function, **result** which takes a state and an action as input, and returns a new state.
  - A function, **goaltest**, which takes a state as input and returns a true or false depending on whether the input is a goal or not.
  - A function, **pathcost**, which takes a path(a sequence of state action transitions) and returns the cost of that path.
    - A **stepcost** function takes a state, an action, and the resulting state from that action and returns the cost of that action.

## Tree Search Algorithm

```
function tree_search(problem):
  fringe = {Initial}
  loop:
    if fringe is empty : return FAIL
    path = remove_choice(fringe)
    s = path.end
    if is is a goal : return path
    for a in actions:
      add [path + a -> result(s,a)] to fringe
```

- Starts by initializing the fringe to be a path only holding the initial state. Then enters a loops where it first checks to see if there is anything left in the fringe. If there is nothing left, the program fails. If there is something left in the fringe, we choose a path and remove it from the fringe. Then we set s to be the last state of the chosen path. Then if that final state is a goal, we return the path. If that final state is not the goal, then we expand that path. We look at all the actions that can be done at that state, and append the old path, the action, and the result of that action to the fringe.

## Graph Search Algorithm

```
function graph_search(problem):
  fringe = {Initial}; explored = {}
  loop:
    if fringe is empty : return FAIL
    path = remove_choice(fringe)
    s = path.end; add s to explored
    if is is a goal : return path
    for a in actions:
      add [path + a -> result(s,a)] to fringe
      unless result(s,a) is in fringe and explored
```

- This algorithm is similar to the tree search algorithm, but with a few added steps. When we start the search, we initialize the explored set which holds the states that we have already explored. Then when we choose a new path, we add it to the set of explored states. Also, when we expand the new path, we don't add in a state if we have already encountered that state in the fringe or the explored sets.

## Search Algorithms

![Search Algorithms](/resources/images/udacity_ai/search_algos.PNG)

### Breadth First Search

- This search algorithm always chooses the shortest possible path off the fringe.
- This algorithm is complete.

### Uniform Cost Search(Cheapest First Search)

- This search algorithm always chooses the path with the path with the lowest total cost off the fringe.
- This algorithm is complete.

### Depth First Search

- This search algorithm always chooses the longest possible path off the fringe.
- This algorithm is not complete.

### Greedy Best First Search

- This algorithm always chooses the path with the least distance to the goal. It expands nodes that get continuously closer to the goal node.
- This algorithm does not always return the shortest path if there are obstacles in the way.

## A* Search

- This algorithm always expands the with the minimum value of the function f. The function f is the sum of the path cost and the heuristic of the final state in the path.
- This algorithm finds the lowest cost path if the h(heuristic) cost for a state is less than the true cost of the path to the goal through that state. Another way to state this condition is that h is optimistic, or **admissible**. An admissible heuristic also never over estimates.

## State Spaces

- An example of a state space is the vacuum world shown below. In this space, the vacuum can be in either space a or b. Also, space a or b can be dirty or clean.

![Vacuum world](/resources/images/udacity_ai/vac_world.JPG)

- The state space above has 8 spaces because there are 2 places where the vacuum can be, and 4 combinations of the spaces to be dirty and clean. The diagram of all the states in the state space are shown below.

![Vacuum World State Space](/resources/images/udacity_ai/vacuum_world_state_space.JPG)

## Constraints of Problem Solving Technology

- Problem solving technology only works when:
  - the domain is fully observable(must be able to see the initial state)
  - the domain is known(all the possible actions must be known)
  - the domain is discrete(must be a finite number of actions to choose from)
  - the domain is deterministic(result of taking an action must be known)
  - the domain is static(nothing else in the world that can change the world except for our own actions)

## Implementation of Search Algorithms

- With search algorithms, we talk a lot about paths in the state space. When implementing paths in computer programs, we make use of nodes. A node is a data structure with the four fields.
- The fields of a node are
  - state - State at the end of the path
  - action - The action the algorithm took to get to the state
  - cost - Total cost of the path
  - parent - A pointer to another node before it.
- The two data structures that utilizes nodes in search algorithms are the fringe and the explored set
  - Since we add and remove nodes from the fringe, which means it should be implemented as a priority queue. However, there must also be a check to see if a node is in the fringe, so it can also be implemented as a hashmap or a tree.
  - With the explored set, we just add new nodes and check if nodes are in the set. So this can be implemented with hashmap or a tree as well.

# Unit 3 - Probability in AI

## Bayes Network

- A Bayes Network is a compact representation of a distribution over this very large joint probability distribution or all the variables.

- A Bayes Network is composed of nodes and these nodes correspond to events that you may or may not know(random variables). These nodes are connected with arcs and an arc suggests that the child of the arc is influenced by the parent. It may not be influenced in a deterministic way, but may be influenced in a probabilistic way.

## Probabilities

- Complimentary probability - $$ P(A) = p \to P(\bar{A}) = 1-p $$
- Independence - If two variables, x and y, are independent, then the joint probability of the two variables is the product of probability of x and probability or y.
- Dependence - One probability depends on the probability of another event. An example of a dependence problem is shown below.

![Dependence Example](/resources/images/udacity_ai/dependence.PNG)

- Law of Total Probability - $$ P(Y) = \sum_{i}^{n} P(Y|X=i)\timesP(X=i) $$
