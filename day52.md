**# Day 52**

# Section 3: Protocols

## 17. Protocol Properties

### What to take into account when designing a protocol?

Don’t memorize the properties.

End of the day, what you need to do matters.

### What is a protocol?

Is a system that allows two parties to communicate.

Has certain set of rules depending on it’s purpose.

examples: TCP, UDP, HTTP, gRPC, FTP

### protocol properties

1. Data format

   A data format can be either text based or binary

   Text based: plain text, JSON, XML

   Binary: protobuf, RESP(redis serialization protocol), HTTP/2, HTTP/3

2. Transfer mode

   Message based: UDP, HTTP

   stream: TCP, WebRTC

3. Addressing system

   DNS name, IP, MAC

4. Directionality

   Bidirectional: TCP

   Unidirectional: HTTP

   Full/Half duplex

5. State

   Stateful: TCP, gRPC, apache thrift

   Stateless: UDP, HTTP

6. Routing

   Proxies, Gateways

7. Flow and Congestion control

   TCP: Flow and congestion

   UDP: No control

8. Error management

   Error code

   Retries and timeouts

## 18. OSI model

Open Systems Interconnection model

Is a communication standard and is used almost everywhere.

### Why do we need a communication model?

We are supposed to build agnostic applications

- Agnostic applications:
  A program, system, function or organization that works consistently regardless of any particular brand of software that it may use (a client and server should have some standard communication system to function the system properly)
  Without standard model, your application must have knowledge of the underlying network medium.
- Network Equipment Management
  Without a standard model, upgrading network equipment become difficult.
- Decoupled Innovation
  Innovations can be done in each layer separately without affecting the rest of the models.

### Layers of OSI model

Layer 7: Application - HTTP/FTP/gRPC

Layer 6: Presentation - Encoding, Serialization

Layer 5: Session - Connection establishment, TLS

Layer 4: Transport - UDP/TCP

Layer 3: Network - IP

Layer 2: Data link - Frames, Mac address Ethernet

Layer 1: Physical - Electric signals, fiber or radio waves

Application layer

Is from where data comes in. That’s where the data is coming from different protocols like HTTP, FTP, gRPC

Presentation layer

The data coming as JSON or object from through fetch or axios are serialized into a string and encoded (from other format into one like utf8) into standard form.

Session Layer

Is where TLS happens.

Where connection is established and states sets place (you store state in the client and in the server) and session is created.

Transport Layer

Is most important layer for the backend dev along with Application layer.

TCP and UDP protocols live here. Usually only these two. Everything is built on top of either of them.

Network layer

Doesn’t have transport concept

Network protocol lives here

It’s a packet that destined to an IP

In transport layer, the visibility to ports is available but not in the network layer it’s not. It only knows IP addresses.

Data link layer

Deals with physical medium and physical network addresses.

The layer doesn’t know about the IP addresses here. It only knows the MAC address protocols like Ethernet.

NOTE: We send frames in layer 2 (Data link layer), packets in layer 3 (Network layer), segments in layer 4 (Transport layer)

Physical layer

Deals with electric signals, light waves(fiber) or radio waves

Convert the signals into the frames which will be sent to the layer 2 (Data link layer)

### OSI Layer example (Senders POV)

![Untitled](https://github.com/pankaj485/60daysoflearning/assets/61234787/0083b711-8953-46e3-bdd2-62e627365897)

### OSI Layer example (Receivers POV)

![Untitled](https://github.com/pankaj485/60daysoflearning/assets/61234787/fddbc142-a5df-446d-9426-3e1a3d07aaf3)

### client sending an HTTP POST request (diagram)

Not all the layers has to be used all the time. for example, in case of authentication the flow may not go till the application layer, but instead it will stop at session layer, checks for the connection, validates and then it can be done there and flow till there will be enough.

![Untitled](https://github.com/pankaj485/60daysoflearning/assets/61234787/29b99639-b3bb-49fa-8252-e133f12a5b68)

### How client and server send and receive data?

The layers will keep track of the source and destination ports, ip, macs and sends the respective frames, packets, segments to respective layers

![ref: SPORT: source port, DPORT: destination port, SIP: source IP, DIP: destination IP, SMAC: source MAC, DMAC: destination MAC](https://github.com/pankaj485/60daysoflearning/assets/61234787/bc87df0d-6f62-4bc5-b076-602baa789eaa)

ref: SPORT: source port, DPORT: destination port, SIP: source IP, DIP: destination IP, SMAC: source MAC, DMAC: destination MAC

### When client is talking to server through switch and router

![Untitled](https://github.com/pankaj485/60daysoflearning/assets/61234787/a547f18a-fef4-4d85-bb08-1d939ecc4799)

### When client is talking to server through firewall, load balancer, and CDN

![Untitled](https://github.com/pankaj485/60daysoflearning/assets/61234787/82241fa0-bd4a-476c-a108-4ccb7851f0bc)

### Shortcomings of OSI model

1. OSI model has too many layers which can be hard to comprehend.
2. Hard to argue about which layer does what
3. Simpler to deal with layers 5-6-7 as just one layer, application which TCP/IP model does

### TCP/IP model

Is much simpler model than OSI as it has only 4 layers

Layers:

1. Application layer (layer 5, 6, 7 from OSI)
2. Transport layer (layer 4 from OSI)
3. Internet layer (layer 3 from OSI)
4. Data link layer (layer 2 from OSI)

Physical layer is not officially covered in the model.
