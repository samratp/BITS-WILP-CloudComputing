Transmission delay is the time it takes to push all the bits of a packet into the link for transmission. It depends on the size of the packet and the transmission rate of the link.

The formula for transmission delay is:

```
Transmission Delay (D_trans) = Packet Size (L) / Transmission Rate (R)
```

Here's an explanation of transmission delay with an example:

### Example:

Suppose you have a packet of data that needs to be transmitted over a network link. The packet size is 10,000 bits (or 10 kilobits), and the transmission rate of the link is 1 megabit per second (1 Mbps).

Using the formula:

```
D_trans = L / R
```

where `L` is the packet size and `R` is the transmission rate, we can calculate the transmission delay:

```
D_trans = 10,000 bits / 1,000,000 bits per second
        ≈ 0.01 seconds
```

So, in this example, the transmission delay is approximately 0.01 seconds, or 10 milliseconds.

### Interpretation:

This means that it will take 10 milliseconds to transmit the entire packet over the link. During this time, the bits are pushed into the link at a rate of 1 million bits per second.

Keep in mind that transmission delay is just one component of the total delay in network communication. Other factors like propagation delay, processing delay, queueing delay, and serialization delay also contribute to the overall time it takes for data to travel from the source to the destination.
