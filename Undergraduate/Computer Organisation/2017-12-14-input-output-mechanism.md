# Lecture 12: Input / Output Mechanism

## I/O Programming Interface

- **Special Instructions** vs. **Memory-Mapped**
  - Special Instructions: Designate insns for I/O, registers encoded in
  - Memory-Mapped: Assign a memory addr to each device register, use **LD/ST**
- **Synchronous** vs. **Asynchronous**
  - Synchronous: Data supplied at a fixed rate
  - Asynchronous: Data less predictable
- **Polling _(CPU Controls Transfer)_** vs. **Interrupts _(Device Controls Transfer)_**
  - Polling: Keep querying...
  - Interrupts: Device send a special signal to CPU, then CPU perform tasks

## LC-3 I/O

LC-3 uses:

- Memory-Mapped
- Asynchronous
- Polling

for I/O. **xFE00 - xFFFF** are reserved for I/O registers:

| Location  | I/O Register                                    |
| --------- | ----------------------------------------------- |
| **xFE00** | Keyboard Status Register (**KBSR**)             |
| **xFE02** | Keyboard Data Register (**KBDR**)               |
| **xFE04** | CRT (Display) Status Register (**CRTSR / DSR**) |
| **xFE06** | CRT (Display) Data Register (**CRTDR / DDR**)   |

### Keyboard I/O

- When a character is typed:
  - Its ASCII code is stored in **KBDR[7: 0]**
  - **KBSR[15]** = 1 _(Negative)_
  - _CI_
- When KBDR is read:
  - **KBSR[15]** = 0
  - _EI_

### Screen I/O

- When the display is ready to display a character:
  - **CRTSR[15]** = 1 _(Negative)_
  - _EI_
- When data is written to CRTDR:
  - **CRTSR[15]** = 0
  - Display **CRTDR[7: 0]**
  - _CI_

### KBDR / CRTDR

| [15: 8]    | [7 : 0]           |
| ---------- | ----------------- |
| Unused (0) | **Keyboard Data** |

### KBSR / CRTSR

| 15            | [14: 0]    |
| ------------- | ---------- |
| **Ready Bit** | Unused (0) |

## Priority

Every instruction executes at a stated level of urgency. LC-3 has **8 priority levels (PL0 - PL7)**.

- **PL6** program can interrupt **PL0**
- Not the other way around

**Priority encoder** selects highest priority device, compares to current processor priority level, and generates interrupt signal if appropriate.
