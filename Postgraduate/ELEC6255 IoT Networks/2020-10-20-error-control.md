# Lecture 5: Error Control

## Error Models

- Singie-bit errors
- Bursts of errors

## Two Strategies

- **Error detection**, then request re-transmission
  - better for fewer errors (FEC introduct overhead)
- **Error correction**, aka Forward Error Correction (FEC)
  - better for many errors (re-transmission introduce overhead)

They may be handled in other layers.

## Redundancy

We embed an ability to detect and / or correct errors by adding redundancy.

```
m + r = n
^   ^   ^
|   |   +- total number of transmitted bits
|   +- redundant check bits
+- data bits
```

This is then known as an **`(n, m)` code** with an **n-bit codeword**:

```
|<-          n bits          ->|
+-----------------+------------+
|     Message     | Check bits |
+-----------------+------------+
|<-   m bits    ->|<- r bits ->|
```

The **code rate** is the fraction of the codeword carrying non-redundant information:

```
m / n
```

- On a noisy channel, a code rate of 0.5 (more redundancy) might be suitable.
- On a reliable channed, a code rate close to 1.0 (less redundancy) might be suitable.

Only a fraction of the `2^n` possible codewords are used: `2^m / 2^n = 2^{-r}`.

## Block, Systematic and Linear Codes

### Block Code

> Any set of input bits (`m`) could be **looked up** in a table to find the corresponding codeword (`n`).

#### Hamming Distance

Hamming distance `d` is the number of bits different between two codewords.

- XOR then count 1s
- **can detect `(d - 1)` errors**
- **can correct `(d - 1) / 2` errors** (round-down for non-integer in digital systems)

### Systematic Code

> The set of input bits (`m`) is **trasmitted alongside** the check bits (`r`).

### Linear Code

> The check bits (`r`) are a **linear function** of the message bits (`m`).

## Error Detection

- **Single Parity Bit**
  - even parity: add a redundant bit to **make an even number of 1**
  - odd parity: **make an odd number of 1**
  - random errors are 50% detected
- **Multiple Parity Bits**
  - break message to `h` rows with length `w` and assign each row a parity bit
    - `r` = `h`
  - still not good for burst errors
- **Interleaved (交错) Parity**
  - generate parity bits in `w`-wide columns after the message
  - `r` = `w`
- **Checksums**
  - _often refers to a set of check bits_
  - typically treats the message as being formed from many `N`-bit words, and adds `N` check bits to the end, which are **the modulo `2^N` sum** of all words
    - **`mod(sum(M), 2^N)`**
    - `r` = `N`
  - more effective than parity
    - detects bursts of up to `r = N` errors, and random errors with probability `1 - 2^N`
  - still vulnerable to...
    - LSBs in two words flips
    - systematic errors, e.g. added zeros, swapping parts of the message
- **Cyclic Redundancy Checks (CRC)**
  - a stronger error detection code
    - can detect all double bit errors
    - not vulnerable to systematic errors
  - easy to calculate / check in hardware as well
    - shift + XOR
  - **treat bit strings as the _coefficients of a polynomial_**
    - _`k`-bit string -> coefficient of a polynomial with `k` terms_
      - `sum(X^{k - 1})`, where `X` is a series of bits
  - the _generator polynomial `G(x)`_ is agreed beforehand
  - the _message (frame) polynomial `M(x)`_ must be greater than `G(x)`
  - the _transmitted `n`-bit message `T(x)`_:
    - has `T(x) % G(x) == 0` when:
      - no error is detected
      - the _error `E(x)`_ is a factor of `G(x)`
    - has `(T(x) + E(x)) % G(x) != 0`

### Fletcher's Checksum

Improves protection against position changes in data. It adds two fields of checksum after a message:

- `A`: `mod(sum(M), 2^w)` (`w` is bit wide of block)
- `B`: `mod(sum(A'), 2^w)`

Example _(`w = 8`)_:

```
                              188   187
                               |     |
   |<           M          >|< |  R  | >|
   |< 8b >|                 |  v     v  |
   +------+-----+-----+-----+-----+-----+
N  | 211  | 11  | 112 | 110 |  A  |  B  |
   +------+-----+-----+-----+-----+-----+
     |      |     |     |      ^     ^
     |   (+)|  (+)|  (+)|      |     |
     |  +---+ +---+ +---+  mod |     |
     |  |   | |   | |   |  2^8 |     |
     v  |   v |   v |   v      |     |
   +------+-----+-----+=====+  |     |
A' | 211  | 222 | 334 [ 444 ]--+     |
   +------+-----+-----+=====+        |
     |      |     |     |            |
     |   (+)|  (+)|  (+)|            |
     |  +---+ +---+ +---+        mod |
     |  |   | |   | |   |        2^8 |
     v  |   v |   v |   v            |
   +------+-----+-----+======+       |
B' | 211  | 433 | 767 [ 1211 ]-------+
   +------+-----+-----+======+
```

https://play.rust-lang.org/?version=stable&mode=debug&edition=2018&gist=7b3a346b253e78c3354812f08f895456

### IEEE 802 and CRC-32

- IEEE 802.3 (Ethernet) uses CRC-32
  - detects:
    - all burst errors of length 32 and less
    - all bursts affecting an odd number of bits
- IEEE 802.15.4 and LoRaWAN use the CCITT (ITU-T) CRC-16

### CRCs and Parity

- Even parity is the same as CRC-1
  - `G(x) = 1x^1 + 1x^0 = (x + 1)` -> `0b11`

## Error Correction

### Hamming Codes

- Can fix single-bit errors
- A fraction of the `2^n` bit patterns (possible codewords) are used
  - `2^m / 2^n = 2^{-r}`
  - other codewords will be illegal then
- **Each of the `2^m` messages must have `n` illegal bit patterns 1 bit away from it**

Example (`M = 1000001, (11, 7) Hamming Code`):

```
 P1  P2  M3  P4  M5  M6  M7  P8  M9  M10 M11
+---+---+---+---+---+---+---+---+---+---+---+
| 0 | 0 | 1 | 0 | 0 | 0 | 0 | 1 | 0 | 0 | 1 | = N
+---+---+---+---+---+---+---+---+---+---+---+
  1   2  2+1  4  4+1 4+2  |   8  8+1 8+2  |
  ^   ^       ^          4+2+1           8+2+1
  |   |   |   |   |   |   |   ^   |   |   |
  |   |   |   |   |   |   |   |   |   |   |
  *-------+-------+-------+-------+-------+ P1 Even Parity
      |   |   |   |   |   |   |   |   |   |
      *---+-----------+---+-----------+---+ P2 Even Parity
              |   |   |   |   |   |   |   |
              *---+---+---+   |   |   |   | P4 Even Parity
                              |   |   |   |
                              *---+---+---+ P8 Even Parity
```

In case of an error happens at `M5 (4+1)`:

```
 P1  P2  M3  P4  M5  M6  M7  P8  M9  M10 M11
+---+---+---+---+---+---+---+---+---+---+---+
| 0 | 0 | 1 | 0 | 1 | 0 | 0 | 1 | 0 | 0 | 1 | = N + E
+---+---+---+---+---+---+---+---+---+---+---+
  1   2  2+1  4  4+1 4+2  |   8  8+1 8+2  |
                         4+2+1           8+2+1

P1 Parity Check FAIL -> 1 ^
P2 Parity Check PASS -> 0 |   Error Syndrome
P4 Parity Check FAIL -> 1 | = 0b0101 = 5
P8 Parity Check PASS -> 0 |

=> M5 flips.
```
