# Chapter 6: Synchoronization

## Critical Section Problem

- Designed to solve the problem _Race Condition_
  - _Thread-safe_ if it does not have race condition
- Any piece of code that must be executed by **at most one process at a time**
- Each process:
  - _Must_ ask permission to enter critical section with **entry section**
  - _May_ follow critical section with **exit section**
  - Then **remainder section** (?)

```c
do {
  // [entry section]
    // critical section
  // [exit section]
    // remainder section
} while (true)
```

Solutions:

- **Mutual Exclusion**
  - If process `i` is executing in its critical section, then **no other processes** can execute their critical sections
- **Progress**
  - Each process enter their critical sections one after one
  - Being nice to each other (?)
- **Bounded Waiting**
  - There is a bound of **1** time allowed for process `i` to enter the critical section **before process `j` is finished**
    - Because when `j` finishes, it gives the chance to `i` immediately
  - `i` is guaranteed to be able to enter the critical section _at some point in the future_ (right after `j` is finished)
  - ?

> Philippe says:
>
> Suppose you and your friend are having one bowl of rice with only one spoon.
>
> - Mutual exclusion is about when your friend is eating, _can you eat?_
> - Progress is about when your friend keeps eating, _do you have the chance to eat?_
> - Bounded waiting is about when your friend is hungry and eats a lot, _can you still eat from time to time?_

## Peterson's Solution

- **This assumes `load` and `store` instructions are _atomic_**
  - When process `i` and `j` try to give chance to each other:
    - The hardware will either `load` or `store`
- Two processes sharing 2 variables:
  - **`int turn`**: Indicate **whose turn it is** to enter the critical section
    - Provides _Mutex_
  - **`bool flag[2]`**: Indicate if a process is **ready** to enter the critical section
    - Provides _Progress_
- Even when `j` is much faster than `i`, it is impossible for `j` to beat `i`
  - Provides _Bounded Waiting_

```c
do {
  flag[i] = true;
  turn = j;
  while (flag[j] && turn == j) {}
    // critical section
  flag[i] = false;
    // remainder section
} while (true);
```

- Correct sulution!
- But not used because of the _busy waiting (while loop)_

## Synchronization Hardware

- Uniprocessor disables interrupt during critical section processing
- Multiprocessor provides special instructions (atomic ones)
  - Either _test memory_ or _set memory_ in one atomic instruction
  - Or _swap memory words_ in one atomic instruction

```c
do {
  // [acquire lock (hardware operation)]
    // critical section
  // [release lock (hardware operation)]
    // remainder section
}
```

## `test_and_set`

Definition in C (just an explanation):

```c
bool test_and_set(bool *target) {
  bool rv = *target; // old lock
  *target = true;
  return rv;         // old lock is returned
}
```

This is executed by CPU as a single instruction.

### Using `test_and_set`

```c
do {
  while (test_and_set(&lock)) {}
    // critical section
  lock = false;
    // remainder section
} while (true)
```

This algorithm provies:

- Mutal Exclusion
- Progress
- Busy-Waiting

And no Bounded Waiting.
