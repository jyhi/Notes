# Lecture 2: Primary Data Types And Variables

---

**NOTE**: I notice something wrong. Those data type lengths are actually **REALLY DEPENDENT ON IMPLEMENTATIONS.**

On Windows, data types are using **LLP64 (long long and pointer are 64-bit)** model:

| Data Type | char | short | int     | long   | long long | pointer |
| --------- | ---- | ----- | ---     | ----   | --------- | ------- |
| Length    | 8    | 16    | **32**  | **32** | 64        | 64      |

On Linux, data types (typically) are using **LP64 (long and pointer are 64-bit)** model:

| Data Type | char | short | int     | long     | long long | pointer |
| --------- | ---- | ----- | ---     | ----     | --------- | ------- |
| Length    | 8    | 16    | **32**  | **64**   | 64        | 64      |

And **`int` are all of 32-bit size (this is also dependent on implementations, in ILP64 (integer, long and pointer are 64-bit) model `int` is of 64-bit long)**

So actually you will get `sizeof (int) == 4` and `sizeof (void *) == 8` on 64-bit (Windowd, Linux and Unix (macOS) systems.

- https://en.wikipedia.org/wiki/64-bit_computing#64-bit_data_models
- http://www.unix.org/version2/whatsnew/lp64%5Fwp.html

---

## `int`

- Used to express the integer type.
- The biggest integer that can be expressed in a computer depends on the host computer
  - 32 bits or 64 bits <!-- ??? -->

### `short int`

2 Bytes

### `long int`

4 Bytes

## `char`

Used to express the single characters. Each character corresponds to an integer between 0 and 127

## `float`

Real number (single precision float point)  

## `double`

Real number (double precision float point)

## `bool`

A Boolean value which takes value 0 or 1.

---

Can't be bothered to keep writing those dumb notes, go fetch slides.

---

## Type Conversion

- C allows for conversions between the basic types, implicitly or explicitly.
- Explicit conversion uses the cast operator:

```c
int x = 10;
float y = 3.14;

x = (int) y;   // This *truncates* decimal numbers (x = 3)
y = (float) x; // y = 3.0
```

- If the compiler expects one type at a position, but another type is provided, then implicit conversion occurs.
