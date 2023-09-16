**Transmission Control Protocol (TCP)** is a core protocol of the Internet Protocol (IP) suite. It provides reliable, connection-oriented communication between devices over a network. Here are some details, examples, and common uses of TCP:

**Details**:

1. **Connection-Oriented**:
   - TCP establishes a connection between sender and receiver before data transmission. It ensures that data is reliably delivered and in the correct order.

2. **Reliable**:
   - TCP guarantees the delivery of data packets. It uses acknowledgments and retransmissions to achieve this.

3. **Flow Control**:
   - TCP manages the rate at which data is sent to avoid overwhelming the receiver. It prevents fast senders from overwhelming slow receivers.

4. **Congestion Control**:
   - It adjusts the rate of data transmission based on network conditions to prevent network congestion.

5. **Full-Duplex Communication**:
   - Data can be sent in both directions simultaneously. This means that data can be sent and received at the same time.

6. **Connection Termination**:
   - It gracefully terminates the connection after data exchange, ensuring that all data is delivered.

7. **Error Checking**:
   - TCP uses checksums to verify the integrity of data. If a packet arrives with an error, it will be discarded, and a retransmission will be requested.

**Examples**:

```plaintext
TCP Header:
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|    Source Port (16 bits)    |  Destination Port (16 bits)     |
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|                   Sequence Number (32 bits)                   |
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|                Acknowledgment Number (32 bits)                |
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
| Data  | Rese  | Control Flags |           Window (16 bits)    |
|  Offset | rved  |              |                              |
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
| Checksum (16 bits)          |    Urgent Pointer (16 bits)     |
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
| Options / Padding (Variable)                                  |
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|                             Data ...                          |
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
```

**Common Uses**:

1. **Web Browsing (HTTP/HTTPS)**:
   - When you visit a website, your browser uses TCP to establish a connection to the web server and retrieve the web pages.

2. **Email (SMTP, POP3, IMAP)**:
   - Protocols like SMTP (Simple Mail Transfer Protocol), POP3 (Post Office Protocol version 3), and IMAP (Internet Message Access Protocol) use TCP to send and receive emails.

3. **File Transfer (FTP)**:
   - TCP is used in FTP for transferring files between a client and a server.

4. **Secure Shell (SSH)**:
   - SSH is a network protocol that allows secure communication over an unsecured network. It relies on TCP for reliable data delivery.

5. **Remote Desktop (RDP)**:
   - RDP, used for remote desktop access, relies on TCP for stable connections.

6. **Database Access (MySQL, PostgreSQL, etc.)**:
   - Databases use TCP to allow clients to connect and interact with them.

7. **VoIP Calls (using protocols like SIP)**:
   - TCP is used in Voice over Internet Protocol (VoIP) systems for call setup and signaling.

8. **Online Gaming (for updates, chat, etc.)**:
   - In gaming applications, TCP may be used for features that require reliable delivery, like game updates or chat.

TCP is chosen for applications where data integrity and reliability are crucial. It is ideal for scenarios where ensuring that all data is delivered correctly and in order is more important than minimizing latency.
