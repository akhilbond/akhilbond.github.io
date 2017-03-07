---
layout: page
title: Network Centric Programming
permalink: /Courses/Network_Centric/
---

# Introduction

- This course covers coding network programs in the C programming language.

# Debugging

- What happens if we have a segmentation fault, this means that some portion of our code is trying to access a piece of memory that it does not have access to. Now how do we debug this and find the problem?

- One way to find the error is the use print statements to find which statement doesn't print to show the location of the error. However, this may get the job done, but is very difficult to use on code with a lot of lines and it is very time consuming to find the right place in the code.

- GDB is a tool which allows you to inspect the program state at the moment of failure.
  - Look at variable contents
  - Look at which function was executed
  - Look at register values to see which address caused the segfault

- GDB is used through these shell commands

- ```gcc -g mysource.c``` - compiles the source code with the gdb flag and gdb compatibility with the -g flag

- ```limit -c unlimited``` - enables core dumps when using the gdb debugger

- ```./a.out``` - execute the compiled code until segfault

- ```gdb a.out core``` - allows you to use gdb and look at the current state of the code when it had the segfault


# Processes



# Threads



# Locking

## MUTEX

- Acts as a lock for certain lines of code in a tread which makes sure that a thread accesses a shared variable when another thread is not using it, to avoid corruption of data.

- To create a lock, we would execute the following code

```C
//To create a MUTEX lock
pthread_mutex_t childsum_mutex = PTHREAD_MUTEX_INITIALIZER;
```

- To start the lock, place the following piece of code at the beginning of the portion of code which you would like to lock

```C
//Mark the beginning of the portion of code you want to lock
pthread_mutex_lock(&childsum_mutex);
```

## File Locks - "Record Locks"

- Synchronize access from multiple processes from shared memory
- Allows you to specify what portion of a file to lock to improve performance

## Deadlock

- Can occur is threads acquire several locks for one operation

- Atomic instructions - thread safe instructions which already in your operating system
- Thread safe functions - functions which can be used without using a MUTEX lock
  - The only way to identify if a function is thread safe is to read the documentation for the function
  - A list of some functions that are NOT thread safe are listed on the man page for pthreads
