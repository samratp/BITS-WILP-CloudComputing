In OpenFlow, the header fields of incoming packets are used to determine how they should be processed by the switches. These header fields are referred to as "match fields". When a packet arrives at a switch, OpenFlow uses specific header entries to match against flow table entries. Here are some of the key header entries used for matching in OpenFlow:

**Layer 2 (Data Link Layer):**

1. **Ethernet Source Address (Src MAC)**
   - Matches the source MAC address of the Ethernet frame.

2. **Ethernet Destination Address (Dst MAC)**
   - Matches the destination MAC address of the Ethernet frame.

3. **Ethernet Type (EtherType)**
   - Specifies the type of payload carried in the Ethernet frame (e.g., IPv4, IPv6, ARP, etc.).

4. **VLAN ID (VID)**
   - Matches the VLAN ID in a VLAN-tagged frame.

5. **VLAN Priority (PCP)**
   - Matches the VLAN priority (802.1p) in a VLAN-tagged frame.

**Layer 3 (Network Layer):**

6. **IP Protocol (IP_PROTO)**
   - Matches the protocol type in the IP header (e.g., TCP, UDP, ICMP).

7. **IPv4 Source Address (Src IP)**
   - Matches the source IPv4 address.

8. **IPv4 Destination Address (Dst IP)**
   - Matches the destination IPv4 address.

9. **IPv6 Source Address (Src IPv6)**
   - Matches the source IPv6 address.

10. **IPv6 Destination Address (Dst IPv6)**
    - Matches the destination IPv6 address.

**Layer 4 (Transport Layer):**

11. **Transport Layer Source Port (Src Port)**
    - Matches the source port of the transport layer protocol (e.g., TCP or UDP port).

12. **Transport Layer Destination Port (Dst Port)**
    - Matches the destination port of the transport layer protocol.

**Layer 4-7 (Transport, Session, Presentation, Application Layers):**

13. **TCP Flags (TCP Flags)**
    - Matches specific TCP control flags (e.g., SYN, ACK, FIN, etc.).

14. **ICMP Type and Code (ICMP Type, ICMP Code)**
    - Matches the ICMP message type and code.

15. **ICMPv6 Type and Code (ICMPv6 Type, ICMPv6 Code)**
    - Matches the ICMPv6 message type and code.

16. **ARP Operation (ARP_OP)**
    - Matches the type of ARP operation (e.g., request or reply).

17. **ARP Sender/Target Protocol Address (ARP SPA/TPA)**
    - Matches the source or target protocol address in an ARP packet.

These OpenFlow header entries allow for fine-grained control over packet forwarding based on specific attributes at different layers of the OSI model. They are used to define flow table entries that determine how network traffic is processed and forwarded within an OpenFlow-enabled network.
