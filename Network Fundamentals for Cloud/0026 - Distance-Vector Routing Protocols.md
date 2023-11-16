Distance-vector routing protocols operate based on the number of hops (or distance) to reach a destination network. These protocols periodically exchange routing tables with neighboring routers and use metrics like hop count, bandwidth, or delay to make routing decisions. Here are some of the well-known distance-vector routing protocols:

1. **RIP (Routing Information Protocol)**:
   - **Description**: RIP is one of the oldest and simplest distance-vector routing protocols. It uses hop count as its metric. Routes with fewer hops are considered better.
   - **Characteristics**: Suitable for small to medium-sized networks. Converges relatively slowly compared to link-state protocols like OSPF.
   - **Version**: RIP Version 1 and RIP Version 2 (which supports subnetting and variable-length subnet masks - VLSM).

2. **IGRP (Interior Gateway Routing Protocol)**:
   - **Description**: IGRP is a Cisco proprietary distance-vector routing protocol that uses a more sophisticated metric than RIP. It considers factors like bandwidth, delay, reliability, and load.
   - **Characteristics**: Designed for larger networks and provides faster convergence compared to RIP.

3. **EIGRP (Enhanced Interior Gateway Routing Protocol)**:
   - **Description**: EIGRP is an advanced Cisco proprietary protocol that incorporates features of both distance-vector and link-state routing. It uses a composite metric that includes factors like bandwidth, delay, reliability, and load.
   - **Characteristics**: Balances simplicity and accuracy, provides rapid convergence. Supports both IP and IPv6.

4. **H-Route**:
   - **Description**: H-Route is a simple distance-vector protocol used in some specific networks. It is not as widely used as RIP or IGRP.

Key Characteristics of Distance-Vector Protocols:

- **Periodic Updates**: Routers periodically exchange their routing tables with neighboring routers. This can introduce overhead on the network.

- **Convergence Time**: Distance-vector protocols may have slower convergence times compared to link-state protocols. Convergence time is the time it takes for routers to update their routing tables after a change in the network.

- **Routing Loops**: Distance-vector protocols may suffer from the "count-to-infinity" problem, where incorrect routing information can circulate the network.

- **Ease of Configuration**: They are generally simpler to configure compared to link-state protocols.

- **Suitability for Small to Medium Networks**: Distance-vector protocols like RIP are well-suited for small to medium-sized networks with relatively simple topologies.

It's worth noting that while distance-vector protocols are still used in some environments, more modern networks often rely on link-state protocols like OSPF or EIGRP, or use BGP for inter-domain routing on the internet.
