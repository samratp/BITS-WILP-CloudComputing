TCP (Transmission Control Protocol) is considered connection-oriented due to several key features that are designed to ensure reliable and ordered data transmission between two devices. Here are the features of TCP that make it connection-oriented:

1. **Three-Way Handshake**:
   - TCP uses a three-way handshake process to establish a connection between a sender and a receiver before any data is transmitted. This handshake involves the following steps:
     - SYN (Synchronize) from sender to receiver
     - SYN-ACK (Synchronize-Acknowledge) from receiver to sender
     - ACK (Acknowledge) from sender to receiver

2. **Full-Duplex Communication**:
   - Once a connection is established, both the sender and receiver can send and receive data simultaneously. This enables two-way communication.

3. **Reliable Data Delivery**:
   - TCP guarantees that data will be delivered reliably to the receiver. It achieves this by using acknowledgments and retransmissions to ensure that any lost or damaged packets are retransmitted.

4. **In-Order Data Delivery**:
   - TCP ensures that data packets are delivered to the receiver in the same order they were sent. This is crucial for applications that require data integrity and sequencing.

5. **Flow Control**:
   - TCP implements flow control mechanisms to prevent the sender from overwhelming the receiver with data. It ensures that data is sent at a rate the receiver can handle, preventing congestion.

6. **Error Detection and Correction**:
   - TCP uses checksums to detect errors in transmitted data. If errors are detected, TCP requests retransmission of the affected packets.

7. **Connection Termination**:
   - When both the sender and receiver have finished their data exchange, TCP performs a four-way handshake to gracefully close the connection.

8. **Acknowledgments (ACK)**:
   - After data packets are received, the receiver sends acknowledgments (ACKs) back to the sender to confirm successful receipt. This feedback loop is integral to ensuring reliable delivery.

9. **Timeout and Retransmission**:
   - If an acknowledgment is not received within a certain time frame (known as a timeout period), TCP will retransmit the unacknowledged data packets.

10. **Stateful Protocol**:
    - TCP maintains a state table that keeps track of the state of each active connection. This information is used to manage the flow of data and ensure reliable delivery.

These features collectively make TCP connection-oriented, as it establishes a logical connection between two devices, maintains this connection throughout the data exchange, and ensures the reliable delivery of data. This is particularly important for applications that require data integrity, such as web browsing, file transfers, and email.
