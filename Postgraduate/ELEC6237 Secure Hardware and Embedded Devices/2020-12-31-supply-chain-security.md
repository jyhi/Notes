# Supply Chain Security

## Design Principles

- Combinational logic: `Output = f(In)`
  - has no memory (output changes immediately when input changes)
- Sequential logic: `Output = f(In, Previous In)`

### State Machine Model

- Values stored in registers are the **state** of the circuit
- The combinational circuit computes:
  - the next state
  - the outputs
    - a function of current state _and inputs_: Mealy Machine
    - a function of current state _only_: Moore Machine

Assigning binary codes to states: **Gray Coding** reduces transition and saves dynamic power consumption.

## Design for Trust

- Include comprehensive specs for **every single state** in the circuit

## IC Fingerprinting

The _Satisfactory Don't Care (SDC)_ approach: utilise a combination that can never happen to detect modifications.
