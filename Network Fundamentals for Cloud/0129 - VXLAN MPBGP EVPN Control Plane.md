The VXLAN (Virtual Extensible LAN) control plane using MP-BGP (Multiprotocol BGP) with EVPN (Ethernet Virtual Private Network) is a more sophisticated and scalable approach compared to simpler methods like Flood and Learn. MP-BGP EVPN is widely used for VXLAN-based network virtualization in data center environments. This control plane provides mechanisms for efficient MAC address learning, VTEP discovery, and VXLAN segment information distribution. Let's explore the key components and how it works:

1. **MP-BGP EVPN Overview:**
   - MP-BGP is extended to support address families beyond IPv4 and IPv6, allowing it to carry Ethernet VPN (EVPN) information.
   - EVPN is a BGP address family that is specifically designed for distributing MAC and IP routing information in data center networks.

2. **VTEP Discovery:**
   - VTEPs use MP-BGP EVPN to advertise their presence and capabilities.
   - BGP route type 2 (RT-2) is used for VTEP advertisement. Each VTEP advertises its loopback address and associated attributes.

3. **VNI Advertisement:**
   - MP-BGP EVPN is used to distribute information about VXLAN segments (VNIs) and the corresponding VTEPs.
   - BGP route type 5 (RT-5) is employed for VNI advertisement. This includes the mapping of VNIs to VTEP IP addresses.

4. **MAC Address Learning:**
   - EVPN introduces BGP route type 2 (RT-2) for MAC address advertisement. When a VTEP learns a MAC address, it advertises it to other VTEPs in the network.
   - BGP route type 2 carries the MAC address, the associated VNI, and the IP address of the advertising VTEP.

5. **ARP/ND (Address Resolution Protocol/Neighbor Discovery):**
   - In addition to MAC address learning, MP-BGP EVPN can carry ARP/ND information.
   - BGP route type 3 (RT-3) is used for advertising ARP/ND information. This allows VTEPs to learn the mapping between IP addresses and MAC addresses.

6. **Integration with Layer 3 Routing:**
   - MP-BGP EVPN enables the integration of Layer 2 and Layer 3 routing in the data center.
   - BGP route type 5 (RT-5) can carry both Layer 2 (MAC and VNI information) and Layer 3 (IP prefixes) information.

7. **Redundancy and High Availability:**
   - MP-BGP EVPN supports mechanisms for redundancy and high availability. Multiple active-active VTEPs can share load and provide failover capabilities.
   - BGP route type 8 (RT-8) is used for Ethernet AD (Active-Active) routes, indicating that multiple VTEPs can be active for a given MAC-VRF (MAC Virtual Routing and Forwarding) instance.

8. **Route Target (RT) and Route Distinguishers (RD):**
   - RTs and RDs are used in BGP to distinguish between different VPNs and prevent overlapping of route information.

In summary, the VXLAN control plane using MP-BGP EVPN provides a robust and scalable solution for VXLAN-based network virtualization in data centers. It enables dynamic learning of MAC and IP information, efficient VTEP discovery, and seamless integration with Layer 3 routing, offering a more sophisticated alternative to simpler control plane mechanisms like Flood and Learn.
