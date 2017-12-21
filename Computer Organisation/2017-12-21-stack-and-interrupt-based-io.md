# Lecture 14: Stack and Interrupt-Based I/O

_NOTE: **R6** is **Stack Pointer (SP) in LC-3.**_

## Stack

- **LIFO (Last In First Out)**
- Stack operations:
  - **PUSH**: insert item at the top of stack
  - **POP**: remove item from the top of stack
- Error conditions:
  - **Overflow**: trying to push onto a full stack
  - **Underflow**: trying to pop from an empty stack
  - _Typically use **R5** to report condition_

## State of Program

- A "snapshot" of the system:
  - The content of relavent memory locations
  - The general purpose registers
  - Some special registers, incl. **PC**, **PSR (Process Status Register)** (which stores the most important pieces of information about the current program)

### Process Status Register

| 15 | 14 - 11 | 10 - 8 | 7 - 3 | 2 | 1 | 0 |
| -- | ------- | ------ | ----- | - | - | - |
| P  |         | PL     |       | N | Z | P |

- **P** (PSR[15]): Privilege
  - **0**: Supervisor mode
  - **1**: User mode
- **PL** (PSR[10: 8]): Priority
  - 8 Levels: **PL0 - PL7**
- **N, Z, P** (PSR[2: 0]): Condition Codes

## Saving the State of Interrupted Program

- Save **PC** and **PSR** on a stack

### The Supervisor Stack

- In a separate region of memory
- **R6 (SP)** points to the supervisor stack when in privilege mode
- Two special purpose registers, **Saved.SSP (Supervisor SP)** and **Saved.USP (User SP)** are used to store the pointer currently not in use

## RTI

_Return From Interrupt_

| RTI      | Unused       |
| -------- | ------------ |
| **1000** | 000000000000 |

- Pop **PSR** and **PC** from the supervisor stack
- Restore condition codes from **PSR**
- If necessary (i.e. the current privilege mode is User), restore **R6 (SP)** from **Saved.USP**

## Interrupt Vector Table

- **x0100 - x01FF**
  - Lower half (**x0100 - x0180**, 256 entries) contains the starting addresses of **exception service routines**
  - Higher half (**x0180 - x01FF**, 256 entries) contains the starting addresses of **interrupt service routines**
