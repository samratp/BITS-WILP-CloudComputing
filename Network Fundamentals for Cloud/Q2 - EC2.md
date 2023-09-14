For a point-to-point link of length 30 km, at what value of link transmission rate (in Mbps or Megabits-per-sec) would the link propagation delay (at a speed of 2 × 108 m/sec) equal the transmission delay for 150-byte packets?

-------------

To calculate the propagation delay, you can use the formula:

$\[ \text{Propagation Delay} (D_{prop}) = \frac{\text{Distance} (D)}{\text{Propagation Speed} (S)} \]$

Given:
- $Distance (D) = 30 kilometers = \(30,000\) meters$
- $Propagation Speed (S) = \(2 \times 10^8\) meters/second$

Plugging in the values:

$\[ D_{prop} = \frac{30,000 \text{ meters}}{2 \times 10^8 \text{ meters/second}} \]$

$\[ D_{prop} \approx 0.00015 \text{ seconds} \]$

So, the propagation delay for a link distance of 30 kilometers with a speed of $\(2 \times 10^8\) meters/second$ is approximately 0.00015 seconds or 150 microseconds.

The transmission delay for a packet can be calculated using the formula:

$\[D_{trans} = \frac{\text{Packet Size (P)}}{\text{Link Speed (R)}}\]$

Given:
- $Transmission Delay (\(D_{trans}\)) = 0.00015 seconds$
- $Packet Size (\(P\)) = 150 bytes$

Plugging in the values:

$\[0.00015 = \frac{150}{R}\]$

Solving for $\(R\)$:

$\[R = \frac{150}{0.00015} \approx 1,000,000 \text{ bytes/second}\]$

To convert bytes per second to bits per second (since link speed is typically given in bits per second), we multiply by 8:

$\[R \approx 8,000,000 \text{ bits/second}\]$

So, the link speed is approximately 8 Mbps (megabits per second).
