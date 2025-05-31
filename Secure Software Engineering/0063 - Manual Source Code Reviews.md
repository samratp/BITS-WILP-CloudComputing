**Manual Source Code Reviews** are a critical practice in secure software development. They involve systematically inspecting code by humans to identify bugs, security vulnerabilities, logic errors, and deviations from coding standards that automated tools may miss.

---

**Objectives of Manual Source Code Reviews**

* Identify security vulnerabilities (e.g., injection flaws, broken access controls)
* Detect logic flaws or insecure coding patterns
* Ensure compliance with secure coding standards and guidelines
* Improve code quality and maintainability
* Encourage knowledge sharing and team learning

---

**Key Areas to Focus On**

**1. Input Validation and Output Encoding**
Check for proper validation of user inputs and proper encoding before output.

**2. Authentication and Authorization**
Verify that authentication mechanisms are correctly implemented and access controls are consistently enforced.

**3. Error Handling and Logging**
Ensure errors do not reveal sensitive information and logs do not contain personal data or secrets.

**4. Sensitive Data Protection**
Look for proper handling of passwords, tokens, API keys, and PII. Verify use of encryption where needed.

**5. Secure Use of APIs and Libraries**
Review third-party API usage for proper input/output handling and secure defaults.

**6. Business Logic and Workflow**
Ensure the logic aligns with expected security requirements (e.g., preventing privilege escalation or replay attacks).

**7. Session Management**
Check session lifecycle (creation, expiration, invalidation) and secure cookie settings.

**8. Code Comments and Documentation**
Verify that sensitive data handling is documented and that comments do not leak information.

---

**Review Techniques**

* **Checklist-Based Review**: Use predefined secure coding checklists (e.g., OWASP, CERT).
* **Walkthroughs**: Developers present code logic to peers for collaborative review.
* **Pair Programming**: Continuous peer review through joint development.
* **Adversarial Review**: Think like an attacker; look for abuse scenarios and bypasses.

---

**Best Practices**

* Review small code segments regularly rather than large dumps infrequently.
* Use version control diffs to focus reviews on recent changes.
* Document findings and track resolutions.
* Combine with automated tools (linters, static analysis) for better coverage.
* Involve developers, testers, and security engineers in the review process.

---

**Common Review Tools**

* GitHub/GitLab/Mercurial pull request systems
* Gerrit (code review tool)
* CodeScene (code health analytics)
* IDE-integrated code linters and reviewers

---

**Limitations**

* Time-consuming and resource-intensive
* Prone to human error or oversight if not done systematically
* Requires reviewers with adequate security knowledge

Despite these limitations, manual reviews remain one of the most effective ways to uncover subtle and business logic-related security flaws.
