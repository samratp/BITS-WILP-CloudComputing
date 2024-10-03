### Synchronous Single-Initiator Spanning Tree Algorithm Using Flooding

A **spanning tree** in a network is a subgraph that connects all the nodes without creating any cycles. A **synchronous spanning tree algorithm** ensures that all processes operate in coordinated steps, and the **flooding technique** is a widely used approach in building such trees. In the **single-initiator version**, only one process (the initiator) starts the process of building the spanning tree.

This algorithm works in synchronous systems where each process knows when a message is received or sent in each round of communication. Here is how the algorithm operates.

---

### Algorithm Overview:

1. **Assumptions**:
   - The system is **synchronous** (i.e., each process has a bound on how long it takes to send/receive a message).
   - There is one **initiator** process that starts the process.
   - All processes are connected in an undirected graph, but they do not know the full topology of the network.

2. **Key Terms**:
   - **Parent**: A process assigns a parent to itself as it gets added to the spanning tree.
   - **Flooding**: The initiator broadcasts a message to all neighbors, and each node that receives the message further propagates it to its neighbors.
   - **Acknowledgment**: After a node finishes processing its children’s messages, it sends a confirmation message (ack) to its parent.

---

### Algorithm Steps:

1. **Initiator's Action**:
   - The initiator process `P0` (the root of the spanning tree) sends a "FLOOD" message to all its neighbors.
   - The initiator assigns itself as the root of the spanning tree.

2. **Receiver's Action** (Non-Initiator Processes):
   - Each process `P` receiving the "FLOOD" message for the **first time**:
     - Assigns the sender as its **parent**.
     - Forwards the "FLOOD" message to all its **neighbors** except the parent.
     - Waits for acknowledgments from all its neighbors before sending an acknowledgment to its parent.
   - If a process receives the "FLOOD" message for the **second time or later**, it simply discards the message since it is already part of the tree.

3. **Termination**:
   - A process sends an acknowledgment (ack) back to its parent once it has received acks from all the neighbors it forwarded the message to.
   - The initiator terminates when it receives acknowledgments from all its neighbors, indicating the completion of the spanning tree construction.

---

### Example:

Consider a network of 7 nodes connected in a mesh, where process `P0` is the initiator.

```
    P0
   /  \
 P1    P2
  |   /  \
 P3  P4  P5
      |
     P6
```

1. **Round 1**:
   - `P0` sends "FLOOD" to `P1` and `P2`.
   - `P1` and `P2` set `P0` as their parent and forward the "FLOOD" message to their neighbors (`P3`, `P4`, and `P5`).

2. **Round 2**:
   - `P1` sends "FLOOD" to `P3`, and `P2` sends "FLOOD" to `P4` and `P5`.
   - `P3` sets `P1` as its parent, `P4` and `P5` set `P2` as their parent.

3. **Round 3**:
   - `P4` forwards the "FLOOD" message to `P6`. `P6` sets `P4` as its parent.
   - All nodes forward the "FLOOD" message to their neighbors who have already received the message, so those messages are discarded.

4. **Acknowledgment Phase**:
   - `P6`, `P3`, and `P5` send an acknowledgment (ack) to their parents (`P4`, `P1`, and `P2` respectively) after processing.
   - `P4` and `P2` send an acknowledgment to `P2` and `P0` respectively after receiving acks from their children.
   - Finally, `P1` and `P2` send their acknowledgments to `P0`, completing the spanning tree.

---

### Analysis:

1. **Message Complexity**: 
   - In a system with `n` nodes and `m` edges, the total number of messages exchanged is **O(m)** because each edge is used at most twice (once to send a "FLOOD" message and once to receive an acknowledgment).

2. **Time Complexity**:
   - The time complexity is **O(d)**, where `d` is the diameter of the network (i.e., the longest shortest path between any two nodes). Each process waits for messages from its children before sending an acknowledgment, so the rounds depend on how deep the tree grows.

---

### Advantages and Limitations:
- **Advantages**:
   - Simple and easy to implement.
   - Works well in synchronous systems where timing is predictable.
   
- **Limitations**:
   - Assumes the system is fully synchronous.
   - Message overhead can be high in large networks with many edges (as each edge gets a "FLOOD" message).
   
This algorithm is a basic yet powerful approach for constructing a spanning tree, and it's useful for problems like **broadcasting** or **gathering information** in distributed systems.

