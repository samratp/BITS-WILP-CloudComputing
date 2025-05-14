**Cloud Data Security - Notes**

---

**Definition:**
Cloud Data Security refers to the set of technologies, policies, and procedures used to protect data stored, processed, and transmitted through cloud computing platforms. It ensures confidentiality, integrity, and availability of data in the cloud.

---

**Key Principles of Cloud Data Security**

1. **Confidentiality**

   * Ensures that only authorized individuals and systems can access sensitive data.
   * Achieved through encryption, access controls, and identity management.

2. **Integrity**

   * Ensures that data is not altered or tampered with during storage or transmission.
   * Implemented using hashing, checksums, and digital signatures.

3. **Availability**

   * Ensures that data is accessible when needed, without delays or outages.
   * Supported through redundancy, load balancing, and disaster recovery systems.

---

**Common Techniques Used in Cloud Data Security**

1. **Encryption**

   * Data is converted into a coded format to prevent unauthorized access.
   * Types:

     * Encryption at Rest (e.g., AES-256)
     * Encryption in Transit (e.g., TLS/SSL)

2. **Access Control**

   * Restricts access based on user roles or policies.
   * Uses Role-Based Access Control (RBAC) and Attribute-Based Access Control (ABAC).

3. **Identity and Access Management (IAM)**

   * Verifies user identity and manages their permissions across cloud resources.

4. **Multi-Factor Authentication (MFA)**

   * Adds a second form of authentication to enhance login security.

5. **Data Loss Prevention (DLP)**

   * Prevents unauthorized sharing, leakage, or movement of sensitive data.

6. **Monitoring and Logging**

   * Tracks data access and changes to detect suspicious behavior.
   * Useful for audits, compliance, and real-time alerts.

7. **Backup and Disaster Recovery**

   * Ensures data can be restored in the event of corruption or loss.

---

**Cloud-Specific Risks**

1. **Data Breaches**

   * Unauthorized access to sensitive information due to weak security controls.

2. **Misconfiguration of Cloud Storage**

   * Incorrect settings can lead to public access of private data (e.g., open S3 buckets).

3. **Insider Threats**

   * Employees or contractors misusing their access to steal or damage data.

4. **Insecure APIs**

   * Poorly protected APIs can be exploited to access cloud services or data.

5. **Shared Technology Vulnerabilities**

   * Risks in multi-tenant environments where physical resources are shared.

---

**Best Practices**

1. Encrypt all sensitive data, both at rest and in transit.
2. Regularly audit IAM roles, permissions, and access policies.
3. Enable and enforce MFA for all user accounts.
4. Use cloud provider security services for threat detection and compliance.
5. Continuously monitor activity logs and set up alerts for anomalies.
6. Conduct regular vulnerability assessments and penetration testing.
7. Follow the principle of least privilege—grant only necessary access.
8. Keep systems and software up to date with security patches.
9. Implement automated backups and test recovery procedures periodically.
10. Train staff on cloud security policies and incident response plans.

---

**Cloud Provider Security Tools (Examples)**

* **AWS**: Key Management Service (KMS), IAM, CloudTrail, GuardDuty, S3 encryption
* **Azure**: Azure Key Vault, Azure Active Directory, Defender for Cloud, Azure Monitor
* **GCP**: Cloud Identity, Cloud Key Management, Cloud DLP, Security Command Center
