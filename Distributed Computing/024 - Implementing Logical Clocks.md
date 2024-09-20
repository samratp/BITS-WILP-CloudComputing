To implement logical clocks in a distributed system, it’s important to establish the **data structures**, **rules for clock updates**, and how to manage **local** and **global clocks**. Here, we’ll primarily focus on **Lamport Logical Clocks** as a basic model, which are extended into **vector clocks** for more detailed causal tracking.

### 1. **Data Structures**

#### a. **Lamport Clocks**:
Each process in a distributed system keeps a **local logical clock**, which is an integer.

```python
class LamportClock:
    def __init__(self):
        self.local_clock = 0
```

- **Local Clock**: A simple integer counter, initialized to 0.
  
#### b. **Vector Clocks**:
Each process maintains a **vector of clocks** that tracks the logical clock of all processes in the system.

```python
class VectorClock:
    def __init__(self, process_id, num_processes):
        self.process_id = process_id
        self.local_clock_vector = [0] * num_processes
```

- **Vector Clock**: A list (or array) where each element represents the clock value for a process in the system.

### 2. **Rules for Updating Logical Clocks**

#### a. **Lamport Logical Clock Update Rules**

There are two main rules governing Lamport clocks:

1. **Event at a Local Process**: Each time a process performs an internal operation or sends a message, it increments its local clock by 1.
   - Local operation at process $\( P_i \): \( C_i = C_i + 1 \)$
   - Message send by $\( P_i \): \( C_i = C_i + 1 \)$
   
2. **Message Reception**: When process $\( P_i \)$ receives a message from process $\( P_j \)$ with timestamp $\( T_j \)$, it updates its clock as:
   - $\( C_i = \max(C_i, T_j) + 1 \)$

#### b. **Vector Clock Update Rules**

Vector clocks also follow two rules:

1. **Internal Event or Message Send**: Each process increments its own local entry in the vector clock.
   - Internal event at $\( P_i \): \( V_i[i] = V_i[i] + 1 \)$
   - Send message from $\( P_i \): \( V_i[i] = V_i[i] + 1 \), send entire vector \( V_i \).$

2. **Message Reception**: When receiving a message, a process updates its vector clock by comparing each element of its local vector with the received vector:
   - For each index $\( k \)$:  
     $\( V_i[k] = \max(V_i[k], V_{\text{received}}[k]) \)$
   - After updating, the process increments its own clock: $\( V_i[i] = V_i[i] + 1 \)$.

### 3. **Local and Global Logical Clocks**

#### a. **Local Logical Clock (Per Process)**
- **Lamport Clock**: For each process, the local clock is a simple integer counter that gets updated with every local event or message interaction.
  
  Example:
  ```python
  class LamportClock:
      def __init__(self):
          self.local_clock = 0

      def tick(self):
          self.local_clock += 1

      def send_message(self):
          self.tick()
          return self.local_clock

      def receive_message(self, message_time):
          self.local_clock = max(self.local_clock, message_time) + 1
  ```

- **Vector Clock**: The local clock is now a vector, and for each process, it only increments its own entry in the vector, while keeping track of all other processes’ clocks.

  Example:
  ```python
  class VectorClock:
      def __init__(self, process_id, num_processes):
          self.process_id = process_id
          self.vector = [0] * num_processes

      def tick(self):
          self.vector[self.process_id] += 1

      def send_message(self):
          self.tick()
          return self.vector.copy()

      def receive_message(self, received_vector):
          for i in range(len(self.vector)):
              self.vector[i] = max(self.vector[i], received_vector[i])
          self.tick()
  ```

#### b. **Global Logical Clock**
- **Lamport Clock**: There is no explicit global clock in the system. However, all the local clocks combined define a **partial order** of events across the system.
  - $\( A \rightarrow B \implies \text{Timestamp}(A) < \text{Timestamp}(B) \)$

- **Vector Clock**: The combination of vector clocks across processes provides a more detailed understanding of the global state, enabling identification of concurrent events.
  - If two vector clocks $\( V_i \)$ and $\( V_j \)$ are incomparable (i.e., neither $\( V_i \leq V_j \)$ nor $\( V_j \leq V_i \))$, the events are **concurrent**.

### 4. **Protocols with Two Rules**

#### a. **Lamport Clock Protocol with 2 Rules**
The protocol follows these two simple rules:

1. **Rule 1 (Internal Events)**: On every internal event or message send, a process increments its local logical clock by 1.
   - $\( C_i = C_i + 1 \)$

2. **Rule 2 (Message Reception)**: When a process receives a message, it updates its clock to the maximum of its own clock and the received timestamp, then increments by 1.
   - $\( C_i = \max(C_i, C_j) + 1 \)$

#### b. **Vector Clock Protocol with 2 Rules**
The protocol for vector clocks is slightly more complex but still adheres to two fundamental rules:

1. **Rule 1 (Internal Events and Message Send)**: On every internal event or message send, a process increments its own entry in the vector clock:
   - $\( V_i[i] = V_i[i] + 1 \)$

2. **Rule 2 (Message Reception)**: When a process receives a message, it updates its vector clock by taking the maximum of its own vector and the received vector, then increments its own entry.
   - $\( V_i[k] = \max(V_i[k], V_j[k]) \) for all \( k \)$
   - $\( V_i[i] = V_i[i] + 1 \)$

### 5. **Example with Vector Clocks**

Imagine there are three processes, P1, P2, and P3, each keeping track of their local events and the events of other processes.

```python
# Example with 3 processes
P1 = VectorClock(0, 3)
P2 = VectorClock(1, 3)
P3 = VectorClock(2, 3)

# Internal event in P1
P1.tick()  # P1's vector clock: [1, 0, 0]

# P1 sends a message to P2
msg_vector = P1.send_message()  # P1's vector clock: [2, 0, 0]

# P2 receives the message from P1
P2.receive_message(msg_vector)  # P2's vector clock: [2, 1, 0]

# Internal event in P3
P3.tick()  # P3's vector clock: [0, 0, 1]

# P2 sends a message to P3
msg_vector = P2.send_message()  # P2's vector clock: [2, 2, 0]

# P3 receives the message from P2
P3.receive_message(msg_vector)  # P3's vector clock: [2, 2, 2]
```

At each step:
- **Internal events**: Increment the process’s own clock.
- **Message exchanges**: Propagate the current state of the vector clocks across processes.

### Conclusion

Implementing logical clocks involves using simple data structures (integer clocks for Lamport, vectors for vector clocks) and following strict rules for updating these clocks during local events and message passing. Both **Lamport clocks** and **vector clocks** provide mechanisms to track causality in distributed systems, but vector clocks give more detail and can detect concurrency, making them suitable for complex distributed algorithms.
