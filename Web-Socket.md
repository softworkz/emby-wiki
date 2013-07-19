Clients are recommended to connect to the server's web socket in order to receive notifications of various system events, which can help reduce the need to repeatedly poll for data through the http api.

#### Finding the web socket port

Make a call to /System/Info. WebSocketPortNumber is the port hosting the web socket. From there the connection url is:

`
ws://hostname:{websocketport}/mediabrowser
`