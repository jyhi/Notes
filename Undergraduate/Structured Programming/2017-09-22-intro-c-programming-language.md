# Lecture 1: C Programming Language

## Natural Languages

- Recognized by **human beings**
- To define a natural language, we need to define:
  - **Vocabulary (spelling)**
  - **Syntax (grammar)**
  - **Semantics (meaning)**

## Programming Languages

- Recognized by **computers**
- To define a programming language, we need to define:
  - **Grammar (vocabulary)**
  - **Semantics**

## Evolution of Programming Languages

- Machine Language
- Assembly Language
- Advanced Language

### Machine Language

- A CPU accepts instructions in machine language
- An instruction consists of 0s and 1s (binary number)
- Difficult for human to understand

### Assembly Language

- An assembly language uses symbols to represent the machine language instructions
- An **assembler** is needed to translates symbolic code into machine language

### Advanced Language

- Closed to natural languages
- A **compiler** is needed to translate high level language programs into machine language instructions

## Structured Programming

- C _is_.
- A program is made up of functions
  - One **main** function (compulsory)
  - Sub-functions (optional)

## Our First Program ~~(Not for me.)~~

```c
/* Our first program */
#include <stdio.h>
int main(){
  printf("\nHello World!\n");
  return 0;
}
```

### Preprocessor

```c
#include <stdio.h>
```

- Used to tell compiler infomation used in compiling
- `stdio.h`: **Header file**

### Comments

```c
/* Our first program */
```

- Used to explain... <!-- shits. -->
- Two ways to insert comments:
  - `//` (double dash)
    - **Single line** comment
  - `/*  */`
    - **Multiple lines** of comments
  - Compiler will ignore comments

### Main Fuction

```c
int main()
```

- All programs written in C must have a mian function
  - `main`: function name
  - `int`: function return type
- Part between `{` and `}` is called body of function

### Statements

```c
  printf("\nHello World!\n");
  return 0;
```

- A statement is an instruction telling a computer **what to do**
- A simple one ends with `;`
- A compound statement includes a sequence of Statements or conditions

### Indentation

<!-- this code very fast
int main(){printf("\nHello World\n");return 0;}
-->
