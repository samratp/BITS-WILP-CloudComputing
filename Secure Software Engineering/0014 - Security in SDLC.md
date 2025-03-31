Security in the **Software Development Life Cycle (SDLC)** ensures that security is integrated into every phase of software development, reducing vulnerabilities and preventing cyber threats. This approach is called **Secure SDLC (SSDLC)**.

## 🔹 **Phases of Secure SDLC & Security Practices**  

### 1️⃣ **Planning & Requirement Analysis**
   - Identify security requirements (e.g., regulatory compliance, data protection).
   - Perform threat modeling to anticipate risks.
   - Define security policies and standards.

### 2️⃣ **Design**
   - Use **Secure Architecture Design** principles (e.g., least privilege, defense in depth).
   - Apply threat modeling again to detect attack surfaces.
   - Choose secure authentication and encryption mechanisms.

### 3️⃣ **Implementation (Coding)**
   - Follow **Secure Coding Practices** (e.g., OWASP guidelines).
   - Use **Static Application Security Testing (SAST)** tools to scan code for vulnerabilities.
   - Avoid hardcoding secrets (e.g., API keys, passwords).

### 4️⃣ **Testing**
   - Perform **Dynamic Application Security Testing (DAST)** to check runtime vulnerabilities.
   - Conduct penetration testing (ethical hacking).
   - Use **Software Composition Analysis (SCA)** to find vulnerabilities in third-party libraries.

### 5️⃣ **Deployment**
   - Implement **DevSecOps** to integrate security into CI/CD pipelines.
   - Use container security tools (if using Docker/Kubernetes).
   - Secure cloud infrastructure and apply proper access controls.

### 6️⃣ **Maintenance & Monitoring**
   - Continuously monitor applications for security threats.
   - Patch vulnerabilities and update dependencies.
   - Conduct regular security audits.

## 🔹 **Key Concepts**
- **Shift Left Security**: Implement security early in SDLC to reduce cost and effort.
- **Zero Trust**: Never trust, always verify—enforce strict access controls.
- **Secure Software Supply Chain**: Verify the integrity of third-party libraries and dependencies.
