### **CIA Triad: Confidentiality, Integrity, and Availability**  

The **CIA Triad** is a fundamental security model that ensures information security. It consists of three core principles:  

---

## **1. Confidentiality** 🔒  
Confidentiality ensures that sensitive data is accessible only to authorized users. It protects against **unauthorized access, data leaks, and breaches**.  

### **Key Threats**  
- Unauthorized access (hacking, insider threats)  
- Data leaks (accidental or intentional)  
- Shoulder surfing (looking at screens or documents)  

### **Security Measures**  
✔ **Encryption** – Encrypt data in transit (TLS) and at rest (AES-256).  
✔ **Access Control** – Implement Role-Based Access Control (RBAC).  
✔ **Multi-Factor Authentication (MFA)** – Require more than one authentication method.  
✔ **Data Masking** – Hide sensitive data when displaying information (e.g., credit card numbers).  

---

## **2. Integrity** 🛡️  
Integrity ensures that data remains **accurate, complete, and unaltered**. It protects against **unauthorized modification, corruption, or tampering**.  

### **Key Threats**  
- Data corruption (due to malware, system errors, or cyberattacks)  
- Unauthorized modifications (e.g., SQL injection, man-in-the-middle attacks)  
- Human errors (accidental data deletion or changes)  

### **Security Measures**  
✔ **Checksums & Hashing** – Use cryptographic hash functions (SHA-256) to detect unauthorized changes.  
✔ **Digital Signatures** – Verify the authenticity of files and messages.  
✔ **Version Control** – Maintain backup copies and use version tracking for critical data.  
✔ **Access Logging & Monitoring** – Track changes and unauthorized modifications.  

---

## **3. Availability** ⚡  
Availability ensures that systems and data are **accessible when needed**, preventing downtime or disruptions.  

### **Key Threats**  
- Distributed Denial-of-Service (DDoS) attacks  
- Hardware failures (server crashes, disk failures)  
- Power outages and natural disasters  
- Ransomware attacks  

### **Security Measures**  
✔ **Redundancy & Backups** – Use failover servers and regular data backups.  
✔ **Load Balancing** – Distribute traffic to prevent server overload.  
✔ **Disaster Recovery Plans** – Have contingency plans for system failures.  
✔ **DDoS Protection** – Use firewalls, rate-limiting, and CDNs to mitigate attacks.  

---

### **Balancing the CIA Triad**  
- **Trade-offs exist** (e.g., encrypting data enhances confidentiality but may reduce availability due to processing overhead).  
- **Security policies should align with business needs** while maintaining an optimal balance between confidentiality, integrity, and availability.  

The **CIA Triad** is the foundation of cybersecurity, ensuring that data remains protected, trustworthy, and accessible.
