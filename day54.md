**# Day 54**

- [Section 3: Protocols](#section-3-protocols)
  - [summary](#summary)
  - [ICMP](#icmp)
  - [How PING works:](#how-ping-works)
  - [Trace Route](#trace-route)

# Section 3: Protocols

### summary

The IP packets has headers and data sections

IP packet header is 20 bytes (can go up to 60 byte if options are enabled but is very very rare)

Data section can go up to 65536

Packets need to get fragmented if it doesn’t fit in a frame

### ICMP

Stands for Internet Control Message Protocol

Lives in layer 3 of the OSI layer (Network) which means it only has source and destination IP addresses and there is no concept of port in the layer

Is designed for informational messages

1. Host unreachable, port unreachable, fragmentation needed
2. Packet expired (infinite loop in routers)

It uses IP directly

`PING` and `traceroute` use it

Doesn’t require listeners or ports to be opened.

Some firewalls block ICMP for security reasons due to which `PING` may not work in those cases

Disabling ICMP also can cause real damage with connection establishment. Also called TCP balckhole. (when sending very small data, it works well but when sending real life data, it fails due to lack of processing ability)

example: Fragmentation needed

### How PING works:

source IP sends ICMP echo request to the destination IP.

If the destination is reachable then it will return the ICMP echo request.

If the destination is not reachable then the router responds with ICMP destination unreachable message.

when destination IP is reachable

![Untitled](https://github.com/pankaj485/60daysoflearning/assets/61234787/1f8d9465-0b8c-455c-b0a0-6c74247f543e)

when destination IP is not reachable

![Untitled](https://github.com/pankaj485/60daysoflearning/assets/61234787/1259b7ed-91bb-43d9-bcf3-8b90a3b6a23c)

### Trace Route

Answers the question of “can you identify the entire path your IP packet takes?”

Is a clever use of TTL (Time to live (TTL) refers to the amount of time or “hops” that a packet is set to exist inside a network before being discarded by a router)

If we increment the TTL slowly the we can get the router IP address from the each hop

It doesn’t work as path changes and ICMP might be blocked so can’t be accurate all the times.

example:

```bash
➜  ~ traceroute google.com
# output is not used due to security reasons.
```
