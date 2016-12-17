## Playing with sockets

1. Write the HTTP client written pictured in lecture 5 and make it run. 

2. Change it so the last line of the output gives the number of TCP segments used to recieve the data from the server.
Why are we recieving the data in several chuncks? Ask if unsure.

3. Pair with someone. One of you will write a TCP server. The other will write a TCP client. In both case you will use the [`net` module's documentation](https://nodejs.org/api/net.html) to write your code.

For the *server*, your code will:

* have a function named `handleConnection`, taking an argument `conn`, a [net.Socket](https://nodejs.org/api/net.html#net_class_net_socket) object. This function will:
    * write to the server's console (with `console.log`) the address (see `server.address()` method of `net`) of any client that connects to it
    * specify what happens when the server recieve events, such as new data arrives through the stream (`conn`). For now, we'll only have an event handler for the `data` event emitted by `conn`.
* The `data` event handler will take a callback that writes to the stream (hints: net.Socket extends the [`Stream` module](https://nodejs.org/api/stream.html) which has a [`.write`](https://nodejs.org/api/stream.html#stream_writable_write_chunk_encoding_callback) method to write to it).
* create a server with `createServer` and bind the `connection` event to the previously defined `handleConnection` function.
* listen to traffic on a specific port (e.g. 9000, has to 1024 or above);


For the *client*, your code will:

* create an instance of `net.Socket`
* have an event handler on the socket for `data`, which will write to the console of the client any response from the server
* use [socket.Connect](https://nodejs.org/api/net.html#net_socket_connect_options_connectlistener) to send data to the server through the socket (hints: `net.Socket` extends the [`Stream` module](https://nodejs.org/api/stream.html) which has a [`.write`](https://nodejs.org/api/stream.html#stream_writable_write_chunk_encoding_callback) method to write to it).
