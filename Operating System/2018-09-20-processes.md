# Chapter 3: Processes

- **Process**: a program in execution
  - **Text section**: the program code
  - **Program counter**: current activity
  - **Stack**: temporary data
  - **Data section**: global variables and static variables
  - **Heap**: dynamically allocated memory

## State

- New
- Running
- Waiting
- Ready
- Terminated

## Process Control Block (PCB)

aka **task control block**: information associated with each process

- Each process in memory has a corresponding unique PCB in the kernel

## Threads

In Chapter 4!

## Process Scheduling

- **Process scheduler** selects among available processes for next execution on CPU core
  - Maintaining scheduling queues:
    - **Ready queue**
    - **Wait queues**

## Context Switch

![](./img/context-switch-silde.png)
