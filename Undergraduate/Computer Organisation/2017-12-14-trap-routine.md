# Lecture 13: Trap Routines

**System Calls** for safe and convenient low-level, privileged operations.

- Information handling
- Code reuse
- Security

## The Trap Mechanism

- A set of **trap service routines (TSRs)**
- A **trap vector table** or **system control block**
  - In LC-3: **x0000 - x00FF**, up to 256 entries, only 5 in use

Instruction **TRAP** loads the starting address of TSR into **PC**.

## LC-3 Trap Routines

- **GETC (TRAP x20)**
- **OUT (TRAP x21)**
- **PUTS (TRAP x22)**
- **IN (TRAP x23)**
- **HALT (TRAP x25)**

## TRAP Instruction

| TRAP     |      | TrapVect8 |
| -------- | ---- | --------- |
| **1111** | 0000 | 10001000  |

- **R7** = **PC**
- **PC** = \*(SEXT(TrapVect8))
  - The service routine must not touch **R7**...
