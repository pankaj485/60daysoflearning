**# Day 57**

# Section 3: Protocols

## 21. TCP

Stands for Transmission Control Protocol.

Is a common choice of protocol to communicate between client and server. Most of the applications are built on top of it.

Is built with congestion control, flow control, order guarantee. All one has to do is send a request and the message will arrive.

Most of the time the kernel has the implementation of the TCP

Is a layer 4 protocol

Has ability to address processes in a host using ports.

It controls the transmission unlike in UDP which is a firehose

Requires to create connection between client and server to function.

Since it requires to establish the connection, it has to perform handshake and it’s stateful as it has to store the session information in order to perform handshake

Has 20 bytes headers segment (can go up to 60)

### Use cases of TCP

1. Reliable connection (as it requires handshake and creates connection between client and server)
2. Remote shell
3. Database connections
4. Web communications (All web communications uses HTTP which is built on top of TCP)
5. Any bidirectional communications

### TCP connection

Is a layer 5 (session)

Connection is an agreement between client and server

Must create a connection to send data

Connection is identified by 4 properties:

1. SourceIP-SourcePort
2. DestinationIP-DestinationPort

Can’t send data outside of a connection

Sometimes called socket or file descriptor

Requires a 3-way TCP handshake

Segments are sequenced and ordered

Segments are acknowledged

Lost segments are re transmitted which makes TCP a reliable protocol

### Connection Establishment (diagram)

SYN: Sequence number

ACK: acknowledgement

![Untitled](https://github.com/pankaj485/60daysoflearning/assets/61234787/bc77952f-6ade-42b5-8cf9-2f821a348cf9)

### Sending data (diagram)

App1 can send new segment before acknowledgement of old segment arrives.

ACK: acknowledgement

![Untitled](https://github.com/pankaj485/60daysoflearning/assets/61234787/29780555-dba0-4e8f-81db-425988255f08)

### Acknowledgement (diagram)

ACK: acknowledgement

![Untitled](https://github.com/pankaj485/60daysoflearning/assets/61234787/87a5b5ea-ad35-42d7-a8c4-38d78ef7fd75)

### Lost data (diagram)

If multiple packets are received on same time then later one will be acknowledged. If a data which is not acknowledged then it will be sent again (retransmission)

ACK: acknowledgement

![Untitled](https://github.com/pankaj485/60daysoflearning/assets/61234787/21f2a735-607b-4604-951e-8a48fe4b4553)

### Closing connection (diagram)

ACK: acknowledgement

![Untitled](https://github.com/pankaj485/60daysoflearning/assets/61234787/8587fa1a-00a7-4420-a1d6-649f7b88bad2)

### Summary (TCP)

Stands for Transmission Control Protocol

Is layer 4 protocol

Controls the transmission unlike UDP which is a firehose

Introduces connection concept

Retransmission, acknowledgement, guaranteed delivery, congestion control

Stateful, connection has a state

Lives in memory

### TCP Segment

TCP segment header is 20 bytes and can go up to 60 bytes

TCP segments slides into an IP packet as “data”

Port are 16 bit (0 to 65535)

Sequences, Acknowledgement, flow control and more control

![Untitled](https://github.com/pankaj485/60daysoflearning/assets/61234787/cc94350f-71a9-446d-b6ab-0e253fd0dac2)

### Maximum Segment Size

Is maximum amount of data which can be sent in a time to handle everything smoothly.

Segment size depends the MTU (maximum time unit) of the network

Usually 512 bytes can go up to 1460 bytes

Default MTU in the internet is 1500 (results in MSS (Maximum Segment Size) 1460) can go more if the frames support them.

Jumbo frames MTU goes to 9000 or more

MSS can be larger in jumboo frames
