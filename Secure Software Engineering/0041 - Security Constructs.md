### **Security Constructs**  

Security constructs are fundamental building blocks used to design secure systems. They help protect data, systems, and networks from cyber threats by implementing **security controls** and **best practices** across different domains.  

---

## **Key Security Constructs**  

### **1. Authentication** (Who are you?)  
Ensures only legitimate users or systems can access resources.  
🔹 **Examples:**  
- Multi-Factor Authentication (MFA)  
- Passwordless Authentication (e.g., biometrics, FIDO2)  
- OAuth, OpenID Connect  

### **2. Authorization** (What can you do?)  
Controls **user permissions** and access rights.  
🔹 **Examples:**  
- Role-Based Access Control (RBAC)  
- Attribute-Based Access Control (ABAC)  
- Least Privilege Principle  

### **3. Confidentiality** (Protecting sensitive data)  
Ensures data is **accessible only to authorized parties**.  
🔹 **Examples:**  
- **Encryption** (AES, RSA, TLS)  
- **Data Masking**  
- **Secure Key Management**  

### **4. Integrity** (Ensuring data is not altered)  
Prevents unauthorized **modification, deletion, or corruption** of data.  
🔹 **Examples:**  
- **Cryptographic Hashing (SHA-256, HMAC)**  
- **Digital Signatures**  
- **Checksums & Integrity Verification**  

### **5. Availability** (Ensuring uptime and reliability)  
Ensures systems are **accessible when needed**, even during attacks.  
🔹 **Examples:**  
- **Load Balancing & Redundancy**  
- **DDoS Mitigation (Cloudflare, AWS Shield)**  
- **Disaster Recovery & Backup Plans**  

### **6. Non-Repudiation** (Proving actions were taken)  
Prevents users from **denying** their actions.  
🔹 **Examples:**  
- **Digital Signatures & Certificates**  
- **Audit Logs & Secure Logging**  

### **7. Secure Coding Practices**  
Prevents **common vulnerabilities** in software development.  
🔹 **Examples:**  
- **Input Validation (to prevent SQL Injection, XSS)**  
- **Secure API Design (OAuth2, JWT)**  
- **Memory Safety (Bounds Checking, ASLR)**  

### **8. Threat Detection & Response**  
Identifies and mitigates attacks in real time.  
🔹 **Examples:**  
- **SIEM (Security Information and Event Management)**  
- **Intrusion Detection Systems (IDS)**  
- **Security Incident Response Plans**  

### **9. Network Security**  
Protects communication channels from threats.  
🔹 **Examples:**  
- **Firewalls (NGFW, WAF)**  
- **Zero Trust Architecture**  
- **VPN & Network Segmentation**  

### **10. Security Governance & Compliance**  
Ensures security policies align with regulations.  
🔹 **Examples:**  
- **ISO 27001, NIST, CIS Benchmarks**  
- **GDPR, HIPAA Compliance**  
- **Security Awareness Training**  

---

## **How Security Constructs Work Together**  
Example: **Securing an Online Banking App**  
✅ **Authentication** → Users log in via **MFA**.  
✅ **Authorization** → Admins & users have different permissions (**RBAC**).  
✅ **Confidentiality** → Data is encrypted via **TLS** & **AES**.  
✅ **Integrity** → Digital signatures verify transactions.  
✅ **Availability** → Load balancers prevent **DDoS** outages.  
✅ **Non-repudiation** → Logs track **transaction approvals**.  
✅ **Threat Detection** → SIEM alerts on unusual login attempts.  

A **secure system** integrates multiple security constructs to **prevent, detect, and respond** to cyber threats effectively.
