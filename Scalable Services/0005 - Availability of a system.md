### **Availability of a System**  

**Availability** refers to the ability of a system to remain operational and provide responses to user requests, even in the presence of failures.  

---

### **1. Definition**  
A system is **available** if it responds to requests **within an acceptable time**, regardless of failures.  

**Formula for Availability:**  
\[
\text{Availability} = \frac{\text{Uptime}}{\text{Uptime} + \text{Downtime}}
\]
Example: A system that runs **99.99% of the time** has **four nines availability (99.99%)**, meaning **only ~52 minutes of downtime per year**.  

---

### **2. High Availability (HA)**  
A system is **highly available** if it has **minimal downtime** and can quickly recover from failures.  
**Techniques to achieve HA:**  
- **Redundancy:** Duplicating components (e.g., multiple servers).  
- **Failover Mechanisms:** Switching to backup resources during failures.  
- **Load Balancing:** Distributing requests to prevent overload.  
- **Replication:** Copying data across multiple nodes to prevent data loss.  

🔹 **Example:**  
- **Google Search:** Always accessible due to multiple data centers handling traffic.  
- **Netflix:** Uses distributed servers to ensure uninterrupted streaming.  

---

### **3. Availability vs. Consistency (CAP Theorem)**  
- **If a system prioritizes availability (AP systems)**, it may return slightly outdated data instead of failing.  
- **If a system prioritizes consistency (CP systems)**, it may become unavailable when a network partition occurs.  

🔹 **Example:**  
- **DNS (Domain Name System) is AP** → Always available but may return outdated IP addresses.  
- **Banking system is CP** → Ensures correct balances but might be unavailable during failures.  

---

### **4. Measuring Availability**  

| Availability (%) | Downtime per Year | Example Systems |
|-----------------|------------------|----------------|
| **99% (Two 9s)**  | 3.65 days | Basic websites |
| **99.9% (Three 9s)** | 8.76 hours | Small SaaS applications |
| **99.99% (Four 9s)** | 52.6 minutes | Cloud services (AWS, Azure) |
| **99.999% (Five 9s)** | 5.26 minutes | Banking, telecom systems |

---

### **5. Trade-offs**  
- **Higher availability requires more redundancy** → Increases cost.  
- **Stronger consistency can reduce availability** → System may refuse requests during failures.  
- **Latency can be a trade-off** → Replicating data across multiple regions improves availability but increases response time.  

Systems like **cloud storage (Google Drive, Dropbox)** aim for high availability, ensuring users can access their files anytime.
