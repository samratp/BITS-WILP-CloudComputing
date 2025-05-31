### Defenses Against Attacks

---

### **Overview:**

Modern applications face a wide range of threats including code injection, denial-of-service (DoS), data exfiltration, and network-based attacks. In Secure Software Engineering, multiple layers of defense—known as **defense-in-depth**—are deployed to detect, prevent, and respond to these threats.

---

### **1. Runtime Application Security Protection (RASP)**

#### **Definition:**

RASP is a security technology that runs **inside the application**, monitoring and blocking attacks in **real-time** by analyzing app behavior and context.

#### **Key Features:**

* Works within the runtime environment (e.g., JVM, .NET)
* Detects and blocks SQL injection, XSS, command injection, etc.
* Application-aware (understands data flow and control flow)

#### **Advantages:**

* Low false positives (deep insight into the app logic)
* Stops zero-day attacks
* Complements traditional testing tools like SAST/DAST

---

### **2. Web Application Firewall (WAF)**

#### **Definition:**

A WAF filters, monitors, and blocks HTTP traffic to and from a web application.

#### **How it works:**

* Sits between users and the application
* Enforces rules against known attack patterns (e.g., OWASP Top 10)

#### **Common WAF Capabilities:**

* Detect and block SQL injection, XSS, CSRF
* Rate limiting, bot protection
* Virtual patching for known vulnerabilities

#### **Popular WAF Solutions:**

* AWS WAF, Cloudflare WAF, ModSecurity, F5, Imperva

---

### **3. Anti-DDoS Protection**

#### **Purpose:**

Mitigates **Distributed Denial of Service (DDoS)** attacks that aim to exhaust system resources or bandwidth.

#### **Techniques:**

* **Rate Limiting**: Restrict requests from IPs or locations
* **Traffic Scrubbing**: Route traffic through systems that filter out malicious packets
* **CDN-based protection**: Absorb traffic via globally distributed nodes (e.g., Cloudflare, Akamai)
* **Geo-blocking** and **CAPTCHA challenges**

#### **Cloud Providers Offerings:**

* AWS Shield, Azure DDoS Protection, Google Cloud Armor

---

### **4. Intrusion Detection/Prevention Systems (IDS/IPS)**

#### **Definition:**

* **IDS**: Monitors and alerts on suspicious activity (passive).
* **IPS**: Monitors and **actively blocks** malicious activity (active).

#### **Functionality:**

* Analyze traffic at the network or host level
* Match against known attack signatures or behaviors
* Detect anomalies, port scans, brute force, etc.

#### **Examples:**

* Snort, Suricata (open-source)
* Zeek (network visibility)
* Host-based IDS (HIDS) vs Network-based IDS (NIDS)

---

### **5. Firewalls**

#### **Definition:**

Firewalls control **incoming and outgoing network traffic** based on predetermined security rules.

#### **Types:**

* **Network Firewalls**: Control traffic between subnets or zones
* **Host-Based Firewalls**: Installed on individual servers
* **Next-Gen Firewalls (NGFW)**: Include DPI, IDS/IPS, and app-layer filtering

#### **Functions:**

* Block unauthorized ports
* Allow only whitelisted IPs or protocols
* Enforce segmentation and zoning policies

---

### **Defense-in-Depth Architecture:**

| Layer              | Defense Mechanism                           |
| ------------------ | ------------------------------------------- |
| Application Layer  | RASP, WAF                                   |
| Presentation Layer | Anti-DDoS, CDN                              |
| Network Layer      | IDS/IPS, Firewalls                          |
| Host Layer         | Host-based Firewalls, Secure Configurations |
| Data Layer         | Encryption, Access Control                  |

---

### **Conclusion:**

Effective defenses against attacks require **layered security controls** across the application, network, and infrastructure stack. In Secure Software Engineering, integrating tools like **RASP**, **WAF**, **IDS/IPS**, and **firewalls** ensures early detection, real-time protection, and resilience against a wide spectrum of cyber threats.
