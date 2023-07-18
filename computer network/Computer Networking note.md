# Computer Networking

# Main content

- Computer Network and Internet
- Application Layer
- Transport Layer
- Network Layer: Data Plane
- Network Layer: Control Plane
- Data Link Layer and Local Area Network
- Network Security
- Wireless and Mobile Network
- Multimedia Network
- Network Management

# Introduction of Computer Network

## Objective

- Understand basic terminology and concepts
- Master the basic principles of the network

## Outline

1. What's the Internet? 

2. What's a protocol?

3. Network Edge

4. Access Network and Physical media

5. Network core: Packet switching, Line switching

6. Internet/ISP structure

7. Performance: Packet loss, Latency, Throughput

8. Protocol Hierarchy and Service Model

## 1. What's the Internet?

- From the perspective of specific composition。
    1. Node
        1. The host and the applications running on it
        2. Routers, switches, and other network-switching devices
    2. Communication link
        1. Access network link: The link between the host and the internet
        2. Backbone link: The link between routers
    3. Protocol
    4. Internet: Network of networks
        1. Loose hierarchy, interconnected ISPs
        2. Public Intranet vs, Private Intranet.
- From the perspective of Serve
    1. Distributed applications that communicate using communication facilities
    2. The communication infrastructure provides programming interfaces for apps (communication services)

## 2. What's a protocol?

Defines the format and sequence of messages exchanged between two or more communicating entities, and the actions to be taken on message transmission, reception or other events.

## 3. Network Edge: Distributed Applications and Infrastructure

1. End System(Host)
2. Client/Server Mode
3. Peer-Peer Mode
4. Connection-Oriented Services Using Network Facilities
    1. Target: Transfer data between end systems
    2. Shake hands: Be prepared before data transmission
    3. TCP(Transmission Control Protocol):
        1. Reliable, in-order delivery of data
        2. flow control
        3. congestion control
        4. such as HTTP, FTP, SMTP
5. Connectionless services using infrastructure
    1. Target: Transfer data between end systems
    2. Connectionless Server
    3. UDP(User Datagram Protocol)
        1. connectionless
        2. unreliable
        3. no flow and congestion control
        4. such as DNS, Streaming Media

## 4. Network core: Packet switching, Circuit switching

**Router mesh network**

![Untitled](Computer%20Networking%20note%20picture/Untitled.png)

### Packet Switching: store and forward

1. Network bandwidth resources are no longer divided into individual pieces, and all bandwidth is used for transmission
2. Data transferred between hosts is divided into packets
3. Store-and-forward: packets move one hop at a time
    1. The entire packet must reach the router before being transmitted to the next link
    2. Latency is greater than circuit switching
    3. queue time
4. Queuing Latency and Loss
    
    If the arrival rate > the output rate of the link:
    
    - Packets will be queued for transmission
    - If the router's buffer is exhausted, the packet will be discarded
5. Routing: Determines the source-to-destination path that a packet takes
6. Forwarding: diverting a packet from an input link to an output link of a router
7. The storage and forwarding of packets are transmitted from the source end to the target end one by one, according to whether there is a network layer connection
    1. datagram network
        1. The destination address of the packet determines the next hop
        2. At different stages, routing can change
    2. virtual circuit network
        1. Each packet has a label (virtual circuit identification ), and the label determines the next hop
        2. The path is determined at call setup and remains the same throughout the call

### Circuit Switching: Reserve a dedicated circuit for each call: such as the telephone network

1. Features
    1. End-to-end resources are allocated for calls from source to destination
    2. Exclusive resources: no sharing
    3. Transmission efficiency tends to be low
2. Network resources (such as bandwidth) are divided into pieces
    1. Frequency-division multiplexing
    2. Time-division multiplexing
    3. Wave-division multiplexing

### Compare

1. With the same network resources, packet switching allows more users to use the network!
2. Packet switching is suitable for bursty data transfers that do not require resume calls

## 5. Access Network, Physical media

### Access Network

1. Residential Access Network
    1. Modem
        1. Load the Internet data modulation onto the audio signal, transmit it on the telephone line, and demodulate the data at the central office; and vice versa
        2. Can't surf the web and make phone calls at the same time: can't always be online
    2. Digital Subscriber Line (DSL)
        1. Data on the DSL line is transmitted to the Internet
        2. The voice on the DSL line is passed to the telephone network
    3. Cable Network: Two-way Transformation of CATV Signal Cable
        1. FDM: Transmission of data of different channels in different frequency bands, digital TV and Internet data (uplink and downlink)
        2. HFC: hybrid fibre coax
        3. Cable and Fiber Network
    4. Home Network
2. Unit Access Network
3. Wireless Access Network

### Physical media

1. guided media
    1. Coaxial Cable
    2. Optical Fiber
    3. Twisted Pair
2. unguided media
    1. Ground Microwave
    2. LAN
    3. Wide-area
    4. Satellite

## 6. Internet/ISP structure

## 7. Performance: Packet loss, Latency, Throughput

### Latency

$$
d_{nodal} = d_{proc} + d_{trans} + d_{prop}+d_{queue}
$$

1. **Transmission Latency**
    1. R = link bandwidth(bps)
    2. L = packet length(bits)
    3. The time to send the packet to the link = L/R
    4. store-and-forward latency
2. **Propagation Latency**
    1. d = length of physical link
    2. s = speed of communication in the media
    3. propagation latency = d/s
3. **Queueing Latency**
    1. Time to wait for transmission on the output link
    2. Depends on the router congestion level
    3. traffic intensity = La/R
        1. R = link bandwidth(bps)
        2. L = packet length(bits)
        3. a = Average rate at which packets arrive at the queue
4. **Processing Latency**
    1. Check for bit-level errors
    2. Examine packet headers and decide where to direct the packet

### Packet Loss

1. A link has limited queue buffer capacity
2. When a packet arrives at a full queue, the packet will be lost
3. Lost packets may be retransmitted by a previous node or source system, or not retransmitted at all

### Throughput: Rate of transfer between source and destination (data volume/unit time)

1. Instantaneous throughput: rate at a point in time
2. average throughput: average over a long period of time

## 8. Protocol Hierarchy and Service Model

### Protocol Hierarchy

Hierarchically i**mplement complex network functions:**

1. Layer the complex functions of the network into a clear layer of functions, each layer implements one or a group of functions, and some functions can be used by its upper layer: service
2. The protocol entities of this layer interact with each other to execute the protocol actions of this layer, the purpose is to realize the functions of this layer and provide better services for the upper layer through the interface
3. When implementing the protocol of this layer, the services provided by the lower layer are directly used
4. Services of this layer: new functions brought about by the interaction between protocol entities of this layer realized with the help of lower layer services (which can be used by the upper layer) + services provided by the lower layer
5. Service
    1. The ability of lower-level entities to provide communication between them to higher-level entities
    2. primitive: The upper layer uses the service of the lower layer, the upper layer uses the service provided by the lower layer, and the lower layer provides services to the upper layer, all of which interact through service access primitives
    3. Services Access Point(SAP): The upper layer uses the services provided by the lower layer through the interface between layers
6. Service Type
    1. Connection-oriented Service
        1. A union established by two communicating entities for the purpose of communicating
        2. Features: orderly
    2. Connectionless Service
        1. Two peer-to-peer entities do not need to establish a connection before communicating, and do not reserve resources; both parties do not need to be active
        2. Characteristics: unreliable, possible duplication, possible disorder
7. Service and Protocol
    1. Relation
        1. The implementation of this layer protocol depends on the services provided by the lower layer.
        2. Entities in this layer provide higher-level services to the upper layer through protocols
    2. Different
        1. Service: The ability of low-level entities to provide communication between them to upper-level entities is operated through primitives, vertical
        2. Protocol: A set of rules that need to be followed in the process of mutual communication between peer entities, level

### Service Model

![Untitled](Computer%20Networking%20note%20picture/Untitled%201.png) ![Untitled](Computer%20Networking%20note%20picture/Untitled%202.png)

1. Application layer: Internet application; 报文(message)
2. Transport layer: Data transfer between hosts; 报文段(segment)
    1. Based on the end-to-end communication provided by the network layer, it is subdivided into process-to-process, turning unreliable communication into reliable communication
3. Network layer: Route datagrams from source to destination; 分组packet; 无连接datagram
    1. Host-to-host communication, end-to-end communication, unreliable
4. Link layer: Data transmission between adjacent network nodes; 帧(frame)
    1. Communication between 2 adjacent points, point-to-point communication, reliable or unreliable
5. Physical layer: send bits on the link; 位(bit)
6. Supplement
    1. presentation layer: Allows the app to interpret the transmitted data
    2. session layer: Synchronization of data exchange, checkpoint, recovery

![Untitled](Computer%20Networking%20note%20picture/Untitled%203.png)
