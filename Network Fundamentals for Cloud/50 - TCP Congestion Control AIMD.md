**TCP Congestion Control - AIMD (Additive Increase, Multiplicative Decrease)** is a widely used algorithm for managing congestion in TCP connections. It strikes a balance between aggressive sending and conservative throttling of data transmission to avoid network congestion.

Here's how AIMD works:

1. **Additive Increase**:

   - During the **Congestion Avoidance** phase (after Slow Start), TCP increases the congestion window (cwnd) by one segment for each successful round-trip time (RTT).
  
   - This means that for every round trip in which an acknowledgment is received without detecting any packet loss, the sender is allowed to send one additional segment.

2. **Multiplicative Decrease**:

   - If the sender detects a packet loss (usually through the receipt of multiple duplicate acknowledgments or a timeout), it assumes that the network is congested.
  
   - In response, TCP performs a **Multiplicative Decrease** by cutting its congestion window in half. This reduces the sending rate to alleviate potential congestion.

3. **AIMD in Action**:

   - Initially, during Slow Start, the congestion window grows exponentially (doubling for each RTT) until a congestion event occurs.

   - After a congestion event (packet loss), the congestion window is reduced by half. This is the "Multiplicative Decrease."

   - Then, during Congestion Avoidance, the window size increases linearly (additively) for each RTT.

   - This cycle repeats, resulting in a sawtooth-shaped congestion window graph.

**Example**:

1. **Slow Start Phase**:

   - Suppose the initial cwnd is 2.

   - In each round trip, if both segments are acknowledged, the cwnd doubles (2 -> 4 -> 8 -> ...).

   - If a congestion event occurs (packet loss), it transitions to the Congestion Avoidance phase.

2. **Congestion Avoidance Phase**:

   - If a packet loss is detected, the cwnd is halved (e.g., from 8 to 4).

   - In this phase, cwnd increases additively for each successful RTT.

   - For example, if all segments are acknowledged in a round trip, cwnd increases by 1.

   - If another congestion event occurs, the process repeats.

AIMD helps TCP achieve a good balance between aggressive sending (to fully utilize the network) and conservative throttling (to prevent congestion). This allows TCP to efficiently use available network resources while also being responsive to network conditions.
