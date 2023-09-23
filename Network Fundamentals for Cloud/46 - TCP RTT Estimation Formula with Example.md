The estimation of Round-Trip Time (RTT) in TCP is crucial for various aspects of the protocol, including retransmission timeout calculation and congestion control. The RTT estimation is done using an Exponentially Weighted Moving Average (EWMA) approach. The formula for estimating RTT is:

$\[EstimatedRTT = (1 - \alpha) \cdot EstimatedRTT + \alpha \cdot SampleRTT\]$

Where:
- $\(EstimatedRTT\)$ is the current estimate of the round-trip time.
- $\(\alpha\)$ is the smoothing factor (usually between 0.1 and 0.3).
- $\(SampleRTT\)$ is the measured round-trip time for a specific segment.

Let's go through an example:

Suppose we have the following scenario:

- Initial $\(EstimatedRTT\)$ = 100 ms
- $\(SampleRTT\)$ for a transmitted segment = 120 ms
- Chosen $\(\alpha\)$ value = 0.2

Using the formula:

$\[EstimatedRTT = (1 - 0.2) \cdot 100 + 0.2 \cdot 120\]$

$\[EstimatedRTT \approx 80 + 24 \approx 104 \text{ ms}\]$

In this example, the new estimate of the round-trip time $(\(EstimatedRTT\))$ is approximately 128 ms.

Keep in mind that this process continues for each transmitted segment, allowing the TCP sender to adapt its estimate of the round-trip time based on the actual measurements. This helps TCP respond to changes in network conditions and adjust its retransmission behavior accordingly.
