TCP sockets are created using the socket object `socket.socket()` specifying the socket type as `socket.SOCK_STREAM` 

When used socket.SOCK_STREAM, the default protocol is TCP. This is a good default.

## TCP Socket Flow


![[Pasted image 20251011123539.png]]


Server
socket - bind - listen - accept

Client 
socket - connect - send - recv - close


Server makes a "Listening" socket
- `socket()`
- `.bind()`
- `.listen()`
- `.accept()`

### socket
socket listens for the connections for clients. When the client connects, the server calls `.accept()` to accept or complete the connections.

The client calls `.connect()` to establish a connection to the server and initiate the three-way handshake. The handshake step is important because it ensures that each side of the connection is reachable in the network.

``` python
with socket.socket(socket.AF_INET, socket.SOCK_STREAM) as s:
    pass  # Use the socket object without calling s.close().
```


Note: with statement is used to wrap the execution of a block with methods defined by a context manager.

## Context Manager

- The Context Manager `__enter__()` is loaded for later use.
- The context manger's `__exit__()` is loaded for later use.
- The Context manager's `__enter__()` method is invoked.



# UDP socket
It is created with `socket.SOCK_DGRAM` aren't reliable, and data read by the receiver can be out of order from the sender's writes.

