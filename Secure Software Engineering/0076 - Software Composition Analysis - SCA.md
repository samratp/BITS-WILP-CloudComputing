### Software Composition Analysis (SCA)

---

### **Definition:**

**Software Composition Analysis (SCA)** is the process of **identifying and managing open-source components** in software applications. It helps detect **known vulnerabilities**, **license risks**, and **version issues** in third-party libraries used during development.

---

### **Why It Matters in Security:**

Most modern applications contain **60–90% open-source code**. Vulnerabilities in these components can:

* Introduce critical security flaws
* Violate legal compliance (e.g., GPL, LGPL)
* Be exploited through supply chain attacks

SCA tools provide **visibility**, **risk detection**, and **automated management** of these components.

---

### **Core Functions of SCA Tools:**

| Function                     | Description                                                         |
| ---------------------------- | ------------------------------------------------------------------- |
| **Dependency Discovery**     | Identifies all open-source libraries and their versions             |
| **Vulnerability Detection**  | Scans components against databases like **CVE**, **NVD**, OSS Index |
| **License Compliance Check** | Flags risky or incompatible licenses                                |
| **Component Health Check**   | Analyzes project activity, popularity, and maintenance status       |
| **Policy Enforcement**       | Blocks unsafe or unapproved packages based on predefined rules      |
| **Remediation Suggestions**  | Recommends secure, compatible package upgrades                      |

---

### **Common SCA Tools:**

* **OWASP Dependency-Check**
* **OWASP Dependency-Track**
* **Snyk**
* **Black Duck (Synopsys)**
* **WhiteSource (Mend)**
* **FOSSA**
* **Trivy** (for containers and SBOM)

---

### **Key Features in SCA:**

#### 1. **Vulnerability Database Integration**

* Links identified libraries to known CVEs
* Provides severity scores (CVSS), patches, and exploitability info

#### 2. **License Risk Management**

* Detects use of restrictive or conflicting open-source licenses
* Supports legal compliance efforts

#### 3. **SBOM Generation**

* Generates a **Software Bill of Materials (SBOM)** for documentation and audits

#### 4. **Automated CI/CD Integration**

* SCA runs in pipelines to prevent risky code from being merged or deployed

#### 5. **Transitive Dependency Scanning**

* Identifies vulnerabilities in **indirect (nested)** dependencies

---

### **SCA vs SAST:**

| Feature        | SCA                                | SAST                                   |
| -------------- | ---------------------------------- | -------------------------------------- |
| Focus          | Open-source components             | Custom source code                     |
| Detects        | Known CVEs, license issues         | Logic flaws, insecure coding practices |
| Input          | Dependency files (e.g., `pom.xml`) | Source code                            |
| Execution Time | Fast (metadata-driven)             | Slower (code parsing and analysis)     |

---

### **Best Practices:**

* **Pin dependency versions** to prevent unintentional upgrades
* Use **allowlists** and **deny lists** for package approval
* Continuously scan during development, not just pre-release
* Monitor **new vulnerabilities** in old dependencies
* Educate developers on choosing and updating secure libraries

---

### **Example Use Case:**

A web app uses `log4j` version 2.13. SCA flags this as vulnerable to **Log4Shell (CVE-2021-44228)** with a CVSS score of 10.0. The tool recommends upgrading to version 2.17.1 and alerts the team during the CI build.

---

### **Conclusion:**

Software Composition Analysis is a vital part of **secure software development**, providing automated insight into **open-source risks**. For Secure Software Engineering, SCA ensures that **external code dependencies** are as trustworthy and secure as the in-house code, reducing the likelihood of hidden vulnerabilities and compliance issues.
