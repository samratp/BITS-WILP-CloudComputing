The **Spanning Tree Protocol (STP)** is a protocol used in computer networking to prevent loops in Ethernet networks. It works by designating certain network links as inactive, creating a loop-free logical topology. When a failure occurs, STP can quickly adapt to reconfigure the network.

Here's how STP works with an example:

**Scenario**:
Consider a simple network with three switches (A, B, and C) connected together.

```
         A
        / \
       B   C
```

1. **Initial Configuration**:

   - All links are active initially, which could lead to a loop in the network.

2. **Root Bridge Election**:

   - STP elects one switch as the **Root Bridge** based on the lowest Bridge ID. The Bridge ID is composed of a priority value and the switch's MAC address.
   - Let's say Switch A has the lowest Bridge ID, so it becomes the Root Bridge.

3. **Designated Ports**:

   - Each non-Root Bridge switch selects a single **Designated Port** to forward frames towards the Root Bridge. The Designated Port is the one with the lowest cost to reach the Root Bridge.

   - In our example, switches B and C will select the link towards A as their Designated Ports.

4. **Blocking Ports**:

   - The remaining ports on non-Root Bridges are placed in a blocking state. These ports do not forward frames; they only listen to BPDUs (Bridge Protocol Data Units).

   - In our example, one of the links between A and B, and one of the links between A and C will be placed in a blocking state.

   ```
             A
            / \
    (Block) B   C
   ```

5. **Forwarding and Listening States**:

   - Ports can transition between different states: **Blocking**, **Listening**, **Learning**, and **Forwarding**.

   - A port starts in **Blocking** state, then moves to **Listening** where it starts to receive BPDUs and prepares to transition to the **Learning** state.

   - After the Learning state, the port transitions to **Forwarding** where it actively forwards frames.

6. **Failure Scenario**:

   - Suppose the link between Switch B and Switch A fails.

   - STP will detect the failure and reconfigure the network.

   ```
            A
             \
              C
   ```

   - Switch C now has a direct link to the Root Bridge (A), and it will transition its Designated Port to Forwarding state.

   - Switch B, however, will still have its link to A in Blocking state.

   ```
             A
              \
               C
    (Block)   (Forward)
   ```

STP ensures that the network is loop-free and provides redundancy. In case of link or switch failures, it can rapidly adapt to reconfigure the network topology, ensuring uninterrupted communication.
