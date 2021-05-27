# Elliptic Curves

Elliptic Curves (ECs) have a natural abelian group structure.

    E: y^2 = x^3 + ax + b

- also includes a _point of infinity_

## Restrictions

    4 a^3 + 27 b^2 <> 0

i.e. an EC with double (2) root cannot be used to construct a cryptographic system. (3 roots are required)

## Addition

Given two points, `P` and `Q`, and `P <> -Q`. Draw a line through the two points, the line will intersect with the EC at `-R`. `R` is reflected from `-R` on the x-axis.

    P + Q = R

For `R = (Xr, Yr)`:

- `Xr = L^2 - x1 - x2`
- `Yr = -y1 + L(x1 - xr)`

... where

- `L = (y2 - y1) / (x2 - x1)`

### Point of Infinity

The line through `P` and `-P` is vertical and does not intersect with the EC. Thus, the _point of infinity_ `O` is:

    O = P + (-P)

As a result:

- `P + O = P`
- `O` is the _addictive identity_ of the EC group

### Doubling the Point

- Case 1: `yp <> 0`: draw a tangent line at `P`. The line will intersect with the EC at `-R`. `R` is reflected from `-R` on the x-axis.

    2P = P + P = R

For `R = (Xr, Yr)`:

- _`Xr = L^2 - 2 x1`_
- `Yr = -y1 + L (x1 - xr)`

... where

- `L = (3 x1^2 + a) / (2 y1)`
^
- Case 2: `yp == 0`: a tangent line at `P` will be vertical. In this case:

    2P = O

## Elliptic Curve over `Zp`

    4 a^3 + 27 b^2 <> 0 (mod p)

### Find All Points of EC over `Zp`

1. For each element `e` in `Zp`, list `e -> e^2`
2. For each element `x <- e` in `Zp`, list `y^2`
3. From step 1, determine if `y^2` in step 2 has square roots in `Zp`

## Properties

- **Order**: (`|E|`) number of points on the curve, plus `O`
  - _Hasse's Theorem_: `p + 1 - 2 sqrt(p) <= |E| <= p + 1 + 2 sqrt(p)`
    - using a large field guarantees a large elliptic curve!

## EC Discreate Logarithm Problem

Given two points, `P` and `Q`, and an EC `E` over `Zp`. Find an `i` satisfying:

    Q = i P

The security of ECC depends on the difficulty of determining `i` given `iP` and `P`.

## ECDH Key Exchange

Public knowledge: a group `E(Zp)` and a _generator point_ `G` of order `n`.

| Step | Alice | Bob |
|-|-|-|
| 1 | Choose secret `0 < a < n` | Choose secret `0 < b < n` |
| 2 | Compute `Qa = aG` | Compute `Qb = bG` |
| 3 | Send `Qa` to Bob `->` | `<-` Send `Qb` to Alice |
| 4 | Compute `a Qb` | Compute `b Qa` |
| 5 | `a Qb = a b G` | `b Qa = a b G` |

## EC Elgamal Encryption

Suppose Alice wants to send a message `m < n` to Bob:

1. Perform ECDH
2. Choose a random `0 < k < n`
3. Compute `k . Qb = k . a . G = Qshared = (x, y)`
4. Send `C1 = kG`, `C2 = x . m (mod p)`

Bob's decryption:

1. Compute `a . C1 = a . k . G = Qshared = (x, y)`
2. Compute `x^{-1}` in `Zp`
3. Compute `x^{-1} C2 = x^{-1} . x . m (mod p) = m`
