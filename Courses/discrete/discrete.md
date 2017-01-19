---
layout: page
title: Discrete Mathematics (198:205)
permalink: /Courses/discrete/
mathjax: true
---

- __The syllabus and other important details of the course are located at the [Course Website](https://www.cs.rutgers.edu/~allender/205/)__

## Set Theory

- A set is a group of elements
- An example of a set is {1,2,a,b}
- Sets are considered equal if they have the same unique elements, no matter the order or # of times the element appears.
- A proof for set equality is

$$ A=B \; \; iff \; A \in B \; \text{and} \; B \in A $$

- An example of equal sets is

$$ \{ 1,2,a,b \} = \{ 1,1,b,b,a,a,a,2,2,2 \} $$

- **Intersection** $$ ( \cap ) $$ - The unique elements of the sets that are present in both sets

$$ A \cap B = \{ x : x \in A \; \mathbf{AND} \; x \in B \} $$

- An example of the intersection of two sets is

$$ \{ a,b,c \} \cap \{ c,d,e \} = \{ c \} $$

- **Union** $$ ( \cup ) $$ - All of the unique elements of both sets, each included only once

$$ A \cap B = \{ x : x \in A \; \mathbf{OR} \; x \in B \} $$

- An example of the union of two sets is

$$ \{ a,a,a,b,b,c \} \cup \{ c,d,d,e,e,e \} = \{ a,b,c,d,e \} $$

- **Difference**(-) - The elements that are in one set, but not in the other

$$ A - B = \{ x : x \in A \; \text{and} \; x \notin B \} $$

- An example of the difference of two sets is

$$ \{ a,b,c \} - \{ c,d,e \} = \{ a,b \} $$

- **Size** of a set (\|\|) - the number of unique elements in a set. The size of a set is also know as the **cardinality**.
- An example of finding the size of a set is

$$ | \{ 1,2,3 \} | = | \{ 1,1,2,2,3,3,3 \} | = 3 $$

- **Empty Set** $$ ( \emptyset ) $$ - A set which contains no elements
  - The size of the empty set is 0
  - Every set technically contains the empty state

- **Power Set** - noted by $$ \mathscr{P} (A) $$

$$ \text{Let A be a set} \; \; \; \mathscr{P} (A) = \{ B : B \subseteq A \} $$

- An example of the power set is

$$ A = \{ 0,1 \} \; \; \; \mathscr{P} (A) = \{ \emptyset , \{ 0 \} , \{ 1 \} , \{ 0,1 \} \} $$

$$ | \mathscr{P} (A) | = 2^{|A|} $$

- **Multiplication** (X) - defined as

$$ \{ a,b \} \text{X} \{ 0,1,2 \} = \{ (a,0), (a,1), (a,2), (b,0), (b,1), (b,2) \} $$

- **DeMorgan's Law**

$$ \overline{A \cup B} = \overline{A} \cap \overline{B} \quad \mathbf{OR} \quad \overline{A \cap B} = \overline{A} \cup \overline{B} $$

- **Function** $$ (f : A \to B) $$ - A mapping of the *Domain*(Inputs) to the *Codomain*(Outputs)
- The **Range** of a function is

$$ Range(f) = f(A) = \{f(x) : x \subseteq A \} $$

- A function, f, mapping A to B is a subset of $$ AxB $$
- Any subset of $$ AxB $$ set, for every $$ x \subseteq A $$, there is exactly one $$ y \in B $$
  - In other words, each input has one output
