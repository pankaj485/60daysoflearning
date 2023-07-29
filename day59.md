**# Day 59**

- [Section 3: Protocols](#section-3-protocols)
  - [23. HTTP/1.1](#23-http11)
    - [Parts of a HTTP request](#parts-of-a-http-request)
    - [working of HTTP 1.0](#working-of-http-10)
    - [HTTP/1.1](#http11)
    - [Advantages of HTTP 1.1 over HTTP 1.0](#advantages-of-http-11-over-http-10)
    - [HTTP/2](#http2)
    - [HTTP over QUIC(HTTP/3)](#http-over-quichttp3)

# Section 3: Protocols

## 23. HTTP/1.1

Is simple and used widely.

works on client/server architecture

Works on PORT 80

It doesn’t include any encryption

Whatever application that makes HTTP request is client like browser, python, JavaScript or any other app

Whatever application that handles the HTTP requests is server like IIS, Apache, Tomcat, NodeJs, Python Tornado

### Parts of a HTTP request

1. Method (GET/POST)
2. PATH (address to process request)
3. Protocol (HTTP, HTTP1, HTTP/1.1)
4. Headers (collection of key value pair like content-type, cookie, authority)
5. Body (body of the request. It doesn’t have limit)

### working of HTTP 1.0

When a request is made, a connection is opened and when the response is sent, it closes the connection.

For each request the connection is closed and opened. Due to which it’s quite slower and also an expensive way.

In HTTP 1.0, there is no concept of buffering as the response can’t be broken into smaller chunks and has to be sent in a single response.

Due to limitation of the HOST header, multi-homed websites can’t be created with it. (a single ip which could host multiple domains)

### HTTP/1.1

Allows to have keep-alive connection which can be useful to handle multiple requests on a same connection without reestablishing it.

### Advantages of HTTP 1.1 over HTTP 1.0

1. Persisted TCP communication
2. Low latency and low CPU usage
3. Streaming with Chunked transfer
4. Pipelining (allows to handle multiple request at once and send the response back in a single go. But is limiting as depends on CPU and the ordering of the response also matters and is a complex process to implement. Is disabled by default.)
5. Allows to have proxying and multi-homed websites.

### HTTP/2

What HTTP/2 provides which isn’t available in HTTP/1

1. SPDY (pronounced as spidy)
2. Compression
3. Multiplexing
4. Server Push
5. Secure by default
6. Protocol negotiation during TLS (NPN/ALPN)

### HTTP over QUIC(HTTP/3)

1. Replaces TCP with QUIC (UDP with congestion control)
2. All HTTP/2 features are available
3. Doesn’t have HOL(Header of line) blocking

A really good read on HTTP1 HTTP2 and HTTP3 collectively https://medium.com/@sandeep4.verma/http-1-to-http-2-to-http-3-647e73df67a8
