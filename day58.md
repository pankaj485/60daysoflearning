**# Day 58**

- [Section 3: Protocols](#section-3-protocols)
  - [22. TLS (Transport Layer Security)](#22-tls-transport-layer-security)
    - [How HTTP works?](#how-http-works)
    - [How HTTPS works](#how-https-works)
    - [TLS1.2 Handshake](#tls12-handshake)
    - [DIffie Hellman Key generation algorithm](#diffie-hellman-key-generation-algorithm)
    - [TLS1.3](#tls13)

# Section 3: Protocols

## 22. TLS (Transport Layer Security)

Is an standard to encrypt data

What vanilla HTTP looks like without encryption.

HTTPS (HTTP over TLS)

How it works with TLS 1.2 Handshake

Diffie Hellman (key exchange algorithm)

TLS 1.3 Improvements

### How HTTP works?

HTTP woks on port 80

A connection is opened, a request is made, request will be made on the application layer and then a response is sent back with headers and content (could be a single segment or multiple segments) once the response is received the connection is closed.

The request sent and the response received is not encrypted and any medium in medium like router or ISP can read the data.

Diagram

![Untitled](https://github.com/pankaj485/60daysoflearning/assets/61234787/a151bc76-0bc3-46d8-a90f-19169ab5fb54)

### How HTTPS works

HTTPS works on port 443

Unlike in HTTP, before sending a request a handshake is done between client and server and shares the symmetric encryption key which will be used to encrypt the requests and response. No other medium in the middle should have the key except for the sender and receiver.

Once the handshake is done, then the request and response is made just like in HTTP. But in this case, the data is encrypted and will be decrypted with the encryption key only.

Diagram

![Untitled](https://github.com/pankaj485/60daysoflearning/assets/61234787/3cbe5fb1-bec9-4ba1-9061-717d5a304da7)

The encryption is done with symmetric key algorithms.

The keys has to be exchanged between client and server.

Key exchange uses asymmetric key (PKI)

Symmetric key is used because it’s way faster than asymmetric key.

### TLS1.2 Handshake

Uses RSA key exchange algorithm

Utilizes RSA public key and RSA private key\

Since documenting is not so easy, here is the resource to it https://cheapsslsecurity.com/blog/what-is-tls-1-2-a-look-at-the-secure-protocol/

RSA algorithm is less used due to known secure vulnerability which causes leakage of the private key.

Diagram

![Untitled](https://github.com/pankaj485/60daysoflearning/assets/61234787/64c9f05a-8f7a-4d76-a78a-8855f0bcb588)

### DIffie Hellman Key generation algorithm

It can be slow for the larger database

Unlike in RSA, it requires to have 2 private key to generate symmetric keys and one public key.

If any one of the private key is used with the public key, it can be shared as it’s not breakable and is a way to generate symmetric key.

### TLS1.3

Utilizes the Diffie Hellman key generation algorithm by default unlike with TLS1.2 (although it can also use if configured but by default uses RSA key generation algorithm)

Since it’s also a complex process, documenting is not easy so here is a nice resource to follow on about TLS1.3 and it’s working https://www.telerik.com/blogs/tls-1-3-what-is-it-why-use-it
