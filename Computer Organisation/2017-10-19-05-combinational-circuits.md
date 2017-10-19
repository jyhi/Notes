# Lecture 5: From Gates to Circuits I: Combinational Circuits

## Basic Building Blocks

- AND
- OR
- NOT
- NAND
- NOR
- XOR

## Universal Gate

**Any electronic circuit can be constructed using only _NAND_ gates.**

## Integrated Circuits (IC)

![IC](./img/ic.png)

### Two Types of Circuits

- **Combinational logic circuits**
  - Its output depends solely on its current input.
  - _No storage, memoryless_
- **Sequential logic circuits**
  - Its output depends not only on its current input, but also on its _current state (previous input)_
  - _Can remember previous input, storage devices_

## Binary Addition

### Half Adder

![Half Adder](./img/half-adder.png)

- S = xor(x,y)
- C = and(x,y)

![Half Adder Circuits](./img/half-adder-diagram.png)

### Full Adder

![Full Adder](./img/full-adder.png)

z is **Carry-In**.

![Full Adder Circuits](./img/full-adder-diagram.png)

### Ripple-Carry Adder

![Ripple-Carry Adder](./img/ripple-carry-adder.png)

**Very slow.**
