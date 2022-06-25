# Socket.io

Socket.IO is a library that enables low-latency, bidirectional and event-based communication between a client and a server.

It is built on top of the **WebSocket**  protocol and provides additional guarantees like fallback to HTTP long-polling or automatic reconnection.

## WebSocket
WebSocket is a computer communications protocol, providing full-duplex communication channels over a single TCP connection. The WebSocket protocol was standardized by the IETF as RFC 6455 in 2011. The current API specification allowing web applications to use this protocol is known as WebSockets.[1] It is a living standard maintained by the WHATWG and a successor to The WebSocket API from the W3C.[2]

WebSocket is distinct from HTTP. Both protocols are located at layer 7 in the OSI model and depend on TCP at layer 4. Although they are different, RFC 6455 states that WebSocket "is designed to work over HTTP ports 443 and 80 as well as to support HTTP proxies and intermediaries", thus making it compatible with HTTP. To achieve compatibility, the WebSocket handshake uses the HTTP Upgrade header[3] to change from the HTTP protocol to the WebSocket protocol.


## Listening to events


* **EventEmitter methods** : On the server-side, the Socket instance extends the Node.js EventEmitter class.
On the client-side, the Socket instance uses the event emitter provided by the component-emitter library, which exposes a subset of the EventEmitter methods.

* **socket.on**(eventName, listener)
Adds the listener function to the end of the listeners array for the event named eventName.

* **socket.once**(eventName, listener)
Adds a one-time listener function for the event named eventName.

* **socket.off**(eventName, listener)
Removes the specified listener from the listener array for the event named eventName.





