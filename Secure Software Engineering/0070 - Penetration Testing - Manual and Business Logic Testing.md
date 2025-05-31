### **1. Penetration Testing – Overview**

**Definition:**
Penetration Testing (Pen Testing) is a **simulated attack** on a software system to identify exploitable vulnerabilities. It is conducted from an **attacker’s perspective** to assess security controls in a **realistic environment**.

---

### **Types of Penetration Testing**

* **Automated**: Using tools (e.g., scanners) to identify known issues
* **Manual**: Human-led analysis and exploitation, especially for complex or logic-based flaws
* **Black-box**: No internal knowledge (like an external attacker)
* **White-box**: Full knowledge of the system
* **Gray-box**: Partial knowledge (common in internal testing)

---

### **2. Manual Penetration Testing**

**Definition:**
Manual Pen Testing involves human experts evaluating the application **without relying solely on automated tools**. It focuses on **complex vulnerabilities** that require human reasoning.

#### **Objectives**

* Identify issues not detectable by scanners (e.g., logic flaws, privilege escalation)
* Understand application behavior from a creative attacker’s mindset
* Bypass security controls through unconventional inputs or flows

#### **Common Manual Techniques**

* Custom payload crafting (e.g., hand-built SQL or XSS payloads)
* Manual tampering using tools like Burp Suite Repeater
* Testing session management, access controls, encryption misuse
* Bypassing client-side validations or business logic

#### **Advantages**

* Detects deep, complex issues
* Can exploit multi-step flaws or misimplementations
* Adapts to dynamic and custom application behavior

#### **Limitations**

* Time-consuming and resource-intensive
* Requires skilled testers
* Not suitable for full automation or frequent testing

---

### **3. Business Logic Testing**

**Definition:**
Business Logic Testing is a **subtype of manual testing** that identifies vulnerabilities stemming from **flaws in the application’s design or workflows**, rather than coding mistakes or misconfigurations.

#### **Focus Areas**

* Misuse of legitimate features
* Circumventing business rules (e.g., price manipulation, bypassing approval)
* Unauthorized actions (e.g., changing user roles via modified requests)
* Abuse of API endpoints in ways that violate intended workflows

#### **Examples**

* Booking a flight with a negative price
* Transferring money without required authorization
* Purchasing items with altered discounts or taxes via modified parameters
* Replaying old requests to perform repeated operations (e.g., coupon re-use)

#### **Why It's Hard to Automate**

* No clear “signatures” of a flaw—depends on context and business logic
* Often involves multi-step workflows or user role transitions
* Requires understanding of **how the app is supposed to behave**

---

### **Penetration Testing Process**

1. **Reconnaissance**

   * Gather information about targets, endpoints, users

2. **Scanning**

   * Identify live hosts, services, and application interfaces

3. **Exploitation**

   * Attempt to exploit vulnerabilities (manual or tool-assisted)

4. **Privilege Escalation**

   * Try to gain deeper access (e.g., admin rights)

5. **Post-exploitation**

   * Assess impact (e.g., data exposure, unauthorized actions)

6. **Reporting**

   * Provide proof-of-concept, risk analysis, and remediation guidance

---

### **Tools for Manual and Logic Testing**

* Burp Suite (Intruder, Repeater, Sequencer)
* OWASP ZAP
* Postman (for API logic testing)
* Fiddler, Tamper Data
* Manual script writing (e.g., Python or Bash)

---

### **Conclusion**

* **Manual Penetration Testing** is essential for catching high-impact flaws that automated tools miss.
* **Business Logic Testing** focuses on **how** a system behaves rather than **what** it runs, making it a crucial component of secure software engineering.
* Both techniques enhance application security by identifying **contextual, workflow-specific, and human logic-dependent vulnerabilities**.
