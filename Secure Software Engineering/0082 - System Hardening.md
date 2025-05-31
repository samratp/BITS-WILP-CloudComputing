### System Hardening

---

### **Definition:**

**System hardening** is the process of **reducing the attack surface** of a system by eliminating unnecessary components, tightening configurations, and applying security best practices. It ensures the system is resilient to attacks and operates in a **least-privilege, minimal-trust** environment.

---

### **Goals of System Hardening:**

* Minimize vulnerabilities
* Enforce strong access control
* Limit exploitable entry points
* Ensure compliance with security standards (e.g., CIS Benchmarks, NIST)

---

### **Types of System Hardening:**

| Type                      | Description                                                               |
| ------------------------- | ------------------------------------------------------------------------- |
| **OS Hardening**          | Disabling unused services, removing default accounts, applying patches    |
| **Application Hardening** | Secure configuration of software (e.g., web servers, DBs)                 |
| **Network Hardening**     | Firewall rules, segmentation, disabling unused ports                      |
| **Database Hardening**    | Enforce encryption, disable unused features, limit query capabilities     |
| **Kernel Hardening**      | Use of secure sysctl settings, disabling module loading, SELinux/AppArmor |
| **Cloud Hardening**       | Configuring IAM, VPCs, storage access policies, audit logging             |

---

### **Common System Hardening Techniques:**

#### 1. **Disable Unnecessary Services**

* Stop and remove services that are not essential (e.g., FTP, Telnet, NFS).
* Prevents attackers from exploiting unused open ports.

#### 2. **Remove Unused Software and Packages**

* Fewer binaries = fewer potential vulnerabilities.

#### 3. **Apply Security Patches**

* Regularly update the OS and software to fix known vulnerabilities (CVEs).

#### 4. **Configure Strong Authentication**

* Enforce **multi-factor authentication (MFA)**
* Disable password-based SSH in favor of key-based login

#### 5. **Set File Permissions Strictly**

* Use **least privilege** principles for system files and executables.

#### 6. **Enable Firewalls**

* Configure `iptables`, `ufw`, or cloud-based firewalls to allow only necessary traffic.

#### 7. **Audit and Log Everything**

* Enable auditd, syslog, journald, or cloud audit logs.
* Monitor logs for abnormal activity.

#### 8. **Use Security Extensions**

* **SELinux**, **AppArmor**, or **Grsecurity** for mandatory access control.
* Harden runtime behavior of applications.

#### 9. **Secure Boot and BIOS**

* Enable secure boot, disable USB boot, set BIOS passwords.

#### 10. **Enforce Cryptographic Protocols**

* Disable weak protocols (e.g., SSL, TLS 1.0).
* Enforce strong ciphers and key lengths.

---

### **System Hardening Frameworks and Tools:**

| Tool/Framework                   | Purpose                                              |
| -------------------------------- | ---------------------------------------------------- |
| **CIS Benchmarks**               | Industry-standard hardening checklists               |
| **Lynis**                        | Audit and harden Linux systems                       |
| **OpenSCAP**                     | SCAP-based auditing and automation                   |
| **Ansible Roles**                | Automate system hardening via Infrastructure as Code |
| **Microsoft Security Baselines** | Hardening guides for Windows systems                 |

---

### **Example – Linux OS Hardening:**

* Remove unused packages: `yum remove telnet ftp`
* Disable root SSH login: `PermitRootLogin no`
* Enforce password complexity via PAM
* Configure UFW firewall: `ufw allow 22; ufw deny all`

---

### **System Hardening in the Secure SDLC:**

* Apply hardening in the **deployment phase**
* Integrate security baselines into **infrastructure automation**
* Periodically **reassess hardened systems** for drift

---

### **Conclusion:**

System hardening is a **foundational defense-in-depth practice** in Secure Software Engineering. By systematically reducing unnecessary functions and enforcing strict configurations, developers and system admins can **protect systems from compromise** and **limit the blast radius** of any potential breach.
