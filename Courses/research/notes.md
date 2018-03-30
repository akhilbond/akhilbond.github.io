---
layout: page
title: Research
permalink: /Courses/research/
---

# Reinforcement Learning

## MDP - Markov Decision Processes

- MDP's are used when the environment is fully observable, however the agent's actions are stochastic. They are useful because, in the real world, the environment is fully observable through the robot's sensors, however every movement that the robot makes is not always perfect.

- A sequential decision problem for a fully observable, stochastic environment with a Markovian transition model and additive rewards is called a **Markov Decision Process**. It consists of a set of states (with an initial state of $$ S_0 $$), a set *ACTIONS(s)* of actions in each state, a transition model $$ P(s' \vert s,a) $$, and a reward function *R(s)*.

- Since the environment is stochastic, we know that any fixed action sequence will not solve the problem. We must come up with a solution that specifies what the agent should do at any state that it might reach, this is known as a **policy**, also written as $$ \pi (s) $$.

- An **optimal policy** is a policy that yields the highest expected utility. We use $$ \pi * (s) $$ to denote the optimal policy.

## Markov States

- A state $$ S_t $$ is Markov if and only if

$$ \mathbb{P} [S_{t+1} | S_t ] = \mathbb{P} [S_{t+1} | S_1, ..., S_t ] $$

  - The state captures all the relevant information from the history
  - Once the state is known, the history may be thrown away

## State Transition Matrix

- For a Markov state, s, and a successor state s', the state
