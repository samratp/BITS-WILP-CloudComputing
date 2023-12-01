The VXLAN (Virtual Extensible LAN) data plane is responsible for the encapsulation and decapsulation of Ethernet frames as they traverse a network. VXLAN is designed to extend Layer 2 network segments over Layer 3 networks, providing a scalable and flexible solution for network virtualization, especially in data center environments. Let's explore how the VXLAN data plane works:

1. **VXLAN Encapsulation:**
   - When a VM (Virtual Machine) sends an Ethernet frame within a VXLAN segment, the frame needs to be encapsulated for transmission over the underlying IP network (Layer 3).
   - VXLAN encapsulation involves adding a VXLAN header to the original Ethernet frame. The VXLAN header includes information such as the VXLAN Network Identifier (VNI), which identifies the specific VXLAN segment.

2. **VTEP (VXLAN Tunnel Endpoint):**
   - Each device functioning as a VTEP is responsible for the encapsulation and decapsulation of VXLAN frames.
   - The VTEP is typically located at the edge of the VXLAN network and serves as the entry and exit point for VXLAN traffic.

3. **VXLAN Header Format:**
   - The VXLAN header includes the following fields:
     - VNI (VXLAN Network Identifier): A 24-bit identifier that differentiates between different VXLAN segments.
     - Flags: Various flags used to control VXLAN features.
     - Reserved: Reserved bits for future use.
     - Next Protocol: Indicates the type of payload carried within the VXLAN packet (commonly set to 0x0800 for IP).

4. **Transmission over IP Network:**
   - The VXLAN-encapsulated frame is then transmitted over the IP network. The IP network acts as the transport medium for VXLAN traffic, allowing it to traverse routers and switches that may exist between VTEPs.

5. **VXLAN Decapsulation:**
   - When the VXLAN-encapsulated frame reaches the destination VTEP, the VTEP performs decapsulation to extract the original Ethernet frame.
   - The VTEP uses the information in the VXLAN header, such as the VNI, to determine the appropriate VXLAN segment for the frame.

6. **Forwarding Based on VNI:**
   - The VNI is crucial for forwarding the decapsulated frame to the correct VXLAN segment.
   - The VTEP looks up the VNI in its mapping table to determine the destination VXLAN segment and forwards the frame accordingly.

7. **Underlay Network:**
   - The underlay network, typically an IP network, is responsible for transporting VXLAN-encapsulated frames between VTEPs.
   - Routers in the underlay network treat VXLAN traffic as regular IP traffic and route it based on IP routing protocols.

8. **Integration with Physical Network:**
   - The VXLAN data plane integrates with the physical network infrastructure, allowing VXLAN traffic to traverse existing routers and switches without the need for modifications to the underlying network.

In summary, the VXLAN data plane enables the encapsulation and decapsulation of Ethernet frames for communication between VMs in different VXLAN segments over a Layer 3 network. VTEPs play a key role in this process, handling the VXLAN encapsulation at the source and decapsulation at the destination, while the underlay IP network serves as the transport medium for VXLAN traffic.
