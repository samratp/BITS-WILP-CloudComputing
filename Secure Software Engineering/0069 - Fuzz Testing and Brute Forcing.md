### Fuzz Testing and Brute Forcing – Secure Software Engineering Notes

---

### **1. Fuzz Testing (Fuzzing)**

**Definition:**
Fuzz Testing is a **black-box testing technique** that automatically feeds a program with malformed, unexpected, or random data to find **input-handling vulnerabilities**.

---

#### **Objectives**

* Detect crashes, hangs, assertion failures
* Identify memory corruption, buffer overflows, and input validation flaws
* Stress-test parsers and input routines

---

#### **How It Works**

1. Identify target input (e.g., file, API, form field)
2. Generate a large volume of invalid/random/mutated input data
3. Feed the inputs into the application automatically
4. Monitor the application's behavior (e.g., crashes, exceptions, memory leaks)

---

#### **Types of Fuzzers**

* **Mutation-based**: Modify valid inputs (e.g., flip bits, inject symbols)
* **Generation-based**: Build inputs based on a specification or format (e.g., XML, JSON)
* **Coverage-guided**: Use feedback from code coverage to guide input generation (e.g., AFL, libFuzzer)

---

#### **Common Vulnerabilities Detected**

* Buffer overflows
* Null pointer dereferencing
* Integer overflows
* Format string bugs
* File parsing vulnerabilities

---

#### **Tools**

* AFL (American Fuzzy Lop)
* libFuzzer
* Peach Fuzzer
* Burp Suite (fuzzing module)
* zzuf

---

#### **Advantages**

* Automated and scalable
* Can discover unknown/zero-day vulnerabilities
* Effective against complex file formats and protocol parsers

#### **Limitations**

* May miss logic flaws or auth issues
* Needs instrumentation or monitoring setup
* Can generate a high volume of noise (false negatives possible)

---

### **2. Brute Forcing**

**Definition:**
Brute Forcing is an attack/testing method that systematically tries **all possible combinations** of inputs (e.g., passwords, tokens, session IDs) to **guess a valid value**.

---

#### **Objectives**

* Test the strength of authentication mechanisms
* Check for poor password policies
* Identify predictable tokens or insecure direct object references (IDOR)

---

#### **Types**

* **Password brute force**: Try every combination to guess a password
* **Dictionary attack**: Try common or leaked passwords from a list
* **Credential stuffing**: Use known leaked credentials across different services
* **Parameter brute force**: Guess IDs, tokens, URLs (e.g., `/user?id=123`)

---

#### **Tools**

* Hydra
* Burp Suite Intruder
* Medusa
* THC-Hydra
* OWASP ZAP (brute force module)

---

#### **Indicators of Vulnerability**

* No rate limiting or lockout mechanism
* Predictable tokens or IDs
* Informative error messages (e.g., "user not found", "incorrect password")

---

#### **Advantages**

* Simple and effective for weak security setups
* Useful for assessing password policy enforcement
* Often uncovers misconfigured or forgotten endpoints

#### **Limitations**

* Time-consuming without optimization (e.g., slow networks or large keyspaces)
* Easily detected and blocked by security controls (e.g., WAFs, CAPTCHAs)
* Ethical/legal concerns if done on unauthorized systems

---

### **Conclusion**

* **Fuzz Testing** is best for detecting **input-handling and memory-related vulnerabilities**.
* **Brute Forcing** focuses on testing **authentication strength** and **predictability** of sensitive parameters.
* Both are essential tools in the secure software engineering lifecycle, especially for identifying vulnerabilities not covered by static or dynamic code analysis.
