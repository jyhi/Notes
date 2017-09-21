# Lecture 1: What is a Computer

## Definition of Computer

- A modern computer is an **electronic, digital, general purpose** computing machine that automatically follows a **step-by-step list of instructions** for solving a problem.
- This step-by-step list of instructions taht a computer follows is also called a **computer program**.

## The Turing Machine

_Abstract model of all computers_

A Turing Machine Consists of:

- A **type** divided into cells;
- A **moving read / write head**
- A **state register** storing the state of the Turing Machine
- A **finite table of instruction** specifying what the machine does when reading the content of the current cell:
  - Move left / right;
  - Erase / write a symbol;
  - Change the state.

## The Church-Turing Thesis

**All things that can be computed can be computer by a Turing Machine.**

## Universal Turing Machine (**UTM**)

Turing described a Turing machine that **could simulate all other Turing machines**:

- Inputs: Data + A description of computation (Turing machine)
- **Programmable**
- _**A computer is a Universal Turing Machine**_

## The von Neumann Architecture

- aka **stored-program architecture**
- Both data and program are stored in the memory

### The stored-program architecture

- **CPU**
  - Control Unit
  - Arithmetic Logic Unit (**ALU**)
  - Registers
- Main Memory
- I/O System
- A single path between the main memory and CPU, called the **von Neumann bottleneck**
