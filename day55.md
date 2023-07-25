**# Day 55**

- [Section 3: Protocols](#section-3-protocols)
  - [20. UDP](#20-udp)
    - [Use cases of UDP](#use-cases-of-udp)
    - [Multiplexing and demultiplexing](#multiplexing-and-demultiplexing)
    - [example: sending data from one app to another using UDP](#example-sending-data-from-one-app-to-another-using-udp)
    - [UDP datagram](#udp-datagram)
    - [Pros of UDP](#pros-of-udp)
    - [Cons of UDP](#cons-of-udp)

# Section 3: Protocols

## 20. UDP

User Datagram Protocol

There is not message size, starting and ending unlike in TCP but it’s just message based protocol and is like a pipe through which data will be passed.

Is a layer 4 protocol and sits on top layer 3 protocol of (Internet Protocol)

It has ability to process in a host using ports

It’s a simple protocol to send and receive data

It doesn’t require to have prior communication (which is good and also bad)

Is a stateless protocol just like IP and unlike TCP

Has very tiny header (8 byte) as compared to IP (24 byte)

### Use cases of UDP

1. Video streaming
2. VPN (most vpn use ip or ip)
3. DNS (resolves host name to ip address)
4. WebRTC (real time web communication)
5. game (to not to have the extra over heads tcp has)

### Multiplexing and demultiplexing

IP targets hosts only

Hosts run many apps each with different requirements

Ports now identify the “app” or “process”

Sender multiplexes all it’s apps into UDP

Receiver demultiplex UDP datagrams to each app

All it requires to connect apps is source IP, source port and destination IP, destination port. client doesn’t need to know server and vice versa for sending data.

### example: sending data from one app to another using UDP

explanation diagram:

![Untitled](https://github.com/pankaj485/60daysoflearning/assets/61234787/a3aae78b-5262-42e8-80ae-c46b5641abbe)

### UDP datagram

The UDP header is 8 bytes only (IPV4)

Datagram slides into an IP packets as “data”

Port are 16 bit (0 to 65535) (8-8 for each source and destination)

length is the length of the data

checksum is to verify the data packet is corrupted or not.

explanation diagram:

![Untitled](https://github.com/pankaj485/60daysoflearning/assets/61234787/b9be16fc-765a-4da0-94c8-31ea35dc71be)

### Pros of UDP

1. Is a simple protocol
2. Header size is small so datagrams are small
3. Uses less bandwidth
4. Is stateless protocol
5. Consumes lesser memory (no state stored in the server/client)
6. Low latency - no handshake, order, retransmission or guaranteed delivery

### Cons of UDP

1. No acknowledgement if the data is sent/received to and from respective parties
2. No guarantee delivery
3. connection-less (anyone can send data without prior knowledge)
4. No flow control
5. No congestion control
6. No ordered packets
7. Security - can be easily spoofed
