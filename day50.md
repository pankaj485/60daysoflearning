**# Day 50**

- [Section 2: Backend Communication Design Patterns](#section-2-backend-communication-design-patterns)
  - [14. Stateful vs Stateless](#14-stateful-vs-stateless)
    - [Stateful backend](#stateful-backend)
    - [Stateless backend](#stateless-backend)
    - [stateful backend diagram](#stateful-backend-diagram)
    - [stateless backend diagram](#stateless-backend-diagram)
    - [stateless vs stateful protocols](#stateless-vs-stateful-protocols)
    - [complete stateless system](#complete-stateless-system)

# Section 2: Backend Communication Design Patterns

## 14. Stateful vs Stateless

Is the way to store the state within the application and relying on that state. Can be implied to system, backend, functions, protocols

### Stateful backend

Stores state about clients within itself (not on database).

To function properly, it requires to have the state information.

The client will not have the information about the state.

### Stateless backend

Client is responsible to transfer the state with every request.

It can still store data somewhere else.

If a backend system can restart the backend during the idle time while the client workflow continues to work then the backend can be considered as stateless backend.

The backend remain stateless but the system is stateful.

### stateful backend diagram

**when stateful backend works:**

When user request for certain resource which might require the authentication process, it will verify it with the database first and then generate a session and store it locally on backend and also passes it in the response. Next time when it gets the same request again, it checks for the session is there in the memory or not, if it’s there then it will handle the response there right away and doesn’t go to other states.

![Untitled](https://github.com/pankaj485/60daysoflearning/assets/61234787/d910eb5b-b205-468c-8bbf-e064d8e7d6e4)

**when stateful backend fails:**

Since it doesn’t rely on the data base to verify the authentication, if it doesn’t found the status of the session then it effectively will fail.

It can be occurred in the case of load balancer quite a lot as there is no straight idea about which server exactly it will it and if the server request is hitting is not having the session data then user might have to authenticate multiple times.

![Untitled](https://github.com/pankaj485/60daysoflearning/assets/61234787/fa745f41-bb70-4cfd-9304-1a9b4f67b439)

### stateless backend diagram

The backend app is always stateless but the entire system will still be stateful. If the database dies then everything will be gone.

The session is stored permanently on some database and each time the resource access is asked for, it will look into the database and each time time it will verify weather the session information is stored or not and then proceeds further based on that.

![Untitled](https://github.com/pankaj485/60daysoflearning/assets/61234787/4515161b-5bcf-4080-8576-60fd74cbacd1)

### stateless vs stateful protocols

The protocols can be designed to store or not to store any sort of state.

TCP is stateful protocol as it maintains the flow control, connection,

UDP is stateless as it doesn’t store anything and is connection less.

DNS sends queryID in UDP to identify queries.

QUIC sends connectionID to identify connection.

You can build a stateless protocol on top of a stateful one and vice versa.

HTTP is stateless protocol but it’s built on top of TCP which is stateful. If TCP breaks, HTTP blindly create another one. TCP is just a medium to transfer information.

QUIC is stateful protocol it’s built on top of UDP which is stateless.

### complete stateless system

Stateless systems are very rare firstly.

The stateless systems require the backend service that relies completely on the input and doesn’t require to communicate with another system(client side information).

In complete stateless system, state is carried with every request.

JWT(JSON Web Token) is completely stateless as it has everything within itself. It can cause security concerns as well.

Not everything is figured out in the backend. People will only talk about it when flaws happen. Trying to be better backend engineer is knowing what’s the limit and work around it.
