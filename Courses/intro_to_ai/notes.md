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
- For the complete Turing test, the program would also posses *computer vision* to interpret the question, and *robotics* to manipulate objects to write a response.

#### Thinking Rationally

- Rationality: being reasonable, based on facts or reason; doing the right thing.
- Aristotle, a Greek philosopher, was one of the first to attempt tot codify rational thinking. He created **syllogisms** to provide patterns that always yielded correct conclusions when given the correct inputs.

#### Acting Rationally

- AI is the discipline of studying and designing rational agents.

### Agents

- An **agent** is something that can perceive its environment through sensors and acting upon that environment through actuators.
- **Precept** - the agent's perceptual inputs at any given instance. A **precept sequence** is the complete history of what the agent has perceived.
- The **agent function** maps any given precept or precept sequence to an action.
- A **rational agent** is an agent that acts to achieve the best expected outcome.
- To measure the performance of an agent, we must define a measure of performance. Some way to quantize the performance of the agent.
- Properties of agent environments are defined in the table below.

| **Fully Observable**     | Only whatever your agent can sense at a given time is sufficient to make the optimal decision     |
| **Partially Observable**       | The agent requires memory to make the optimal decision |
| **Deterministic** | An environment where your agent's actions uniquely determine the outcome. |
| **Stochastic** | An environment is one where your agent's actions cannot uniquely determine the outcome, as there is some sort of randomness involved. |
| **Discrete** | An environment is one where the agent has a finite number of action choices and a finite number of things you can sense. |
| **Continuous** | An environment where the space of possible actions or things you can sense may be infinite. |
| **Benign** | The environment might be random, stochastic, but it has no objective of its own that would contradict your objective |
| **Adversarial** | The environment might be random, stochastic, but it has an objective of its own to contradict your objective. |
| **Single Agent** | The environment only contains one agent at a time. |
| **Multiagent** | The environment may contain several agents at a time. |
| **Episodic** | An environment where an agent only has to do one action to complete its task. |
| **Sequential** | An environment where an agent must take more than one action to complete its task. |
| **Known** | An environment where the agent knows all the possible attributes of the environment. |
| **Unknown** | An environment where the agent doesn't know the attributes of the environment. |
{:.mbtablestyle}

<br>

#### **IN THIS COURSE, WE ASSUME THAT THE ENVIRONMENT IS KNOWN AND *FULLY OBSERVABLE*, AND ACTIONS ARE *DETERMINISTIC*. THE ENVIRONEMENTS WILL ALSO BE SINGLE AGENT.**

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

- The initial state, actions, and transition model together implicitly define the **state space** of a problem.

- A **path** is a sequence of states connected by a sequence of actions.
  - The cost of a path is the sum of the costs of the individual actions along the path. The **step cost** of an action, $$a$$, in state $$s$$ to reach state $$s'$$ is denoted by $$c(s,a,s')$$.
- A **solution** to a problem is a sequence of actions that leads from the initial state to the goal state. A solution with the lowest path cost is an **optimal solution**.

---

<u>Vacuum World Example</u>

This world contains a vacuum the two rooms, A and B. The vacuum has the actions left/right to move between rooms, and suck to get rid of the dirt in a given room.

![Vacuum World](/resources/images/intro_to_ai/vacuum_world.PNG){:height="25%" width="25%"}

The state space of the problem is shown below.

![Vacuum World State Space](/resources/images/intro_to_ai/vacuum_world_state_space.PNG)

The formal description of the Vacuum World is

- States: There are 2 rooms that may or may not contain dirt and there are 2 positions for the robot. There are $$ 2 \cdot 2^{2} = 8 $$ possible world states.
- Initial State: Any state can be the initial state.
- Goal State: Having both the rooms clean. This is seen in the bottom two states of the state space.
- Actions: Move left, Move right, suck
- Transition model: The actions have their expected effects. Moving left or right, moves the robot accordingly. Moving left in the left space or moving right in the right space have no effect on the position of the robot.
- Path cost: Each action has a cost of 1.

---

### Search Trees

- A solution to a problem is an action sequence. Search algorithms work by considering various possible action sequences and finding the optimal one as a solution. All the possible action sequences starting from the initial state from a **search tree** with the initial state at the root. The branches are actions and the **nodes** correspond to the states in the problem's state space.
- The process of finding the goal state in the tree is called **tree searching**

### Tree Search

- A node is **expanded** when all it's children are added to the search tree.
- The set of nodes that have already been added to the search, but have not yet been expanded is called the **open list**, **fringe**, or **frontier**.
- A generic algorithm for tree searching is

```
function tree_search(problem):
  fringe = {Initial State}
  loop:
    if fringe is empty : return FAIL
    s = remove_choice(fringe)
    if s is a goal : return path taken to goal
    for a in actions: //Expand current node
      add [result(s,a)] to fringe
```

- The tree search starts by initializing the fringe with the initial state of the problem. Then enters a loop where it first checks to see if there are any nodes in the fringe. If there are no nodes, it returns a failure. If there are nodes in the fringe, we choose a node, s, and remove it from the fringe. If s is a goal state, the program then returns the path it took from the root to node s. If it is not a goal state, then we expand state s. We look at all the actions that can be done at the state, and add the resulting nodes to the fringe.
- Search algorithms vary with the way they remove from and add to the fringe. They only vary in the function ``` remove_choice()``` from the algorithm above.

### Implementing a Search Tree algorithm

- In a search tree, each node, n, is represented by a data structure that contains the fields of
  - **n.State**: the state the node corresponds to
  - **n.Parent**: the parent of node n
  - **n.Action**: the action from n.Parent that leads to node n
  - **n.Path-cost**: the cost of the path from root to the current node, denoted by $$g(n)$$
  - **n.Depth**: number of nodes from root to current node including the current node

- A generic child node is

```
function CHILD-NODE(problem, parent, action) returns a node
  return a node with
    STATE = problem.RESULT(parent.STATE, action),
    PARENT = parent, ACTION = action,
    PATH-COST = parent.PATH-COST + problem.STEP-COST(parent.STATE, action)
```

- The nodes are kept in a queue. The operations on a queue are
  - **EMPTY?(queue)**: returns true if the queue is empty
  - **POP(queue)**: removes the first element and returns it
  - **INSERT(element, queue)**: insert an element and returns the resulting queue. This is also known as PUSH().
  - **INITIALIZE(element)**: returns a queue that contains the element
- Queues are categorized by the order in which they store the inserted nodes
  - **FIFO**: first-in, first-out
  - **LIFO**: last-in, first-out
  - **Priority**: pops the element with the highest priority according to a priority function

- The four criteria used to compare various search tree algorithms are
  - **Completeness**: Is the algorithm guaranteed to find a solution when there is one?
  - **Optimality**: Does the strategy find the optimal or best solution?
  - **Time Complexity**: How much time does it take to find a solution?
  - **Space Complexity**: How much memory is needed to perform the search?
- The following parameters are used to calculate and compare the performance of an algorithm:
  - **b**: the maximum branching factor(number of children per node)
    - If the number of children per parent vary, then we would use an effective branching factor
  - **d**: the depth of the shallowest goal state
  - **m**: the maximum length of a path in the tree
- The **search cost** or a search algorithm refers to the time complexity. However, it can also include a term for the memory usage, and when it does, it is known as **total cost**. This combines the search cost and the path cost of the algorithm.

### Graph Search

- The set of expanded nodes is called the **closed list** or **explored list**.
- In tree searches, there can be several repeated nodes in the search tree. To avoid these redundant paths, graph searching keeps tracks of explored nodes as well.
- A generic algorithm for graph searching is

```
function graph_search(problem):
  fringe = {Initial}; explored = {}
  loop:
    if fringe is empty : return FAIL
    s = remove_choice(fringe)
    add s to explored
    if s is a goal : return path to goal
    for a in actions:
      add [path + a -> result(s,a)] to fringe
      unless result(s,a) is in fringe and explored
```

- This algorithm is similar to the tree search algorithm, but with a few added steps. When we start the search, we initialize the explored set which holds the states that we have already explored. Then when we choose a new node, we add it to the set of explored nodes. Also, when we expand the new node, we don't add in a node if we have already encountered that node in the fringe or the explored sets to eliminate the redundancy.


### Uninformed Search Strategies

- An uninformed search algorithm means the strategies have no additional information about the states beyond that provided in the problem definition.
- Some uninformed search algorithms are
  - Breadth-first search
  - Uniform-cost search
  - Depth-first search
  - Depth-limited search
  - Iterative deepening depth-first search
  - Bidirectional search

#### Breadth-First Search (BFS)

- BFS expands all the nodes in current level first before expanding the nodes at the next level.
- BFS always has the shallowest path to every node in the frontier.
- BFS is optimal and complete.
- An example of BFS is

![BFS](/resources/images/intro_to_ai/BFS.PNG)

- A generic BFS algorithm is

```
function BREADTH-FIRST-SEARCH(problem) returns a solution, or failure
  n <- a node with STATE = problem.INITIAL-STATE, PATH-COST = 0
  if problem.GOAL-TEST(n.STATE) then return SOLUTION(n)
  frontier <- a FIFO queue with n as the only element
  explored <- an empty set
  loop:
    if EMPTY?(frontier) then return failure
    n <- POP(frontier) // Chooses the shallowest node in the frontier
    add n.STATE to explored
    for each action in problem.ACTIONS(n.STATE) do
      child <- CHILD-NODE(problem, n, action)
      if child.STATE is not explored or frontier then
        if problem.GOAL-TEST(child.STATE) then return SOLUTION(child)
        frontier <- INSERT(child, frontier)
```

- The properties of BFS are
  - Frontier Queue: First-in First-out (FIFO)
  - Completeness: Complete if branching factor, b, is finite
  - Optimality: Optimal only if all the costs of the edges are equal(shallowest path in the tree is not always the shortest is the problem)
  - Time complexity: $$ O(\sum_{i=0}^{d-1} b^i) = O(b^d) $$
  - Space complexity: $$ O(\sum_{i=0}^{d-1} b^i) = O(b^d) $$
- With an exponential complexity($$O(b^d)$$) is really inefficient!

#### Uniform-Cost Search

- BFS is optimal only when all step costs are equal. Uniform-cost search, however, expands the node with the lowest path cost, instead of the shallowest node.
- The queue of the fringe is ordered by path cost.
- In BFS, all the nodes in the queue have the same path cost, and the goal test is performed when a node is generated. However, in Uniform-cost search, the nodes in the queue have different path costs. The goal test is performed when a node is expanded.



- A generic Uniform Cost Search algorithm is

```
function UNIFORM-COST-SEARCH(problem) returns a solution, or failure
  n <- a node with STATE = problem.INITIAL-STATE, PATH-COST = 0
  frontier <- a priority queue ordered by PATH-COST, with n as the only element
  explored <- an empty set
  loop:
    if EMPTY?(frontier) then return failure
    n <- POP(frontier) // Chooses the lowest-cost node in the frontier
    if problem.GOAL-TEST(node.STATE) then return SOLUTION(n)
    add n.STATE to explored
    for each action in problem.ACTIONS(node.STATE) do
      child <- CHILD-NODE(problem, node, action)
      if child.STATE is not in explored or frontier then
        frontier <- INSERT(child, frontier)
      else if child.STATE is in frontier with higher PATH-COST then
        replace that frontier node with child
```

- The properties of Uniform-cost Search are
  - Frontier queue: Ordered by path cost
  - Completeness: Complete if branching factor is finite
  - Optimality: Optimal search
    - Whenever uniform-cost search selects a node, n, for expansion, the optimal path node has been found
  - Time complexity: $$ O(b^{1 +\lfloor C^{*}/\epsilon \rfloor}) $$, where $$C^* $$ is the path cost of the optimal path and $$\epsilon$$ is the minimum step cost. There is a factor of 1 before because we start at the root which is position 0, which then contributes the factor of 1.
  - Space complexity: $$ O(b^{1 +\lfloor C^{*}/\epsilon \rfloor}) $$, where $$C^* $$ is the path cost of the optimal path and $$\epsilon$$ is the minimum step cost. There is a factor of 1 before because we start at the root which is position 0, which then contributes the factor of 1.

- Dijksta's algorithm is a slightly different variant of Uniform-cost search
  - Dijksta's uses a list of unvisited verticies(initially contains all verticies), and a table that keeps track of the shortest distance to each vertex so far(initialized to infinity) instead of open and closed lists.

#### Depth First Search (DFS)

- DFS always expands the deepest node in the frontier first.
- DFS can get stuck in infinite loops if visiting repeated states is allowed
- Properties of DFS:
  - Frontier queue: Last-in First-out (LIFO)
  - Optimality: Not optimal, because it returns the first path that contains the goal.
  - Time Complexity: $$ O(b^m) $$, where m is the maximum depth of any node. This is worse than BFS($$O(b^d)$$) where d is the depth of the shallowest node.
  - Space Complexity: $$ O(b \cdot m) $$ and $$O(m)$$ when using backtracking(where we don't need to generate all the successors of each node)

#### Depth Limited Search
- In an infinite state space, DFS fails if an infinite non-goal path is encountered. To avoid getting stuck in an infinite loop, we can supply a predetermined depth limit, l.
  - This makes the time complexity $$ O(b^l) $$
  - This makes the space complexity $$ O(b \cdot l) $$

- A generic Depth Limited Search algorithm is

```
function DEPTH-LIMITED-SEARCH(problem, limit) returns a solution, or failure/cutoff
  return RECURSIVE-DLS(MAKE-NODE(problem.INITIAL-STATE), problem, limit)

function RECURSIVE-DLS(node, problem, limit) returns a solution, or failure/cutoff
  if problem.GOAL-TEST(node.STATE) the return SOLUTION(node)
  else if limit=0 then return cutoff
  else
    cutoff_occurred? <- false
    for each action in problem.ACTIONS(node.STATE) do
      child <- CHILD-NODE(problem, node, action)
      result <- RECURSIVE-DLS(child, problem, limit-1)
      if result = cutoff then cutoff_occurred? <- true
      else if result != failure then return result
    if cutoff_occurred? then return cutoff else return failure
```

#### Iterative Deepening Depth-First Search

- To solve a problem of choosing the right depth, l, we can start with l=0, and iteratively increase during search.
- Iterative Deepening DFS runs repeatedly through the tree, increasing the depth limit with each iteration until it reaches the depth of the shallowest goal.
- Iterative Deepening DFS has the space complexity of DFS of DFS and the completeness of BFS.

- An example of iterative deepening DFS is

![Iterative Deepening DFS](/resources/images/intro_to_ai/iterating_deepening_DFS.PNG)

- Properties of Iterative Deepening DFS:
  - Optimality: Optimal, if all the edges have the same edge cost
  - Complete: by iteratively increasing the limit, at some point the algorithm reaches the goal and the algorithm never searches an infinite path
  - Time Complexity: $$ O(b^d) $$, the number of nodes using depth limit, d, is equal to the number of nodes using all depths that are < d.
  - Space Complexity: $$ O(b^d) $$, which is also the same as BFS.

#### Bidirectional Search

- Runs two simultaneous BFS searches: one forward from the initial state, and one backward from the goal.
  - Then stop when both of the two BFS searches meet.
- Bidirectional search properties:
  - Complete: Complete, if the branching factor, b, is finite
  - Optimality: Optimal, if all the edges have the same cost, similar to BFS
  - Time complexity: $$ O(2b^{(\frac{d}{2})}) = O(b^{(\frac{d}{2})}) $$
  - Space complexity: $$ O(2b^{(\frac{d}{2})}) = O(b^{(\frac{d}{2})}) $$
