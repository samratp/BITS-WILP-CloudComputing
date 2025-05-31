### Supply Chain Attacks – Secure Software Engineering Notes

---

### **Definition:**

A **Supply Chain Attack** is a type of cyberattack where the attacker **targets a trusted third-party component** or **process** used in the software development or deployment pipeline. Instead of attacking the software directly, the attacker compromises the **supplier** to infiltrate the target system **indirectly**.

---

### **Why It's Critical in Software Security:**

Modern software relies heavily on **external libraries, tools, services, and infrastructure**. A single vulnerability or compromise in these dependencies can lead to **widespread breaches**, even in well-secured environments.

---

### **Common Vectors of Supply Chain Attacks:**

1. **Third-Party Software Libraries**

   * Inserting malicious code into open-source or vendor-provided libraries.
   * Example: A malicious NPM package injected to steal environment variables.

2. **Dependency Confusion**

   * Attacker publishes a package with the same name as an internal package in a public registry.
   * Example: Security researcher infiltrated major tech firms using this method.

3. **Typosquatting**

   * Uploading packages with names similar to popular ones to trick developers.
   * Example: `requet` instead of `request` in Python or JavaScript.

4. **Compromised Software Vendors**

   * Malicious update or backdoor inserted by a trusted vendor.
   * Example: **SolarWinds (2020)** — attackers inserted a backdoor in the Orion software update.

5. **Build Tool or CI/CD Pipeline Compromise**

   * Attackers modify build scripts or inject malicious code during software compilation.
   * Example: Codecov Bash Uploader compromise (2021).

6. **Infected Container Images**

   * Publishing or using container images that contain malware or backdoors.
   * Risk increases with pulling images from public registries (e.g., Docker Hub).

7. **Malicious Insider Contributions**

   * Authorized contributors intentionally inserting malicious code into OSS.
   * Example: `event-stream` NPM package incident.

8. **Hardware/Firmware Supply Chain Attacks**

   * Rare but impactful; involves planting vulnerabilities in hardware or firmware.
   * Example: Allegations against foreign-manufactured chips containing surveillance backdoors.

---

### **Notable Supply Chain Attack Examples:**

| **Attack**  | **Description**                                                       |
| ----------- | --------------------------------------------------------------------- |
| SolarWinds  | Orion update contained malware affecting 18,000+ customers            |
| Codecov     | Bash uploader script tampered, leaking secrets from CI pipelines      |
| UAParser.js | NPM package compromise led to data-stealing malware                   |
| NotPetya    | Malware spread via a compromised Ukrainian accounting software update |

---

### **Impact of Supply Chain Attacks:**

* **Massive scale** due to trust in upstream components
* **Delayed detection**, often discovered after months
* **Data exfiltration**, credential theft, backdoor access
* **Reputational damage** and financial loss

---

### **Defense Strategies:**

1. **Software Bill of Materials (SBOM)**

   * Maintain a full list of all dependencies (direct + transitive)

2. **Dependency Management**

   * Use dependency pinning
   * Vet and approve third-party packages

3. **Vulnerability Scanning**

   * Tools like Snyk, Trivy, OWASP Dependency-Check, etc.

4. **Package Integrity**

   * Verify signatures or checksums
   * Use Sigstore, GPG, or in-toto for artifact signing

5. **Secure CI/CD Pipelines**

   * Isolate build environments
   * Monitor and log all build steps

6. **Zero Trust Principles**

   * Treat every component as potentially untrusted until verified

7. **Continuous Monitoring**

   * Track new CVEs and emerging threats in your dependencies

---

### **Conclusion:**

Supply Chain Attacks are **indirect, stealthy, and highly impactful** threats in modern software systems. Secure Software Engineering must include rigorous controls over **external dependencies, build processes, and third-party integrations**. Managing the software supply chain is no longer optional—it's essential to building resilient, secure systems.
