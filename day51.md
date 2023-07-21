**# Day 51**

- [Section 2: Backend Communication Design Patterns](#section-2-backend-communication-design-patterns)
  - [15. Sidecar pattern](#15-sidecar-pattern)
    - [Changing the library is hard](#changing-the-library-is-hard)
    - [when we delegate communication?](#when-we-delegate-communication)
    - [Sidecar design pattern](#sidecar-design-pattern)
    - [Sidecar examples](#sidecar-examples)
    - [pros of sidecar proxy](#pros-of-sidecar-proxy)
    - [cons of sidecar proxy](#cons-of-sidecar-proxy)

# Section 2: Backend Communication Design Patterns

## 15. Sidecar pattern

When the clients are complex so does the backend becomes.

Every protocol requires a library to be imported which lives within the app. (like HTTP)

![Untitled](https://github.com/pankaj485/60daysoflearning/assets/61234787/e9a6f878-b255-4178-a137-cfa37ecd4311)

![Untitled](https://github.com/pankaj485/60daysoflearning/assets/61234787/17300f40-9a89-43c9-b218-101bf7ede1bd)

### Changing the library is hard

Once you use the library, your app is entrenched.

Both app and library should be same language. (if you are using socket with NodeJS, you need NodeJS socket library)

Changing the library require re testing.

Changing the library also requires to be backward compatible.

Adding feature is hard part on library.

Micro services suffers more

### when we delegate communication?

Proxy communicate instead of direct communication.

Proxy allows to have the rich library which means it can talk to whatever library it can

client has thin library (e.g h1)

Each client must have a sidecar proxy.

### Sidecar design pattern

Since the pattern includes the sidecar proxy, now the request coming and going will be happening through it only.

server will response back to the proxy and the proxy will write back to the same connection requesting for the resource.

![Untitled](https://github.com/pankaj485/60daysoflearning/assets/61234787/cddef459-7fe2-4a64-b116-430c605158c8)

Let’s say one has to upgrade to HTTP/3 instead of HTTP/2 then there will be no need to change the both client and serve code, just the proxies have to be upgraded to handle them. Will introduce the extra hop

![Untitled](https://github.com/pankaj485/60daysoflearning/assets/61234787/d2e356ea-827e-4558-aafc-3d6cb2ff734a)

### Sidecar examples

1. Service mesh proxies

   linkerd, lstio, envoy

2. Sidecar proxy container
3. Must be layer 7 proxy

### pros of sidecar proxy

1. Is language agnostic (polyglot)
2. All networking logic an be done on sidecar proxy
3. Protocol upgrade is available
4. Security
5. Tracing and Monitoring is possible as the use of proxy
6. Service Discovery
7. Caching

### cons of sidecar proxy

1. Complexity (is complex system and is not easy to debug)
2. Latency (the proxies adds up extra layer of hops which increases latency)
