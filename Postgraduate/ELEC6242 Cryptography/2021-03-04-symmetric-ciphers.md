# Symmetric Ciphers

> "A signal that is totally predictable carries no information."
>
> Shannon (1948)

A system contains `n`-bits of information if it contains `2^n` possible characters.

## Information and Entropy

Consider an information source with a set of symbols `ai`, where each of the symbol occurs in the data with probability `pi`.

**Entropy**: how much information is encoded in a message.

    H(X) = SUM(pi * log_2(1 / pi))

The minimum **bits needed to binary encode a message**:

    B = n * H(X)

## Kirchoff's Principle

> "The cipher must not depend on the secrecy of the mechanism, it must not matter if it falls into the hands of the enemy."
>
> (1883)

## Shannon Perfect Secrecy

> "Ciphertext reveals no information about the plaintext."
>
> Shannon (1949)

A cipher `(E, D)` over `(K, M, C)` has perfect secrecy if... (see slides) no _ciphertext-only_ attack is possible (but other attacks may be possible).

Problems:

- **Too strong to be useful**
- Only related to ciphertext-only attacks

Solution: _relax_ the notion from information-theoretic secrecy to **computational secrecy**: no **efficient algorithm** can break the cipher. However, this also assumes that an attacker can only observe the ciphertext.

## Deterministic vs. Random Functions

- A function `D` is said to be **deterministic** if it always produces the same output when the input does not change.
- A function `R` is said to be **random** if it may produce different outputs for the same input.

## PRPs and PRFs

- **Pseudo-Random Function (PRF)**: `F: K * X -> Y`
- **Pseudo-Random Permutation (PRP)**: `E: K * X -> X`
  - _Deterministic_
  - One-to-one
  - Examples:
    - 3DES: `X = {0, 1}^64`, `K = {0, 1}^168`
    - AES: `K = X = {0, 1}^128`

Functionally, any PRP is also a PRF: A PRP is a PRF where `X = Y` and is efficiently invertible.

## Ideal Block Cipher

**Truly random permutation**: each block consists of `2^N` "characters"; permutation wires one set of "characters" to another set.

An ideal block cipher would allow us to use any of the `2^N` mappings.

- The key space is extremely large...
- A secret key of size `log2({2^N}!)` bits is required

If `N = 64`, then `log2({2^64}!) ~= 10^11 GB`... infeasible!

## Shannon's Confusion and Diffusion

Claude Shannon suggested using both substitution and permutation blocks:

- **Confusion** is done by **substitution**: obscures the relationship between ciphertext and plaintext
- **Diffusion** is done by **permutation**: removes the redundancy of plaintext

## Feistel Structure

Horst Feistel proposed an approach to avoid the complexity of ideal block ciphers: **the execution of two or more simple ciphers in sequence** leads to a more cryptographically secure solution.

### Implementation of a Feistel Cipher

Key parameters:

- **Block size**: the larger, the more secure, the slower.
- **Key size**: same as block size trade-offs.
- **Number of rounds**: each round adds more security. 16 is considered standard.
- **Subkey generation**: the more complex, the more secure.
- **Round function**: the more complex, the more resistance to cryptanalysis.

## DES

DES is a Feistel Cipher with 16 rounds, 64-bit block size, 56-bit long key.

The round function is specific to DES; refer to the slides.

### The Choice of S-boxes and P-boxes

A random S-box or P-box may lead to insecure cipher, since they may be close to a linear function, allowing key recovery

## Triple-DES with Two Keys

    C = E_{K1}(D_{K2}(E_{K1}(P)))

a.k.a. EDE encryption. The reason for this design is mainly for backward compatibility.

Why not 2-DES: **Meet-in-the-middle attack**

- It takes `2^57` steps in 2-DES, not much more than attacking 1-DES.
- It takes `2^55 * 2^56 = 2^111` steps in 3-DES.

## AES

- Based on a substitution-permutation network, not Feistel Network
- Decryption is done by applying an inverse

Refer to the slides for details.

## Using Block Ciphers Securely

NIST approved block cipher modes to use one secret key to produce different encryption outputs on the same plaintext:

- Cipher Block Chaining (CBC)
  - IV XORed
  - serial processing (slow)
  - after `2^44` AES blocks / `2^12` 3DES block, the key must be changed
- Counter (CTR)
  - like CBC, but IV++
  - encrypt again to decrypt; can process in parallel
- Cipher Feedback (CFB)
  - block cipher used as a stream cipher
  - a corrupted ciphertext segment affects the next few segments
- Output Feedback (OFB)

## Attacks

- **Ciphertext-only**
  - once this is possible then the cipher is insecure
- **Known-plaintext** / **Chosen-plaintext**
  - e.g. Meet-in-the-middle in 3DES
- **Side channel**: analysis of information leaked from the physical implementation
  - e.g. power consumption, EME, timing, sound, heat, ...
- **Quantum**: time complexity of `O^{1/2}` to classic computers
  - DES ~= `2^28`, AES-128 ~= `2^64`
