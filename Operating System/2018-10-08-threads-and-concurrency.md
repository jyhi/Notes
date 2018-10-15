# Chapter 4: Threads & Concurrency

Process creation is heavy-weight while thread creation is light-weight.

![Multithreading](./img/multithreading.png)

## Benefits

- Responsiveness
- Resource sharing
- Economy
- Scalability

## Multicore Programming

- Multicore or multiprocessor systems putting pressure on programmers, challenges include:
  - Dividing activities
  - Balance
  - Data splitting
  - Data dependency
  - Testing and debugging
- **Parallelism** implies a system can perform more than one task simultaneously
- **Concurrency** supports more than one task making progress
  - Single processor / core, scheduler providing concurrency

![Concurrency vs. Parallelism](./img/concurrency-vs-parallelism.png)

## Amdahl's Law

**Speedup <= 1 / (S + (1 - S) / N)**

(Not `=`, extra communication required between threads)

## User Threads and Kernel Threads

- User threads
  - No system call required
  - A process with only one thread gets as much CPU time as a process with many threads.
- Kernel threads
  - No need for threads to cooperate for scheduling
  - Every thread management operation requires a system call so slower compared to user-level threads

## Multithreading Models

- Many-to-one (seldom used)
- One-to-one
- Many-to-many

`fork()` Schematics:

- Does `fork()` duplicate only the calling thread or all threads?
  - Some UNIXes have two versions of fork

## Thread-Local Storage (TLS)

- Useful when you do not have control over the thread creation process
- Different from local variables
  - Local variables visible only during single function invocation
  - TLS visible across function invocations
- Similar to `static` data
  - TLS is unique to each thread
