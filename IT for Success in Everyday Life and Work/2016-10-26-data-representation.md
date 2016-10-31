---
layout: notes
title: "Data Representation"
date: 2016-10-26
categories: notes it
---

## Vocabulary

| analogue | precisely | discrete | essence |
| :------- | :-------- | :------- | :------ |
| 模拟的    | 精确地     | 离散的    | 本质     |

**Analogue Data:** A continuous representation which precisely describes the actual information.

**Digital data:** A discrete representation which breaks the information into units and approximates the actual information.

## Data Representation

- Numbers, texts, audios, pictures, videos, ...
- Data must be represented in a way that:
    1. Captures the essence of the information
    2. is convenient for computer to process

## Data Compression

- Represent the information as accurately as possible using the fewest number of bits
- **Loseless** and **Lossy**
    - **Loseless**
        1. Decrease data size by optimizing the encoding
        2. Does not lose any of the original information
    - **Lossy**: Non-crutial information may be given up

## Representing Texts

Decompose strings into characters. **The general approach is to assign each character a binary number.**

### Charset

**Charset** is a mapping between characters and binary numbers used to represent them. It defines how to represent text in a computer.

#### ASCII

- Designed for English
- Use **8 bits** to represent a character

![ASCII8BCHAR]()

- Not enough for CJK (Chinese, Japanese, Korean)

##### NOTES:

1. Basic ASCII contains the first 128 characters
    - All binary codes start with **zero**
    - Half of the table (the whole table has 256)
2. The first 32 of ASCII are **control characters** that cannot be displayed on the screen

#### Unicode Charset

- Offers multilingual support
- Uses 16 bits to represent a character
- Designed as a superset of ASCII
    1. The first 256 characters are the same as ASCII
    2. ... which makes it convenient to convert between Unicode and ASCII.

## Representing Audio Information
