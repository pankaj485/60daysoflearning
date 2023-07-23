**# Day 53**

- [Section 3: Protocols](#section-3-protocols)
  - [19. Internet protocol](#19-internet-protocol)
    - [IP building blocks](#ip-building-blocks)
    - [Network vs host](#network-vs-host)
    - [subnet mask](#subnet-mask)
    - [Default Gateway](#default-gateway)
    - [IP packets](#ip-packets)

# Section 3: Protocols

## 19. Internet protocol

Any protocol eventually set the data into ip packets irrespective of the data type. The destination is the ip address and also the source is.

### IP building blocks

IP is layer 3 property in OSI model (Network)

IP can be set automatically or statically to the machine

IP address contains host and network portion

IPV4 is 28 bit

### Network vs host

The first 24 bits are network bits and rest 8 are for host

example: `192.168.254.0/24`

which means we can have `2^24` networks and each network has `2^8` hosts which is also called subnet

### subnet mask

`192.168.254.0/24` is also called a subnet

The subnet has a mask `255.155.255.0`

Subnet mask is used to determine whether an IP is in the same subnet

### Default Gateway

Most networks consists of hosts and a default gateway

Host A can talk to B directly if both are in the same subnet. Otherwise A sends it to someone who might know, the gateway

The gateway has an IP Address and each host should know it’s gateway

example:

connecting with default subnet

![Untitled](https://github.com/pankaj485/60daysoflearning/assets/61234787/964139f9-2e4c-4657-9d3a-7d6d9a42e9df)

connecting with different subnet

![Untitled](https://github.com/pankaj485/60daysoflearning/assets/61234787/e4ea5645-9d20-4bad-91a6-9112e07efbd3)

It’s recommended to not to put database in the different subnet and backend in the different subnet. It may cause route congestion and may cause latency and may cause the data loss too.

### IP packets

The IP packets has headers and data sections

IP packets header is 20 bytes (can go up to 60 bytes if options are enabled)

Data section can go up to 16 bits 65536

![Untitled](https://github.com/pankaj485/60daysoflearning/assets/61234787/85db9675-0cd3-4541-8646-44825db5d322)

If the packet contains size is than as compared to it’s capacity, the data has to be fragmented. Fragmentation is complex and also not secure method to go with.

