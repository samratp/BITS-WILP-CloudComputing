A butterfly network is a technique to link multiple computers into a high-speed network. This form of multistage interconnection network topology can be used to connect different nodes in a multiprocessor system. The interconnect network for a shared memory multiprocessor system must have low latency and high bandwidth unlike other network systems, like local area networks (LANs) or internet for three reasons:

- Messages are relatively short as most messages are coherence protocol requests and responses without data.
- Messages are generated frequently because each read-miss or write-miss generates messages to every node in the system to ensure coherence. Read/write misses occur when the requested data is not in the processor's cache and must be fetched either from memory or from another processor's cache.
- Messages are generated frequently, therefore rendering it difficult for the processors to hide the communication delay.

![image](https://github.com/user-attachments/assets/af4237dd-5679-4756-a587-71c5c2277bff)

The major components of an interconnect network are:

- Processor nodes, which consist of one or more processors along with their caches, memories and communication assist.
- Switching nodes (Router), which connect communication assist of different processor nodes in a system. In multistage topologies, higher level switching nodes connect to lower level switching nodes as shown in figure 1, where switching nodes in rank 0 connect to processor nodes directly while switching nodes in rank 1 connect to switching nodes in rank 0.
- Links, which are physical wires between two switching nodes. They can be uni-directional or bi-directional.

## Butterfly network routing

![image](https://github.com/user-attachments/assets/70727f86-051d-456a-9e88-fb822070aa55)

In a wrapped butterfly network (which means rank 0 gets merged with rank 3), a message is sent from processor 5 to processor 2. In figure 2, this is shown by replicating the processor nodes below rank 3. The packet transmitted over the link follows the form:

Header	Payload	Trailer
The header contains the destination of the message, which is processor 2 (010 in binary). The payload is the message, M and trailer contains checksum. Therefore, the actual message transmitted from processor 5 is:

010	M	checksum
Upon reaching a switching node, one of the two output links is selected based on the most significant bit of the destination address. If that bit is zero, the left link is selected. If that bit is one, the right link is selected. Subsequently, this bit is removed from the destination address in the packet transmitted through the selected link. This is shown in figure.

- The above packet reaches N(0,5). From the header of the packet it removes the leftmost bit to decide the direction. Since it is a zero, left link of N(0,5) (which connects to N(1,1)) gets selected. The new header is '10'.
- The new packet reaches N(1,1). From the header of the packet it removes the leftmost bit to decide the direction. Since it is a one, right link of N(1,1) (which connects to N(2,3)) gets selected. The new header is '0'.
- The new packet reaches N(2,3). From the header of the packet it removes the leftmost bit to decide the direction. Since it is a zero, left link of N(2,3) (which connects to N(3,2)) gets selected. The header field is empty.
- Processor 2 receives the packet, which now contains only the payload 'M' and the checksum.
