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

![Abstract View of the components of a Computer System](/resources/images/intro_to_comp_systems/Abstract_view_of_comp_sys.PNG)

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

<hr>

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

#### Registers

- Architecture Rule : Large memories are slow and smaller ones are faster
- Most programs work on only small chunks of memory in a given time period. This is called **locality**
- Most CPU's have 16-32 **general purpose registers**
- Operands and destination can be in
  - Registers only
  - Registers & 1 memory operand
  - Any combinations of registers and memory

<hr>

## Process Management

  - A **process** is a program in execution. It is a unit of work within the system. Program is a **passive** entity, process is an **active** entity.
  - Typically a system has many processes, some user, some operating system running concurrently on one or more CPU's

## Memory Indirection

  - How do we access array elements efficiently if all we can do is name a cell?
    - Modify the operand to allow for fetching and operand "through" a memory location
  - This is called indirection

## Abstracting the machine

- Bare hardware provides a computation device
  - How can multiple uses share the expensive hardware between themselves?
  - Answer: Software is to give the illusion of having it all to yourself while actually sharing it with others.
- This software is the **Operating System**.

## Traps

- A way that the user can legitimately access kernel processes(such as init)
- This is also the basis of a **system call**
  - Interaction between the user and kernel is done via system calls. Each system call is providing one defined service. The user sends the service name (usually a number) and the required parameters.

## System calls

- Programming interface to the services provided by the OS
- Typically written in a high-level language (C or C++)
- Mostly accessed by programs via a high-level **Application Programming Interface(API)**
- The OS will transform certain commands, such as fread and fwrite, into the system calls of read and write

## Interrupts

- Force the CPU back into system mode if the user program is off computing something
- An external event which causes the CPU to jump to a known address
- Types of Interrupts
  - Hardware - Generated by hardware devices(e.g. keystrokes for user, or data on Ethernet card)
  - Software - Generated by programs when they want to request a system call to be done
  - Traps - Generated by the CPU to indicate some error or condition, where the OS is needed
- Interrupts are commonly used for polling the system hardware(e.g. registers, input, screen, etc.)

## Examples and classifications of interrupts

- Interrupts(Hardware & Software)
  - Hardware Interrupts
    - I/O
    - Network
    - Failures
  - Traps
    - Software - system calls
    - Normal Operations - multi-programming Operations
    - OS needs
    - Multi-layer requirements
  - Exceptions
    - Division by 0
    - Wrong memory access

## Input and Output

- To get user input and display output to the user
- A network card(example of an I/O device) - has 2 registers
  - A store into the "transmit" register sends the byte over wire
    - Often written as "TX"
  - A load from the "receive" register reads the last byte which was read from the wire
    - Often written as "RX"
- These registers are said to be **memory-mapped**
  - This allows the CPU to access the registers
- Reserving specific registers for devices has 2 uses
  - Allows protected access - Only the OS can access the device
  - OS can control devices and move data to/from devices using regular load and store instructions
- This is called **Programmed I/O** - having dedicated registers per device where the OS can interact with the device. The CPU polls to check the status registers to see an input or output.

## Status Registers

- A status register holds the state of the last I/O register
- The network card has 1 status register
  - To transmit, the OS writes a byte into TX and changes bit 0 of the status register to 1
  - When the card receives a byte, it puts the byte in RX and sets bit 1 of the status register back to 0

## Input driven I/O

- Polling can waste many CPU cycles -> a way to solve this is to use interrupts
  - The CPU does not have to check every time for input or Output
  - When the machine gets an input or output, the device can call an interrupt
- Interrupts have a high overhead
  - Stop the processor
  - Figure out what caused the interrupt
  - Save the user state
  - Process Request
- Interrupts take several instructions(overhead), but take less CPU cycles. Polling takes more CPU cycles, but takes less instructions(overhead)

## Direct Memory Access(DMA)

- Problem with programmed I/O : the CPU must load/store all the data into device registers
- Solution: Add more hardware to allow the device to read and write memory just like the CPU
- PIO has less overhead than DMA, however DMA is more efficient at moving data
- The DMA will cause an interrupt when the CPU is needed

#### Difference between DMA and PIO

- In PIO the CPU polls the status register to see when it is needed, however the DMA will not need polling and cause an interrupt when it needs the CPU

## How the machine boots

- The process of starting the OS is called **booting**
- Boot protocol in modern machines is a 3-stage process
  1. CPU starts executing from a fixed address
  2. Firmware loads the boot loader - ROM contains the "boot" code
  3. Boot loader loads the OS

## Microkernel System Structure

- Moves as much from the kernel to user space
- Mach is an example of Microkernel
  - Mac OS X kernel is partially based on Mach
- Communication takes place between user modules using message passing

## Operating System Services

- Program Execution
- I/O Operations
- File Systems
- Communication
- Resource Allocation
- Accounting
- Error Detection
- Protection and Security
- GUI (Graphical User Interface)
- CLI (Command Line Interface)
- Batch

## Modules

- Many modern Operating Systems implement **loadable kernel modules**

## Memory allocation

- When a program is put in the "ready" queue for the OS, the OS will allocate and make the program into a process
  - The difference between a program and a process is that, a program is a set of instructions, but a process is running and has memory allocated to it which it is executing the lines of the program

- Each variable must be assigned a storage class
- Global (static) Variables
  - Allocated in the "Globals" region at compile
- Method local variables and parameters
  - Allocate on stack
- Dynamically created objects
  - Allocate from heap
  - Objects live beyond invocation of a method if the memory is not freed
  - Garbage collected when no longer "living"
- The pointer to the next instruction to be executed is stored in a special register called PC(Program Counter)
  - Variables are also cached in registers

## Processes

- What is a Process?
  - A system abstraction for the set of resources required for executing a program
  - A running instance of a program
- The OS maintains the process state per process:
  - Identification: processes, parent, user, group, etc.
  - Execution Contexts: registers, Threads
  - Address Space: Virtual Memory
  - I/O State: file handles(file system), communication endpoints(network), etc.
  - Accounting Information
- For each process, the state is maintained in a *process control block(PCB)*
  - This is just data in the OS data space
  - The process control block can also be called a *Process Table*

#### Process Creation
- How to create a process?
  - System call - fork();
- In UNIX, a process can create another process using the fork() system call
  - An example of the fork command is

```C
//Creates a new process
//Fork returns the Program ID of the child process to the parent process
int pid = fork();
```

- The creating process is called the parent and the new process is called the child
  - The fork will return the PID of the child process to the parent and will return a 0 to the newly created process
- The child process is created as a copy of the parent process(process image and process control structure) except for the identification and scheduling state
  - The parent and the child processes run in two different address spaces
  - By default, the memory is not shared between parent and child
  - Process creation is expensive because of this copying of the parent process
- The exec() call is provided for the newly created process to run a different program than that of the parent
  - The exec() command is a system call to issue a command for the process to run

- Example code in C using fork()

```C
while(true){
  get_command(command, parameters);

  if(fork() != 0){  //Parent
    wait(&status);
  }else{            //Child
    exec(command, parameters);
  }
}
```

- One process can wait for another process to finish by using the wait() system call
- In the program above, the main function gets a command, and then spawns a process to execute the command
  - The wait(&status) line forces the parent to wait for the child to finish before the parent finishes

#### Signals

- User programs can invoke OS services by notifying by using system calls
- What if the program wants the OS to notify it asynchronously when some event occurs?
  - Signals - UNIX mechanism for OS to notify a user program when an event of interest occurs
- When an event of interest occurs
  - Kernel handles it first
  - Then modifies the process's stack to look as if the process's code made a procedure call to the signal handler
  - Puts an activation record on the user-level stack corresponding to the event handler
- When the user process is scheduled next it executes the handler first
- From the handler the user process returns to where it was when the event occurred

#### Schedulers

- Short term scheduler - CPU scheduler - selects which process should be executed next and allocates CPU
  - Sometimes the only scheduler in a system
  - Short-term scheduler is invoked frequently
- Long term scheduler - Job scheduler - selects which processes should be brought into the ready queue
  - Long term scheduler is invoked infrequently
  - The long term scheduler controls the degree of multi-programming
  - Strives for a good mix of types of processes
- Types of Process can be described as either:
  - I/O bound processes - spends more time doing I/O than computations, many short CPU bursts
  - CPU-bound processes - spends more time doing computations, very few long CPU bursts

#### Process Termination

- Some operating systems, don't allow children to exist if it's parent has terminated
  - Done through cascading termination - all children and sub-children are terminated
- Sometimes, parent process can finish and exit before the child if a wait statement is not used
  - This creates a zombie process - a process that was never properly terminated
- To kill a process, we can use the kill() command by giving it the PID of the process to kill
