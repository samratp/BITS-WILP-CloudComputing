The VXLAN (Virtual Extensible LAN) packet format includes headers and encapsulation to enable the creation of overlay networks. VXLAN encapsulates Layer 2 Ethernet frames within UDP (User Datagram Protocol) packets, allowing for the transmission of Layer 2 traffic over Layer 3 networks. Here's an overview of the VXLAN packet format:

### VXLAN Packet Components:

1. **Ethernet Frame:**
   - The original Layer 2 Ethernet frame is the payload that needs to be transmitted over the VXLAN network. This frame includes source and destination MAC addresses, EtherType, VLAN tags, and the actual data.

2. **VXLAN Header:**
   - The VXLAN header is added to the original Ethernet frame. It includes the following fields:
     - **VXLAN Network Identifier (VNI):** A 24-bit identifier that represents the VXLAN segment. Each VNI corresponds to a unique VXLAN segment.
     - **Reserved Bits:** Reserved for future use.

3. **UDP Header:**
   - The VXLAN-encapsulated packet is then placed within a UDP packet. The UDP header includes the following information:
     - **Source Port:** The source port used for the VXLAN UDP tunnel.
     - **Destination Port:** The destination port used for the VXLAN UDP tunnel.
     - **Length:** The length of the UDP packet.
     - **Checksum:** An optional field that can be used for error checking.

4. **IP Header:**
   - The VXLAN-encapsulated UDP packet is further encapsulated within an IP packet. The IP header contains standard information, such as source and destination IP addresses, Time-to-Live (TTL), and protocol information.
     - **Protocol:** Identifies the protocol being carried in the payload (UDP in the case of VXLAN).

5. **Underlying Network Header:**
   - The entire VXLAN-encapsulated packet is carried within the payload of an underlying network packet. This could be an IP packet in the case of Layer 3 networks.

### VXLAN Packet Diagram:

```
+---------------------+
| Original Ethernet  |
| Frame (Layer 2)     |
+---------------------+
| VXLAN Header        |
|   - VNI              |
|   - Reserved         |
+---------------------+
| UDP Header          |
|   - Source Port      |
|   - Destination Port |
|   - Length           |
|   - Checksum         |
+---------------------+
| IP Header           |
|   - Source IP        |
|   - Destination IP   |
|   - TTL               |
|   - Protocol (UDP)   |
+---------------------+
| Underlying Network  |
| Header (e.g., IP)   |
+---------------------+
| Payload (VXLAN-     |
| encapsulated frame) |
+---------------------+
```

### VXLAN Packet Flow:

1. The original Layer 2 Ethernet frame is encapsulated with a VXLAN header, which includes the VNI and reserved bits.
2. The VXLAN-encapsulated packet is then placed within a UDP packet with source and destination ports.
3. The UDP packet is further encapsulated within an IP packet with source and destination IP addresses.
4. The entire VXLAN-encapsulated packet becomes the payload of an underlying network packet (e.g., an IP packet in the case of Layer 3 networks).
5. The VXLAN-encapsulated packet is transmitted over the underlying network to the destination VTEP (VXLAN Tunnel Endpoint).
6. At the destination VTEP, the VXLAN packet is decapsulated to reveal the original Layer 2 Ethernet frame, which is then delivered to the destination host.

VXLAN's encapsulation allows the extension of Layer 2 networks over Layer 3 networks, facilitating communication between hosts in different physical locations or across data centers. The use of UDP as a transport protocol makes VXLAN flexible and compatible with existing IP networks.
