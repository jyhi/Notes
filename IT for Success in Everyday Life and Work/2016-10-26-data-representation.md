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

```
ASCII: 00000000 (NUL)
       ^~~~~~~~
       Total: 2^8=256 characters can be represented
```

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

- To digital a signal we periodically measure the voltage of the sigal and record the appropriate numeric value. This is called **sampling**.
- In general, a sampling rate of ~40,000 times per second is enough to create a reasonable sound reproduction.
- **MP3**: Moving Picture Experts Group audio layer 3
    - Can store both lossy and loseless audio.

## Representing Color

**RGB Model** (Red, Green, Blue: **Primary Colors**)

```
 # RRGGBB
   ^ ^ ^-  8 bits
   | |---  8 bits
   |-----  8 bits
    Total 24 bits
```

Also in decimal. *e.g. `#D5F99F` -> (213, 249, 159)*

### Color Depth

- The number of bits that are used to represent a color
    - **True Color**: 24 bits
    - **HiColor**: 16 bits
        - 3x5 (15) bits are used to represent primary colors
        - 1 bit is used to represent transparency

### Digitalizing Images and Graphics

**Pixels**

- Smallest unit of an image
- Single color
- Image information is stored on a pixel-by-pixel basis
    - The color for each pixel is recorded

#### Resolution

- The number of pixels used to represent a picture
- **Width x Height**
- Determines how much detail an image contains

## Representing Video

- Video is a series of images displayed overtime
- Each image is called a **frame**
- Frame Per Second (**FPS**): Determines how smooth the video is
- The resolution of each frame determines how sharp the video is
- **Alomst all videos are encoded using lossy compression**
