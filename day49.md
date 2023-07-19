**# Day 49**

- [Section 2: Backend Communication Design Patterns](#section-2-backend-communication-design-patterns)
  - [13. Multiplexing vs Demultiplexing (h2 proxying vs Connection Pooling)](#13-multiplexing-vs-demultiplexing-h2-proxying-vs-connection-pooling)
    - [HTTP/2 Multiplexing diagram](#http2-multiplexing-diagram)
    - [HTTP/2 DeMultiplexing diagram](#http2-demultiplexing-diagram)
    - [Connection Pooling](#connection-pooling)
    - [Browser demultiplexing in HTTP/1.1 diagram](#browser-demultiplexing-in-http11-diagram)
    - [Demo of the HTTP/1.1 limit](#demo-of-the-http11-limit)

# Section 2: Backend Communication Design Patterns

## 13. Multiplexing vs Demultiplexing (h2 proxying vs Connection Pooling)

Is a networking concept

Multiplexing is when multiple inputs/requests are converted into a single output/response.

Demultiplexing is when a single inputs/request is converted into multiple output/response

### HTTP/2 Multiplexing diagram

Multiplexing can cause more resource as the server has to parse and handle the multiple request at a single instance (high throughput and backend resources)

![Untitled](https://github.com/pankaj485/60daysoflearning/assets/61234787/0be68936-83be-4bac-a99f-1d2fd46e543e)

### HTTP/2 DeMultiplexing diagram

Demultiplexing will has comparatively lesser throughput and also will case less backend resources

![Untitled](https://github.com/pankaj485/60daysoflearning/assets/61234787/2315ce43-8409-46f2-8990-d674835d0b11)

### Connection Pooling

Is a technique where you can spin up multiple database connection (create pool of connection on request)

Is just another demultiplexing style

If one request is done before another then it will respond back and doesn’t wait for the other request to complete. The order of response is not determined.

### Browser demultiplexing in HTTP/1.1 diagram

Chrome allows upto 6 connections per domain, users requests are demultiplexed in 6 connections.

![Untitled](https://github.com/pankaj485/60daysoflearning/assets/61234787/d5202dc8-13f6-4851-8cae-a538915aa858)

### Demo of the HTTP/1.1 limit

If multiple requests are sent then the connection pool will be filled and one no longer can make the requests until some of it is done. In that case, the browser doesn’t establish a connection it’s absolutely needed.

The protocol `1.1` means it’s HTTP/1.1

![Untitled](https://github.com/pankaj485/60daysoflearning/assets/61234787/c3c04f6a-7b28-4861-a2b4-b44ea3c117e9)
