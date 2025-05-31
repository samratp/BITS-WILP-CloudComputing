### Dynamic Application Security Testing (DAST) – Secure Software Engineering Notes

**Definition:**
Dynamic Application Security Testing (DAST) is a **black-box testing technique** that analyzes a running application by simulating external attacks to find vulnerabilities in real-time, without access to source code.

---

### Key Characteristics

* Conducted at runtime (tests the deployed application)
* Mimics the behavior of real attackers
* Language-agnostic (tests via HTTP, SOAP, REST, etc.)
* Detects runtime and environment-specific issues

---

### Objectives

* Identify vulnerabilities exposed during execution such as:

  * SQL Injection
  * Cross-site Scripting (XSS)
  * Cross-Site Request Forgery (CSRF)
  * Security misconfigurations
  * Authentication & session flaws
* Test real-world interaction patterns
* Simulate attacks on live environments (e.g., staging or QA)

---

### Process

1. **Crawl/Spidering Phase**

   * Tool maps the application's pages, endpoints, parameters

2. **Attack/Scan Phase**

   * Tool sends crafted payloads to input fields, headers, cookies
   * Monitors responses for signs of vulnerability

3. **Vulnerability Detection**

   * Compares responses to expected patterns (e.g., error messages, code execution, DOM manipulation)

4. **Reporting & Remediation**

   * Generates detailed report with severity levels and fix recommendations

---

### Types of Vulnerabilities Detected

* Injection attacks (SQL, command, LDAP)
* XSS (reflected, stored, DOM-based)
* Insecure HTTP headers
* Misconfigured security settings (e.g., directory listing)
* Server-side request forgery (SSRF)
* Broken authentication/session management

---

### Advantages

* No need for source code
* Simulates real attacker behavior
* Identifies vulnerabilities missed by SAST
* Can scan applications built in any language

---

### Limitations

* Cannot detect code-level issues (e.g., logic bugs, dead code)
* May miss vulnerabilities hidden behind authentication
* Limited in analyzing client-side code (e.g., JS-heavy SPAs)
* Possible false negatives if dynamic paths are not triggered

---

### Common DAST Tools

* **Open-source**: OWASP ZAP, Wapiti
* **Commercial**: Burp Suite Pro, Acunetix, IBM AppScan, Rapid7 InsightAppSec, Netsparker

---

### DAST vs SAST – Comparison Table

| Feature               | SAST                           | DAST                            |
| --------------------- | ------------------------------ | ------------------------------- |
| Access to Source Code | Required                       | Not required                    |
| Testing Phase         | Early in SDLC (pre-deployment) | Later (post-deployment/testing) |
| Vulnerability Types   | Code-level issues              | Runtime/environment issues      |
| False Positives       | High                           | Moderate                        |
| Language Dependency   | Yes                            | No (protocol-based)             |

---

### Best Practices

* Run DAST on staging or test environments (never on production)
* Combine with SAST for full coverage
* Include authentication steps for deeper scans
* Regularly update scanner rules to detect new attack types

---

### Conclusion

DAST is essential in secure software engineering to validate the application's security **in its real execution environment**. It complements SAST and manual reviews by simulating attacks and uncovering vulnerabilities that only appear during runtime.
