# Data Link Layer: Flow Control

Prevents a sender out-pacing a slow receiver by giving feedback on data it can accept from the receiver to the sender.

- A topic in link layer and transport layer.

## Example Protocols

- Commonly implemented in NICs and as OS drivers
  - network layer (e.g. IP) is often OS software

### Utopia

An optimistic, **unacknowledged, connectionless** protocol, without error control or flow control, as a starting point. Assumes:

- no error can happen; data is always available
- receiver is as fast as sender

Sender loops blasting frames. Receiver loops eating frames.

### Stop-and-Wait (Error Free)

Assumes:

- no error can happen; data is always available
- ~~receiver is as fast as sender~~
  - only one frame is out at any time
  - **flow control** is added

Sender waits for ACK after passing frame to the physical layer. Receiver sends ACK after passing frame to the network layer.

### Stop-and-Wait (Noisy Channel)

On a noisy channel, 3 things can happen:

1. All good.
2. The frame is successfully received by the receiver, but ACK is corrupted or lost.
    - the system hangs
3. The frame is corrupted or lost, and hence not received by the receiver; ACK is never transmitted.
    - the system hangs

To resolve these, we use ARQ (Automaic Repeast reQuest):

- The sender starts a timer whenever it transmits a frame
- If ACK is not received when the timer expires, the frame is retransmitted
- Plus, add **sequence numbers** to tell which frame is retransmitting

### Sliding Window

- Sender maintains window of frames that it can send
  - needs buffering (for retransmissions)
  - **window advances upon next ACK**
- Receiver maintains window of frames that it can receive
  - needs buffering (for arrivals)
  - **window advances upon in-order arrivals**

An appropriate size of sliding window can be obtained by:

```
w = 2 (bw * t / f) + 1

w:  (b)
bw: (bps) Bandwidth
t:  (s)   One-way transmit time
f:  (b)   Frame size
```

To control the retransmission, **Go-Back-N** and **Selective Repeat** are used.

#### Go-Back-N

- Sender buffers all frames in case of going back
- Receiver doesn't buffer frames; it simply expects and throws NAK
- **Good if errors are rare**
  - wastes a lot of bandwidth for retransmission

#### Selective Repeat

- More complex than _Go-Back-N_ due to **receiver buffers** and **multiple sender timers**
- More efficient use of bandwidth, since only lost frames are resent
- **Good if errors are common**
  - but requires a lot more memory
