---
layout: page
title: Intro to Computer Systems
permalink: /Courses/Intro_to_comp_systems/
---

## Introduction

- Textbook
  - Operating Systems Concepts(9th Edition) - Silberschatz, Galvin, and Gagne

## What is an Operating System?

#### <u>Theoretical Location of the OS</u>
```
APPLICATION (USER)
------------------
 OPERATING SYSTEM
------------------
    HARDWARE
```

- A <i><b>software layer</b></i> between the hardware and the application programs/users which provides a virtual machine interface
- A <i><b>resource manager</b></i> allows programs/users to share the hardware resources
- A <i><b>set of utilities</b></i> to simplify application development and execution

- The abstract view of a computer system

![Abstract View of the components of a Computer System](C:\Users\akhil\Documents\GitHub\akhilbondlela.github.io\Courses\Intro_to_comp_systems\Abstract_view_of_comp_sys.PNG)

- The users interface with the system and applications
- The operating system manages the applications and the resources the applications use
- The OS also manages the connection to the computer hardware which executes specific operations for the high level applications to work


- Benefits of an OS for application writers
  - Easy to write programs
  - Using high level abstractions instead of low level hardware details
    - Files instead of disk blocks


- Benefits of an OS for standard users
  - Easier to use the computers
    - Everyone who uses the computer do not need to be knowledgeable about computer hardware
  - Safety
    - It protects programs from each other
    - It also protects uses from each other


- Mechanisms - data structures and operations that implement an abstraction(e.g. buffer cache)
- Policies - the procedures that guides the selection of a certain course of action among alternatives(e.g. the replacement policy for the buffer cache)


- Virtual machine abstractions
  - **Process** - system abstraction - illusion of being the only job executing in the system
  - **Threads** - CPU abstraction - illusion of having a dedicated CPU
  - **Virtual Memory** - memory abstraction - illusion of having unlimited memory
  - **File System** - storage abstraction - illusion of structured, persistent storage system
  - **Messaging** - communication abstraction - illusion of reliable, ordered communication
  - **Character and block devices** - I/O abstraction - standardized I/F for devices


  - Major Issues in OS design
    - Performance - How to make it run fast?
    - Reliability - How do we keep it from crashing?
    - Persistence
    - Accounting
    - Distribution
    - Scaling


## Computer Architecture Refresher

- How a processor executes instructions
  - Fetches instructions
  - Processes data using ALU's
  - The operating system manages the CPU(processor)
  - How it executes programs
    - Fetch - using fetching unit(if multiple fetching units, then we can fetch multiple instructions at once)
    - Decode
    - Execute
    - Memory
    - Write-back


#### The Program Counter

  - Where the "next instruction" is held in the machine
  - In a special memory cell in the CPU, called the program counter (PC)

#### Memory Indirection

- How do we access array elements efficiently if all we can do is name a cell?
  - Modify the operand to allow for fetching and operand "through" a memory location
- This is called indirection

#### Registers

- Architecture Rule : Large memories are slow and smaller ones are faster
- Most programs work on only small chunks of memory in a given time period. This is called **locality**
- Most CPU's have 16-32 **general purpose registers**
- Operands and destination can be in
  - Registers only
  - Registers & 1 memory operand
  - Any combinations of registers and memory
