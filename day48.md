**# Day 48**

- [Section 2: Backend Communication Design Patterns](#section-2-backend-communication-design-patterns)
  - [12. Publish Subscribe (Pub/Sub)](#12-publish-subscribe-pubsub)
    - [Pros and Cons of Request/Response pattern](#pros-and-cons-of-requestresponse-pattern)
    - [How pub/sub pattern works?](#how-pubsub-pattern-works)
    - [Architecture diagram of pub/sub pattern](#architecture-diagram-of-pubsub-pattern)
    - [Pros of pub/sub model](#pros-of-pubsub-model)
    - [Cons of pub/sub model](#cons-of-pubsub-model)

# Section 2: Backend Communication Design Patterns

## 12. Publish Subscribe (Pub/Sub)

A client will publish a resource to the server and the other client will use it when required. Is a useful pattern while using micro service.

### Pros and Cons of Request/Response pattern

**Pros**

1. Is elegant and simple
2. Is scalable

**Cons**

1. Bad for multiple receivers
2. High coupling
3. Client/server has to be running all the time
4. chaining, circuit breaking

   For example: when someone uploads a video on YouTube, There could be many service which would go before an user will consume it. Some of then will be to compress service, format service, notification service, copyright service and so on. It is very tough to implement it with normal request response as one will break then all the other of them in the chain will also break down as one or more service is dependent to each other.

### How pub/sub pattern works?

Instead of chaining services to one another, the pub/sub model will allow the services to be publish and subscribe to each other.
pub sub is simply you publish to a third component (broker) and you are done. the subscriber can poll the content or the broker can push data to the subscriber)

For example: when a user will upload a video, rather than keep the chain like in request/response, there will be one service which will handle the video upload then it it will publish the data for the other services where they can utilize the data. It can be broken down like this:

1. The video will be uploaded and handled by the upload service. It will be then ready to publish it. It will be kept in message queue or some sort of always online space from where other services can use it.
2. Once the raw video is uploaded, the compress service will subscribe to the data which was published by the queue and then it will compress the video. When it’s done, it will be published again to the queue by the compress service.
3. The compressed video is then subscribed by the format service which will convert the videos into different formats and then when it’s done it will again publish it to the queue.
4. Once the formatting is published, the notification service will subscribe to the format and once the formats are ready it will send the notifications to the user.

### Architecture diagram of pub/sub pattern

![Untitled](https://github.com/pankaj485/60daysoflearning/assets/61234787/bd2f379b-c0ea-44d2-874d-51e7295e37bb)

### Pros of pub/sub model

1. Scales with multiple receivers
2. Is great for micro services
3. Has loose coupling

   reference on tight vs loose coupling: https://www.tutorialspoint.com/what-are-the-differences-between-tight-coupling-and-loose-coupling-in-java

4. Works even if client is not online as the client can consume at own pace

### Cons of pub/sub model

1. Message delivery issues (not easy to know if the message is delivered or not, how many times it was delivered)
2. Complexity (breaking the services will do add complexities)
3. Network saturation (if many clients are using the resource then can cause the network congestion)
