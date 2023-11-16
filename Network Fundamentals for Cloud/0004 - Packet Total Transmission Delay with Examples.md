To calculate the total transmission delay of a packet, we need to consider all the components involved: propagation delay, transmission delay, processing delay, queueing delay, and serialization delay. The total transmission delay can be expressed as:

$\[D_{total} = D_{prop} + D_{trans} + D_{proc} + D_{queue} + D_{seri}\]$

Here is an example to illustrate the calculation of total transmission delay:

### Example:

Let's consider a scenario where you want to transmit a packet of 10,000 bits (or 10 kilobits) over a network link.

1. **Propagation Delay (D_prop)**:
   - Suppose the distance between the sender and receiver is 500 meters, and the speed of propagation in the medium is 200,000,000 meters per second.

   $\[D_{prop} = \frac{Distance}{Propagation Speed} = \frac{500\text{ meters}}{200,000,000\text{ meters/second}} \approx 0.0000025\text{ seconds}\]$

2. **Transmission Delay (D_trans)**:
   - Let's assume the transmission rate of the link is 1 megabit per second (1 Mbps).

   $\[D_{trans} = \frac{Packet Size}{Transmission Rate} = \frac{10,000\text{ bits}}{1,000,000\text{ bits/second}} = 0.01\text{ seconds}\]$

3. **Processing Delay (D_proc)**:
   - This can vary widely depending on the complexity of the routing and processing tasks. Let's assume it's negligible in this example.

   $\[D_{proc} = 0\text{ seconds}\]$

4. **Queueing Delay (D_queue)**:
   - Let's assume there's no significant queueing delay.

   $\[D_{queue} = 0\text{ seconds}\]$

5. **Serialization Delay (D_seri)**:
   - Serialization delay is the time taken to convert the packet into a bit stream for transmission. This depends on the link's transmission rate.

   $\[D_{seri} = \frac{Packet Size}{Transmission Rate} = \frac{10,000\text{ bits}}{1,000,000\text{ bits/second}} = 0.01\text{ seconds}\]$

Now, let's calculate the total transmission delay:

$\[D_{total} = D_{prop} + D_{trans} + D_{proc} + D_{queue} + D_{seri} \approx 0.0000025\text{ seconds} + 0.01\text{ seconds} + 0\text{ seconds} + 0\text{ seconds} + 0.01\text{ seconds} \approx 0.0200025\text{ seconds}\]$

So, in this example, the total transmission delay is approximately 20.0025 milliseconds. This is the time it takes for the packet to travel from the sender to the receiver, considering all the components of transmission delay.
