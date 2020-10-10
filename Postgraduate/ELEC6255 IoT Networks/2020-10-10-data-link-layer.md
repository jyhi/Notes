# Data Link Layer

## Purpose

To provide reliable, efficient communication of **whole units** of information between two **adjacent** machines.

- **whole units**: _frames_
- **adjacent**: _wire(-like)_

## Two Sublayers, and Their Functions

- The **Logical Link Control** sublayer
  - **Framing**
  - **Error control**: dealing with transmission error
  - **Flow control**: regulating flow of data
- The **Media Access Control** sublayer

## Service Provision

- Unackowledged connectionless, e.g. Ethernet
  - frames are sent without acknowledgement
  - no logical connection is established
  - no error detection / correction
- Acknowledged connectionless, e.g. 802.11
  - frames are sent with ackowledgement
  - no logical connection is established
  - suitable for unreliable channels
  - **never essential; could be done at higher layers**
- Acknowledged connection-oriented
  - guaranteed receipt in the correct order
  - suitable for long reliable links

## Frames

```
         +--------+                          +--------+
         | Packet |                          | Packet |             Network Layer
         +--------+                          +--------+
Frame         |                     Frame         |
+--------+---------+---------+      +--------+---------+---------+
| Header | Payload | Trailer |      | Header | Payload | Trailer |  Link Layer
+--------+---------+---------+      +--------+---------+---------+
              |                                   |
              +===================================+                 Physical Layer
               Actual data path
```

## Framing

- **Byte count**: frame begins with a count of the number of bytes in it.
- **Byte stuffing**: use special flag bytes to delimit frames
  - used in PPP
  - _the flag itself usually counts into the length of frame too_
- **Bit stuffing**: **byte stuffing** at the bit level
  - data needs to be stuffed to ensure the flag pattern never occurs in the data
  - size of frames depends on the data length
  - ensures minimum number of transitions which allows **synchronization**
    - USB uses bit stuffing only for this
