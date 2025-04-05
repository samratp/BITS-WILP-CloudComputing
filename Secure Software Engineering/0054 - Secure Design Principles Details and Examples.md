Here’s a detailed look at the **Secure Design Principles** with **clear definitions and examples** for each:

---

### 1. 🔐 **Least Privilege**
**Definition:** Give users or systems the **minimum level of access** necessary to perform their tasks.

**Example:** A web server process should only be able to read HTML files, not write to the file system or access the database directly.

---

### 2. 👥 **Separation of Duties**
**Definition:** Divide tasks among different roles to **reduce fraud or error** by ensuring no one person has full control.

**Example:** A developer can write code, but only a separate deployment engineer can push it to production.

---

### 3. 🧱 **Defense in Depth**
**Definition:** Use **multiple layers of security controls** so a failure in one does not compromise the system.

**Example:** A secure application uses input validation, access control, encryption, firewalls, and intrusion detection together.

---

### 4. ⚠️ **Fail-Safe Defaults**
**Definition:** Systems should **default to denying access** unless it’s explicitly allowed.

**Example:** A system that blocks access to a file unless the user has been given read permission, rather than assuming access is allowed.

---

### 5. ⚙️ **Economy of Mechanism**
**Definition:** **Keep designs as simple as possible** to reduce the chance of errors or vulnerabilities.

**Example:** Use a well-tested authentication library rather than a complex custom login system.

---

### 6. 🔍 **Complete Mediation**
**Definition:** **Check every access request** to a resource rather than caching or assuming prior access still applies.

**Example:** A user’s permissions are checked every time they try to access a file—not just at login.

---

### 7. 🛠️ **Open Design**
**Definition:** Security should not depend on **secrecy of design**, only on **secrecy of keys or credentials**.

**Example:** Encryption algorithms like AES are publicly known and studied, yet remain secure due to strong key protection.

---

### 8. 🔄 **Least Common Mechanism**
**Definition:** Minimize shared resources to reduce the risk of unintended information leakage or interference.

**Example:** Use separate memory spaces or containers for applications rather than having them share the same process memory.

---

### 9. 🧠 **Psychological Acceptability**
**Definition:** Security mechanisms should be **easy for users to understand and use correctly**.

**Example:** Using biometric logins on mobile devices—secure and user-friendly—rather than complex passwords.

---

### 10. 🔗 **Weakest Link**
**Definition:** The overall security is only as strong as its **weakest component**.

**Example:** A highly secure website using HTTPS can still be compromised if the admin uses a weak password.

---

### 11. 🧩 **Leveraging Existing Components**
**Definition:** Use **trusted, proven components or libraries** instead of building new ones from scratch.

**Example:** Using industry-standard libraries like OpenSSL for encryption instead of writing your own.

---

> 🧠 These principles guide architects and developers in building systems that are **robust, secure, and user-friendly** from the ground up.
