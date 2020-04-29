* <https://netty.io/4.1/api/io/netty/channel/ChannelPipeline.html>

```
A list of ChannelHandlers which handles or intercepts inbound events and outbound operations of a Channel.
ChannelPipeline implements an advanced form of the Intercepting Filter pattern to give a user full control
 over how an event is handled and how the ChannelHandlers in a pipeline interact with each other.
```

* inbound: event <- socket.read
* outbound: operation -> socket.write

---