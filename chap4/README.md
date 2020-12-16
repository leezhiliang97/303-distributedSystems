# Chapter 4 - Interprocess Communication

## Java UDP Client/Server

### Pre-requisites

1. Eclipse Java

2. Git

### Compiling

```
$ javac UDPServer.java
$ javac UDPClient.java
```

### Running

```
$ java UDPServer
$ java UDPClient
```

### How the application (client/server) works?

This application contains two main componenets, a client program and a server program. 

The image below show the architecture of client/server UDP Java program.

![The architecture of client server UDP Java program](https://pasteboard.co/JF8eefX.png)

How do UDP sockets work?
The UDP socket communication between a server and a client consists of several phases as follows.

![](https://miro.medium.com/max/597/1*0TPqib9R9MFekbMXWGnZ2g.png)

1. socket() - Firstly a socket is defined in both server and client. This need not happen at the same time. For the explanation to be comprehensive, I will be discussing the actions of both server and client in each stage.
2. bind() - Defined socket is assigned an id and a port in the running machine. This is optional for the client socket. This is because even if the client socket is not bound, it will automatically happen whenever the client initiates connecting to the server.
3. recvfrom() - After binding to a port in the machine, the server socket waits for a connection from a client socket. In the meantime, further execution of the current thread is halt (blocked) until the server socket receives a connection. This is the same for the client socket when waiting for a server response.
4. sendto() - After connecting with a client, the server socket sends data to the client. This same method is used by the client socket to make a connection request to the server.
5. close() - After successful data exchange, both sockets are closed i.e. system resources allocated for the sockets are released.
