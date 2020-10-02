---
layout: notes
title: "Number Systems"
date: 2016-10-12
categories: notes it
---

## Vocabulary:

- radix:        基数
- addressable:  可寻址的
- minuend:      被减数
- subtrahend:   减数
- remainder:    余数
- complement:   补集
- Hindu-arabic: 阿拉伯数字的

> **BIT** = Binary digIT

## Decimal Number System

- 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 **(0 - 9)**
- aka. **"base-10"**

## Binary Number System

- 0, 1
    - 0 stands for off (low)
    - 1 stands for on (high)
- aka. **"base-2"**

### Why Binary System?

- Computer is a binary machine, knows only 0 and 1
- Easy to implement
- Reliabor
- Cheep

## Hexadecimal Number System

- 0 - 9, A, B, C, D, E, F
- aka. **"base-16"**

### Why Hexadecimal?

- A byte is composed of 8 bits
- **One byte can be expressed by 2 digits in Hexadecimal:**

![Why Hex](https://latex.codecogs.com/svg.latex?(11101111)_2\\rightarrow(EF)_h)

## Positional Number System

The value of a digit in a number depends on:

- The digit itself
- The position of the digit within the number

## Base `r` Number System

- `r` symbols (?)
- Value is based on the sum of a power series in powers of `r`:

![Base `r` # Sys](http://latex.codecogs.com/svg.latex?(d_{n-1}d_{n-2}...d_0)=\\sum_{i=0}^{n-1}d_i\\times{r^i})

## Octal Number System

- 0 - 7
- aka. **"base-8"**

![Octal # Sys](http://latex.codecogs.com/svg.latex?N=(d_{n-1}d_{n-2}...d_0)_8=\\sum_{i=0}^{n-1}d_i\\times{8^i})

## Bit & Byte

**1 Byte = 8 bits**

| **MSB** | 0 | 0 | 1 | 0 | 0 | 1 | 1 | 1 | **LSB** |
| :------------------------------------------------ |
|         | b7| b6| b5| b4| b3| b2| b1| b0|         |

- **MSB: Most Significant Bit**
- **LSB: Least Significant Bit**

## Conversion

### Decimal to `r` Number System

**Read remainders from bottom to top.**

- DEC to BIN:
```
2 | 28 ... 0 ^
2 | 14 ... 0 |
2 | 7  ... 1 | => 11100 in BIN
2 | 3  ... 1 |
2 | 1  ... 1 |
  | 0
```

- DEC to OCT:
```
8 | 28 ... 4 ^
8 | 3  ... 3 | => 34 in OCT
  | 0
```

- DEC to HEX:
```
16 | 28 ... C ^
16 | 1  ... 1 | => 1C in HEX
   | 0
```

Thus,

![Dec to r](http://latex.codecogs.com/svg.latex?(28)_{10}=(11100)_2=(1C)_{16}=(34)_8)

## Conversions Between Power-of-2 Radices

- A group of 4 bits is easily recognized as a Hexadecimal number;
- A group of 3 bits is easily recognized as a Octal Number.

![2a9fhex](http://latex.codecogs.com/svg.latex?(2A9F)_h=0010\\ 1010\\ 1001\\ 1111)

![4726oct](http://latex.codecogs.com/svg.latex?(4726)_8=100\\ 111\\ 010\\ 110)

**To convert 4726(OCT) into HEX, we just re-group the BIN value:**

![4726oct2hexobin](http://latex.codecogs.com/svg.latex?(2A9F)_h=1001\\ 1101\\ 0110=(9D6)_h)

## Rules of Binary Arithmetic

### Addition (Omit)

### Subtraction

- 1 - 0 = 1
- 1 - 1 = 0
- 0 - 0 = 0
- 0 - 1 = 1 (borrow 1 from the next MSB)

## Binary Representation of N (In Computer Memory)

- Positive value & Zero: **MSB = 0**
- Negative value:
  - Use *2's complement*
    - Convert the absolute value of N into BIN
    - Invert the BIN
    - Add 1
