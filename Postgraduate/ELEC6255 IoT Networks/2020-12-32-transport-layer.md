<!-- This class is actually taken on 14-15 Jan 2021. -->
# Transport Layer

The Transport Layer is responsible for **delivering data across networks with the desired reliability or quality**.

## Sockets

"A socket is one endpoint of a two-way communication link between two programs running on the network. A socket is bound to a port number so that the Transport Layer can identify the application that data is destined to be sent to. An endpoint is a combination of an IP address and a port number."

- Also known as "virtual ports"

## Addressing

- Transport layer adds **Transport Service Access Points (TSAPs)**.
  - i.e. **ports** in TCP / UDP

## Connection Establishment

Ensuring reliability even though packets may be lost, corrupted, delayed, or duplicated.

- Do not treat an old or duplicate packet as a new one
- Use ARQ (Automatic Repeat reQuest) and checksums for loss / corruption detection
  - do not reuse sequence numbers within twice the MSL (Maximum Segment Lifetime) of 2mins = 240s
    - use a sequence number space _large enough_ so that it won't wrap even when sending at full rate
  - three-way handshake for connection establishment
    - each host contributes to the sequence number
    - prevents duplicate CR, DATA, and spruious ACK

Forbidden region: refer to the slides.

## Connection Release

Ensuring reliability: **asymmetric release is abrupt and may lose data**.

## Error Control and Flow Control

- Error control: A sliding window (from Link Layer) with checksums and retransmissions
- Flow control: Managing buffer at sender / receiver
  - used **when the _receiver_ is not fast enough**
  - buffer strategies: refer to the slides

## Multiplexing

Connections sharing a network address.

- Inverse multiplexing: addresses share a connection.

## Crash Recovery

Application needs to help recovering from a C(rash) (between A(CK) and W(rite)).

| Sender \ Receiver | AC(W) | AWC | C(AW) | C(WA) | WAC | WC(A) |
|-|-|-|-|-|-|-|
| Always Retransmit | OK | DUP | OK | OK | DUP | DUP |
| Never retransmit | LOST | OK | LOST | LOST | OK | OK |
| Retransmit in S0 | OK | DUP | LOST | LOST | DUP | OK |
| Retransmit in S1 | LOST | OK | OK | OK | OK | DUP |

## Congestion Control

Used **when the _network_ is not fast enough**.

Two layers are responsible for congestion control:

- Transport layer _controls_ the offered load
- Network layer _experiences_ congestion

## Desirable Bandwidth Allocation

- **Efficient use** of bandwidth gives high goodput, low delay
  - refer to the slides
- **Fair use** gives bandwidth to all flows (no starvation)
  - max-min fairness gives equal shares of _bottleneck_
- We want bandwidth levels to converge quickly when traffic patterns change

## Regulating the Sending Rate

For flow control and congestion control. Refer to the slides for protocols.

- To achieve the balance between fairness (up / down utilisation) and efficiency (full use of bandwidth)
  - the **AIMD (Additive Increase Multiplicative Decrease)** control law converges!

### Wireless Issues

- Wireless links lose packets due to transmission errors
  - not to be confused with congestion
- Strategy: **ARQ (Automatic Repeat Request)**, which **masks errors**

## UDP

_A **shim** over IP (with TSAP (port), length, and checksum)._

### UDP Pseudoheader in IP

- **This is not actually sent over the network!**
- The _checksum_ covers UDP segment and IP pseudoheader
  - provides E2E delivery check

## TCP

Refer to the slides.

### TCP Sliding Window

- ACK + WIN is (both) the sender's (and the receiver's) limit
- Special cases are added to avoid unwanted behavior
  - e.g. silly window syndrome: "1-byte"-s are sent around the network

### TCP Timer Management

- TCP estimates retransmit timer from segment RTTs
  - tracks both average and variance
  - timeout is set to **average + 4 \* variance**

### TCP Congestion Control

- TCP uses AIMD with loss signal to control congestion
  - implemented as a **congestion window (cwnd)** for **the number of segments that may be in the network**
  - uses several mechanisms that work together
    - ACK clock, slow-start, additive increase, fast retransmit / recovery

## RTP

Real-time Transport Protocol: suport for sending real-time media **over UDP**; often implemented as a part of the application.
