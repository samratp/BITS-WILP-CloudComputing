Wireshark is a powerful network protocol analyzer that allows you to capture and analyze the data traveling through your network. Below is a sample output from Wireshark, showing a simplified view of captured packets:

```
Frame 1: 74 bytes on wire (592 bits), 74 bytes captured (592 bits)
Ethernet II, Src: 00:0c:29:6c:92:af (Cadmus C)
Destination: IntelCor_36:a3:55 (00:21:5a:36:a3:55)
Type: IP (0x0800)
Internet Protocol Version 4, Src: 192.168.1.101, Dst: 173.194.72.100
Transmission Control Protocol, Src Port: 53560, Dst Port: https (443), Seq: 1, Ack: 1
Hypertext Transfer Protocol (GET / HTTP/1.1\r\nHost: www.google.com\r\n\r\n)
```

**Explanation**:

1. **Frame Information**:
   - Frame Number: 1
   - Frame Length: 74 bytes on wire (592 bits)
   - Captured Length: 74 bytes captured (592 bits)

2. **Ethernet II Header**:
   - Source MAC Address: 00:0c:29:6c:92:af
   - Destination MAC Address: 00:21:5a:36:a3:55
   - Type: IP (0x0800)

3. **IP Header**:
   - Version: 4 (IPv4)
   - Source IP Address: 192.168.1.101
   - Destination IP Address: 173.194.72.100

4. **TCP Header**:
   - Source Port: 53560
   - Destination Port: https (443)
   - Sequence Number: 1
   - Acknowledgment Number: 1

5. **HTTP Data**:
   - This section shows an HTTP GET request:
     ```
     GET / HTTP/1.1
     Host: www.google.com
     ```

This output represents a captured packet where a device at IP address 192.168.1.101 is sending an HTTP GET request to www.google.com on port 443 (HTTPS).

Please note that this is a simplified and truncated example. A real-world packet capture in Wireshark would contain many more details, including additional protocol headers, flags, options, and more. Wireshark provides a comprehensive view of the data traveling through a network, which is invaluable for network troubleshooting and analysis.
