---
layout: page
title: Data Structures
permalink: /Courses/Data_Structures/
mathjax: true
---
## Prerequisite Topics:

#### You are expected know these topic before beginning the course.

- Comfortable writing and debugging programs 1 to 2 pages long
- Basic Java (types,control flow,etc.)
- Arrays(1D)
- Sequential Sort
- Insertion Sort
- Recursion
- Using objects
- Big-O worst case analysis

<br>

### What is a Data Structure?
- A data structure is a format for storing multiple pieces of data or relationships between pieces of data. Some example of data structures are objects, arrays, linked lists, etc.

One important aspect of computer programming is checking how long the program takes to run and return the output. This is found using big-O analysis. Some factors that may affect the run time of a program include:

- Computer used
- Language of the program
- Compiler used
- Inputs
- Programmer abilities

<br>

### How to analyze program runtime(Big O)
- Count number of operations executed instead of time elapsed
- The operation count of a program is a function of the input size
- Among inputs of the same size, count the worst case number of comparisons and the best case number of comparisons. Then this is used to find the Big O of the program by focusing on the large inputs and ignoring constants and other multiples.
- Big O notation is O(f), which means the Big O of a function that was found using worst case analysis.

<br>

### Big O Analysis Review
- Since we are counting operations, the processor speed doesn't matter
- Which operation do we count??
     - Most frequent / inner loop
     - Most time consuming
     - Inherent in algorithm, not programming language

- The number of operations depends on("is a function of") the number/size of inputs
    - Number of operations = f(input)



- Average case
  - Computing average cost:
    - What determines the cost?
    - For each such case, find the cost of that case(number of operations), and the probability of that case occurring
    - Sum the cost times the probability over all cases

#### Example :

Array Search code :

~~~
Input: double Array A, int n, double target
Output: boolean: Are any of the first n elements of A equal to the target value

for(i=0; i<n; i++){
  if (A(i) == target){
    break;
  }
}
return i < n;
~~~
- The above code scans through each element of array A, and checks one of the first n elements equals the target value. It returns true if a match was found within the first n elements and returns false if it was found outside of the n elements or not found at all.

#### Big O analysis of above code :

- Worst case : Match not found or match found at the end
    - number of operations = size of array
- Average case :

  $$\sum_{i=0}^n (p* \frac{1}{n}) = \frac{1}{n} \frac{n*(n+1)}{2} = \frac{n+1}{2}$$

- Assume a 50% chance of target not being found
    - If target is found, then there is an equal probability at each position
    - Average Cost = [P(found) * cost if found] + [P(not found) * cost if not found]


### Linked lists
- Linked lists store an ordered list of data terms, all of the same type.
- Most of the time we don't worry about what is 1st, 2nd, 3rd, etc., but it can be more efficient to care about "What comes next?"
- Each entry in the list contains a node. A node is a pointer from the current data element to the next.

#### The IntNode Class

~~~
public class IntNode{

  int data;
  IntNode next;

  public IntNode(int data, IntNode next){
    this.data = data;
    this.next = next;
  }
}
~~~

- The above code is an example of a class called "IntNode" which is used in linked lists. In the declaration statement of the IntNode called Next is a reference to an IntNode object.
- The following is an example of a two-IntNode list.

![Two-IntNode List Example](/resources/two-intnode_list.png)
