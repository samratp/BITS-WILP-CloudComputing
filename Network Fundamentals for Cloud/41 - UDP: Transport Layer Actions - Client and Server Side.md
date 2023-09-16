In UDP (User Datagram Protocol), communication is connectionless and involves both a client and a server. Here are the actions typically performed on the client and server sides:

**Client Side Actions**:

1. **Socket Creation**:
   - The client creates a UDP socket to send data.

2. **Optional Binding**:
   - The client can optionally bind a specific local port to the socket. This is not mandatory in UDP.

3. **Data Preparation**:
   - The client prepares the data it wants to send. This could be a message, a packet, or any other form of data.

4. **Sending Data**:
   - The client uses the `sendto()` function to send the data to the server. The destination address (IP address and port) is specified.

5. **Optional Timeout Setting**:
   - The client may set a timeout value for the socket to handle cases where the server may not respond.

6. **Handling Errors (Optional)**:
   - The client should be prepared to handle potential errors that may occur during transmission.

**Server Side Actions**:

1. **Socket Creation**:
   - The server creates a UDP socket to receive data.

2. **Binding to a Port**:
   - The server binds the socket to a specific port (typically the port it wants to listen on for incoming data).

3. **Waiting for Data**:
   - The server enters a loop where it continuously waits for incoming data using the `recvfrom()` function.

4. **Data Reception**:
   - When data arrives, the server uses `recvfrom()` to receive the data along with the sender's address.

5. **Processing Data**:
   - The server processes the received data as per its application logic.

6. **Sending Response (Optional)**:
   - If a response is needed, the server can use `sendto()` to send data back to the client.

7. **Optional Error Handling**:
   - The server should be prepared to handle potential errors that may occur during reception or processing.

8. **Closing the Socket (Optional)**:
   - When the server is done listening, it can close the socket.

Remember, UDP being connectionless means there is no formal handshake or session setup. The server does not have to know about the existence of the client in advance. Each UDP packet is independent, and there is no acknowledgment of receipt.

Also, since UDP does not guarantee reliable delivery, it's important to implement mechanisms in the application layer (if needed) to handle lost or out-of-order packets.
