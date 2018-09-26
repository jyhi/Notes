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

## Process Creation

- **Parent** process creates **children** processes, forming a **tree**
- Processes are identified and managed via **process identifier (PID)**
- Resource sharing options
  1. Parent and children share all resources
  2. Children share subset of parent's resources
  3. Parent and child share no resources
- Execution options
  1. Parent and children execute concurrently
  2. Parent waits until children terminate

On UNIX:

1. `fork()` syscall creating a new process
2. `exec()` syscall replacing the process' memory space
3. `wait()` syscall for the parent to wait the children

## Process Termination

- `exit()` ask the operating system to delete it
- `abort()` for rare things
- **Cascading termination**
- If no parent is waiting and the child dies, the child process becomes a **zombie**
- If parent terminated without involking `wait`, the child process becomes an **orphan**
