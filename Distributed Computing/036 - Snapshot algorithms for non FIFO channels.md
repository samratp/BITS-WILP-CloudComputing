In non-FIFO (First In, First Out) distributed systems, messages can be received out of the order in which they were sent. This introduces complications when taking consistent snapshots, as the Chandy-Lamport algorithm assumes FIFO message delivery between processes. To handle this, several algorithms have been proposed that adapt the snapshot mechanism to work in non-FIFO systems by introducing techniques such as **message inhibition** and **message piggybacking**.

### Snapshot Algorithms for Non-FIFO Channels

#### 1. **Message Inhibition** (Helary’s Algorithm)
In Helary’s algorithm, **message inhibition** is used to ensure that processes correctly capture the state of the communication channels. The key idea is to temporarily delay or inhibit the processing of certain application messages during the snapshot process.

- **Inhibition**: Once a process has initiated or received a snapshot marker, it temporarily **inhibits** the processing of incoming computation messages (i.e., messages related to the application) on its incoming channels. This delay ensures that the state of the channels can be captured consistently, even in a non-FIFO system.
- **Channel State Recording**: By delaying message processing, the algorithm guarantees that the in-transit messages are captured in the correct order, and the system state is consistent with the snapshot.

This inhibition ensures that no messages sent before the snapshot marker are incorrectly recorded as part of the post-snapshot state.

#### 2. **Message Piggybacking**
In contrast to Helary’s inhibition-based approach, **message piggybacking** is a technique where additional information is attached to messages to help distinguish between those sent **before** and **after** a snapshot marker. This approach is used in several non-FIFO snapshot algorithms, including:

- **Lai-Yang Algorithm**
- **Li et al. Algorithm**
- **Mattern's Algorithm**

Here’s how message piggybacking works:

- **Piggybacking Information**: A snapshot marker is not sent as a separate message. Instead, it is **piggybacked** (attached) onto computation messages. This piggybacked information helps the receiving process determine whether a message was sent before or after the snapshot started.
- **Channel State Recording**: When a process receives a message, it checks the piggybacked information to decide if the message should be considered part of the snapshot (i.e., sent before the snapshot marker) or if it should be recorded as part of the post-snapshot state (sent after the marker).
  
### Examples of Non-FIFO Snapshot Algorithms Using Piggybacking:

#### **Lai-Yang Algorithm**:
- Processes initiate the snapshot and piggyback a special marker on their computation messages.
- Each process records its local state when it first sends or receives a marker.
- When a process receives a message, it uses the piggybacked marker to determine if the message should be considered part of the channel's pre-snapshot state or post-snapshot state.

#### **Li et al. Algorithm**:
- Similar to Lai-Yang, this algorithm piggybacks information about the snapshot onto computation messages.
- It distinguishes between the pre-snapshot and post-snapshot messages to ensure consistency.
- Each process records the local state and the messages in transit using the piggybacked information.

#### **Mattern's Algorithm**:
- Mattern's approach also uses **piggybacking** but is optimized for vector clocks. Each process maintains a vector clock and piggybacks its clock value on messages.
- The snapshot is determined based on the vector clocks, which ensure that the causal relationships between messages are preserved even in a non-FIFO system.

### Comparison of Techniques:

| **Technique**          | **Description**                                                                                                 | **Pros**                                                      | **Cons**                                                      |
|------------------------|-----------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------|---------------------------------------------------------------|
| **Message Inhibition**  | Delays the execution of processes temporarily to ensure channel states are recorded correctly.                  | Simple to implement; ensures a consistent snapshot.            | Can delay the application’s execution, affecting performance.  |
| **Message Piggybacking**| Piggybacks marker information on computation messages to distinguish pre- and post-snapshot messages.           | Does not delay application messages; more efficient in practice.| Adds overhead by piggybacking extra information to messages.   |

### Conclusion:

In non-FIFO systems, **message inhibition** (as used in Helary's algorithm) or **message piggybacking** (as used in the Lai-Yang, Li et al., and Mattern algorithms) can be employed to ensure that consistent global snapshots are taken. Message inhibition delays message processing to maintain order, while piggybacking attaches extra information to computation messages to differentiate between those sent before and after a snapshot. These techniques ensure that even in systems where message order is not guaranteed, a consistent system state can be recorded.
