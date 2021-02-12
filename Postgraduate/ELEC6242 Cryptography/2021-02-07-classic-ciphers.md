# Classic Ciphers

Terminologies:

- **Plaintext**: message in a "clear" form
- **Steganography**: message whose **existence is concealed (hidden)**
- **Cryptography**: messge in plain view, but the **meaning is concealed (hidden)**.
- **Cipher**: the operation on groups of **characters**

## Compression & Encryption

Compression and encryption are both about manipulating information (not data or wisdom).

- _Compression_ extracts information from the data to encode it as efficiently as possible.
- _Encryption_ diffuse a **key** into information as much as possible, and encode it.

## The Best Approach

The best way to practically transmit secure data safely is to:

1. Compress the data
  - this **removes redundancy** in the plaintext
  - this also makes encryption (which is slow) **faster**
2. Encrypt
3. Add error detection and recovery

## Basic Cryptanalysis

- Frequency analysis
- "Crib": a known sequence of letters or words, e.g. _q is almost always followed by u_
- Make guesses
