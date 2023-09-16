Certainly! Let's create a sample flow table with an example:

**Sample Flow Table**:

| Match Fields                       | Actions                   |
|------------------------------------|----------------------------|
| Source MAC: 00:1A:2B:3C:4D:5E       | Output Port: 2             |
| Source MAC: 00:1A:2B:3C:4D:5F       | Output Port: 3             |
| Source IP: 192.168.1.10            | Output Port: 4             |
| Source IP: 192.168.1.20            | Output Port: 5             |
| Destination IP: 10.0.0.1           | Output Port: 1             |
| Destination IP: 10.0.0.2           | Output Port: 2             |
| Source MAC: 00:1A:2B:3C:4D:5E       | Drop Packet                |
| Source IP: 192.168.1.30            | Send to Controller         |

**Example Explanation**:

Let's break down the sample flow table:

1. If the source MAC address is `00:1A:2B:3C:4D:5E`, forward the packet out of Port 2.
2. If the source MAC address is `00:1A:2B:3C:4D:5F`, forward the packet out of Port 3.
3. If the source IP address is `192.168.1.10`, forward the packet out of Port 4.
4. If the source IP address is `192.168.1.20`, forward the packet out of Port 5.
5. If the destination IP address is `10.0.0.1`, forward the packet out of Port 1.
6. If the destination IP address is `10.0.0.2`, forward the packet out of Port 2.
7. If the source MAC address is `00:1A:2B:3C:4D:5E`, drop the packet (do not forward).
8. If the source IP address is `192.168.1.30`, send the packet to the SDN controller for further processing.

**Example Usage**:

Suppose a packet arrives at the switch with the following characteristics:

- Source MAC address: `00:1A:2B:3C:4D:5F`
- Source IP address: `192.168.1.20`
- Destination IP address: `10.0.0.2`

Based on the sample flow table:

- The first rule matches the source MAC address, so the packet is forwarded out of Port 3.
- The second rule matches the source IP address, but it doesn't affect the forwarding decision in this case.
- The fifth rule matches the destination IP address, so it doesn't affect the forwarding decision either.

In this example, the packet would be forwarded out of Port 3 based on the first rule in the flow table.
