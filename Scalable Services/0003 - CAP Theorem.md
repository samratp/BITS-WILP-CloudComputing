### **CAP Theorem (Consistency, Availability, Partition Tolerance)**  
The **CAP Theorem**, proposed by Eric Brewer, states that in a **distributed system**, you can only achieve **two out of the three** guarantees at any time:  

1. **Consistency (C):** Every read receives the latest write or an error.  
2. **Availability (A):** Every request receives a response (even if it's not the latest data).  
3. **Partition Tolerance (P):** The system continues to work despite network failures.  

---

### **Key Trade-offs**  
A distributed system **must** be partition-tolerant (P) because networks can fail. This means you must **choose between Consistency (C) and Availability (A):**  

1. **CP (Consistency + Partition Tolerance, but not Availability)**  
   - System prioritizes consistent data, even if some requests fail.  
   - Example: **Databases like MongoDB (in strong consistency mode)**  

2. **AP (Availability + Partition Tolerance, but not Consistency)**  
   - System always responds but may serve outdated data.  
   - Example: **DNS, Cassandra, DynamoDB**  

3. **CA (Consistency + Availability, but not Partition Tolerance)**  
   - Only possible in single-node databases (not truly distributed).  
   - Example: **Traditional relational databases like PostgreSQL (when running on one machine).**  

---

### **Real-World Example**  
Imagine a bank system:  
- **CP System:** Ensures your balance is correct, but during a network failure, some users may not be able to access their accounts.  
- **AP System:** Ensures users can always see their balance, but during failures, some transactions might not be immediately reflected.  

Most modern systems prefer **AP with eventual consistency**, balancing availability with consistency after a short delay.
