# Data Link Layer: MAC Sublayer: Sharing Channels

_Media Access Control_

## Channel Allocation

- Static channel allocation
  - fine if traffic is predictable and constant
  - _e.g. FDMA, TDMA_
- Dynamic channel allocation

## ALOHA

In _pure ALOHA_, users transmit frames whenever they have data, and retry after a random time for collisions.

- High load causes collision
- Efficiency up to **18%**

In _slotted ALOHA_, time is synchronized across users, and each user can only send data on it's own multiple of `t` slot (where `t` is the slot width).

- Low load wastes slots
- High load causes collision
- Efficiency up to **37%** (`1 / e`)

## MAC Protocols

### CSMA

CSMA improves on ALOHA by sensing the channel:

- 1-persistent (greedy)
  - if idle, transmit
  - if busy, continue monitoring, instantly sends when idle
    - bad: multiple nodes might have the same idea, and thus collision
  - if collide, wait for a random time before trying again
- non-persistent
  - if idle, transmit
  - if busy, **wait for a random time before trying again**
  - if collide, wait for a random time before trying again
- p-persistent (where `p` is probability)
  - if idle, transmit **with a probability `p` of transmission**
    - therefore a probability of `1 - p` for waiting for the next slot
  - if busy, **wait for the next slot**
  - if collide, wait for a random time before trying again

### CSMA/CD

CSMA with Collision Detection

- Can detect / abort collisions

### Collision-Free Protocols

#### Bitmap

Avoids collision entirely.

- Senders must know when it's their turn to send
- The basic bitmap protocol:
  - starts with a contention period containing `N` slots
  - sender `n` sets the bit in contention slot `n` if it wants to speak
  - after the contention period, senders send their frames in turn

#### Token Ring

A station with token may send a frame before passing it to the next station.

- The "ring" defines the sending order, not the physical topology
  - the same idea can be used without rings too, e.g. _token bus_

#### Countdown

Binary countdown improves the 1-bit overhead on the above methods.

- Stations send their addresses in contention slot simutaneously
  - in this way the channel OR bits (1 when any station sent 1)
  - ... which **gives higher priority to higher numbered stations**
- Stations seeing their full address transmits its frame

### Limited-Contention Protocols

#### Adaptive Tree Walk

The tree divides stations into groups (nodes) to **poll**.

?
