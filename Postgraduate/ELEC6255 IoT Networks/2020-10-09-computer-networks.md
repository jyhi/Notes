# Computer Networks and Networking Protocols

## Definitions

- **Service**: functionality a layer provides
- **Interface**: operations and **services** the lower layer makes to the upper one
- **Protocols**: agrement between communicating parties
- **Protocol stack**: a list of **protocols** used by a certain system
- **Network architecture**: a set of **protocol stacks**
- **Computer Network**: a collection of autonomous computers interconnected by a single technology
- **Internetwork**: multiple networks joined together

## Protocol Layering

The main structuring method used to divide up network functionality.

- Each protocol instance talks virtually to its peer
- Each layer communicates only by using the one below
- Lower layer services are accessed by an interface
- At bottom, messages are carried by the medium

```
     ^ Layer k+1                        ^ Layer k+1
     |                                  |
+---------+                        +---------+
| Layer k | <----- Protocol -----> | Layer k |
+---------+                        +---------+
     |                                  |
     v Layer k-1                        v Layer k-1
```

Each layer:

- adds its own header to the message to transmit and removes it on receive
- may also split and join messages

```
              +-----------+
              |     M     | Layer k+1
              +-----------+
                    |
                    v
         +----+-----------+
         | Hk |     M     | Layer k
         +----+-----------+
                    |
                    v
+--------+----+-----------+
| H(k-1) | Hk |     M     | Layer k-1
+--------+----+-----------+
```

### Why? (Design Issues)

- Reliability (error detection and correction)
- Routing
- Addressing (naming destinations)
- Internetworking
- Scalability
- Congestion and flow control
- Throughput, latency and QoS management
- Confidentiality and authentication

## Service Primitives

- `LISTEN`: block waiting for an incoming _connection_
- `CONNECT`: establish a connection with a waiting peer
- `ACCEPT`: accept an incoming connection from a peer
- `RECEIVE`: block waiting for an incoming _message_
- `SEND`: send a message to the peer
- `DISCONNECT`: terminate a connection

## Connection-Oriented vs. Connectionless Servicess

- Connection-oriented service
  - a connection is negotiated and setup, and released when finished
  - provides a communication _"tube"_, and manages flow through it
  - may provide reliable or unreliable services
- Connectionless service
  - messages are sent without establishing a connection
  - messages may be received out-of-order
  - may provide reliable or unreliable services

## OSI Reference Model

- **Application**: provides functions needed by users
- **Presentation**: converts different representations
- **Session**: manage task dialogs
- **Transport**: provides end-to-end delivery
- **Network**: send packets over multiple links
- **Data link**: sends frames of information
- **Physical**: sends bits as signals

## Tanenbaum Model

- **Application**: programs
- **Transport**: provides increased reliability
- **Network**: how to combine links / networks into networks / internetworks
- **Link**: how to send messages between directly connected computers
- **Physical**: how to transmit bits
