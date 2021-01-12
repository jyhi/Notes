# Network Layer

Responsible for delivering packets between **endpoints over multiple links**.

- Deals with end-to-end transmission
- Needs to know the network topology
  - to choose appropriate paths
    - to avoids congested links / routers

## Connection-Oriented vs. Connectionless

### Philosophies

- Connection-oriented
  - similar to traditional phone networks
  - QoS
- Connectionless
  - routers only move packets
  - networks are inherently unreliable
  - **hosts should look after error and flow control themselves**

There is still no agreement on which one should be used: services have different requirements.

- IP is connectionless

## Routing vs. Forwarding

- **Routing** is the process of discovering network _paths_
  - decide what to optimize: correctness, simplicity, robustness, stability, fairness, efficiency, etc
- **Forwarding** is the process of sending packets along _a path_

## Flooding

- A simple method to send a packet to all network nodes
- Nodes need to keep track of flooded packets to stop the flood
  - even using a hop limit can make the number of packets blow up exponentially

## Distance Vector Routing

- **Distance Vector** is a distributed routing algorithm
  - shortest path computation is split across nodes
- Algorithm:
  - Each node knows the distance of liks to its neighbors
  - Each node advertises vector of lowest known distances to all neighbors
  - Each node uses received vectors to update its own
  - Repeat periodically

**Count-to-Infinity** problem occurs while seeking a path to an unreachable node.

## Link State Routing

- **Link State** is an alternative to distance vector
  - more computation, but simpler dynamics
  - widely used on the Internet (OSPF, IS-IS)
- Algorithm:
  - Each node **floods** information about its neighbors in Link State Packets (LSPs)
  - All nodes learn the **full** network graph
  - Each node runs Dijkstra's algorithm to compute the path to take for each destination
- The 5 Steps:
  - Discover neighbors and learn network addresses
  - Set distance (or cost metric) to each of its neighbours
  - Construct a packet telling all that it has just learned it (^)
  - Send the packet (^) and receive such packets from all other routers
  - Compute shortest path to every other router

## Congestion Control

Approaches, from **slower, prevensive** to **faster, reactive**:

- Network provisioning
- Traffic-aware routing
  - choose routes depending on traffic, not just topology
- Admission control
  - allow a new traffic load only if the network has sufficient capacity
- Traffic throttling
  - signal hosts (with "chokes") to slow down traffic
- Load shredding
  - drop packets
  - _"Wine" policy_: older is better (discard new packets)
    - better for file transfer
  - _"Milk" policy_: newer is better (discard old packets)
    - better for media streaming
  - _QoS_ is used to control this

## Traffic Shaping

Refer to the slides.

## Packet Scheduling

Refer to the slides.

## Admission Control

Refer to the slides.

## Differentiated Services

Refer to the slides.

..

## Network Layer in the Internet

- Tier 1, Tier 2, Tier 3

### IPv4

Refer to the slides.

- **Prefixes**: IPv4 addresses are allocated in blocks, called prefixes
- **Aggregation**: joins multiple IP prefixes into a larger one to reduce routing table size
- **Longest Matching Prefix**: packts are forwarded to the entry with the higher slash number (/xx) (smaller address block)
- **NAT**: maps one external IP address to many internal IP addresses

### IPv6

Refer to the slides.

### Internet Control Protocols

- **ICMP**: a companion to IP that returns error info
- **ARP**: finds Ethernet address for a local IP address
- **DHCP**: assigns a local IP to a host
