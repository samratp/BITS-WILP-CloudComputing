### Static Application Security Testing (SAST) – Secure Software Engineering Notes

**Definition:**
Static Application Security Testing (SAST) is a white-box testing method that analyzes an application's source code, bytecode, or binary for security vulnerabilities **without executing the program**.

---

### Key Characteristics

* Performed early in the Software Development Life Cycle (SDLC)
* Analyzes code statically (at rest), typically during development or build stages
* Can be integrated into IDEs or CI/CD pipelines
* Requires access to the application's source code

---

### Objectives

* Detect security flaws such as:

  * Input validation errors
  * SQL injection
  * Cross-site scripting (XSS)
  * Hardcoded credentials
  * Insecure cryptographic practices
* Enforce secure coding standards
* Provide feedback to developers early to reduce remediation costs

---

### Process

1. **Set Up the SAST Tool**

   * Configure to scan selected files or repositories
   * Define rules or coding standards

2. **Code Analysis**

   * Tool parses the source code to build a model (e.g., Abstract Syntax Tree)
   * Applies static analysis techniques to identify issues

3. **Result Generation**

   * Tool outputs a list of detected vulnerabilities
   * Includes severity ratings and remediation suggestions

4. **Remediation and Review**

   * Developers fix reported issues
   * Re-run the scan to confirm resolution

---

### Common Vulnerabilities Detected by SAST

* Buffer overflows
* Injection flaws (SQL, command)
* Cross-site scripting (XSS)
* Insecure file handling (e.g., path traversal)
* Missing or improper input validation
* Insecure use of cryptographic functions
* Hardcoded secrets

---

### Advantages

* Early detection of vulnerabilities
* No need to run the application
* Can be automated and integrated into development workflows
* Supports compliance (e.g., OWASP Top 10, PCI-DSS)

---

### Limitations

* False positives are common
* Does not detect runtime or environment-specific issues
* Requires access to complete source code
* May not understand custom frameworks or libraries

---

### Examples of SAST Tools

* **Open-source**:

  * SonarQube
  * Bandit (Python)
  * PMD (Java)
  * Brakeman (Ruby on Rails)

* **Commercial**:

  * Fortify Static Code Analyzer
  * Checkmarx
  * Veracode SAST
  * AppScan Source

---

### Best Practices

* Integrate SAST into CI/CD pipeline for automated scans
* Use with manual code review for better coverage
* Customize rules for the application’s tech stack
* Prioritize and triage findings to reduce noise

---

### Conclusion

SAST is a foundational technique in secure software engineering for proactively identifying vulnerabilities early in the development process. It should be combined with manual reviews and dynamic testing (e.g., DAST) for comprehensive security coverage.
