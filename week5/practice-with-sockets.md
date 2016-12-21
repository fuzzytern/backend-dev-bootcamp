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

4. Login on the machine as priviledged user (ask Nicolas) and install Wireshark (`sudo apt-get install wireshark` - say `No` at the prompt during install). Open it with `sudo` and capture the TCP trafic that comes from the IP address of your partner by applying the proper filters (you will need to know their IP address). You can read more about filters on the official [
Wireshark documentation](https://wiki.wireshark.org/CaptureFilters)

5. On the server (pair with your partner): Once the request is completely recieved, then read a file from your disk and send its content back to the client. Look up the `fs` module on the Nodejs documentation and find out which of the following functions are most relevant to our scenario: `createReadStream`, `readFileSync`, `readFile`, `readSync`.

6. On the client, forge a HTTP request manually using the information in [RFC 7230](https://tools.ietf.org/html/rfc7230#section-2.1) (do not use the `http` module). Your request will be a `GET` and ask for a resource named `data.json`. On the server, parse the HTTP request manually by inspecting the HTTP headers, and read the requested resource from the filesystem (you'll have to make sure to create a `data.json` file) and send its data over the stream. 
Bonus: your server's answer should be a proper HTTP resonse (see RFC above). Have your client confirm it recieved a `200` HTTP code to its request (you can read more about status code in [RFC 2616](https://www.ietf.org/rfc/rfc2616.txt)).

7. Refactor your code (client and server) using the `http` module (see official doc.) and get rid of the `net` in both places.
