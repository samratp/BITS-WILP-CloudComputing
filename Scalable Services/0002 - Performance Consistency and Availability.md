### **Performance, Consistency, and Availability**  

These are key aspects of distributed systems and databases.  

---

### **1. Performance**  
**Definition:** How fast a system responds to requests and processes data.  
**Factors affecting performance:**  
- **Latency:** Time taken for a request to be processed.  
- **Throughput:** Number of requests processed per second.  
- **Resource Utilization:** CPU, memory, disk, and network usage.  

**Example:** A website should load in milliseconds, not seconds, for a good user experience.  

---

### **2. Consistency**  
**Definition:** Ensuring all copies of data in a distributed system are the same.  
- **Strong Consistency:** Every read gets the latest write.  
- **Eventual Consistency:** Reads may be outdated for some time but will become consistent eventually.  
- **CAP Theorem Trade-off:** A system can choose between strong consistency and availability in case of a network partition.  

**Example:**  
- **Strong Consistency:** A bank transaction must reflect the same balance across all servers instantly.  
- **Eventual Consistency:** Social media posts may appear at different times on different devices but eventually sync.  

---

### **3. Availability**  
**Definition:** The system remains operational and accessible despite failures.  
- **High Availability (HA):** Ensuring minimal downtime with redundancy and failover strategies.  
- **Trade-off with Consistency:** More availability can mean weaker consistency (as per CAP theorem).  

**Example:**  
- A cloud storage service (like Google Drive) should always be accessible, even if some servers fail.  

---

### **Balancing the Three**  
- A system optimized for **performance** might sacrifice **consistency** for speed.  
- A system ensuring **strong consistency** may reduce **availability** during failures.  
- Highly **available** systems might relax consistency to stay operational.  

Distributed systems must carefully balance these factors based on use cases.
