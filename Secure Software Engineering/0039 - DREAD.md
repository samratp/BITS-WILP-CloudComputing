### **DREAD Threat Model**  

**DREAD** is a risk assessment framework used in threat modeling to prioritize security threats based on their potential impact. It helps security teams **quantify risks** and decide which threats need immediate attention.  

---

## **DREAD Scoring Criteria**  

| **Category**        | **Description**                                          | **Example Attack** |
|---------------------|----------------------------------------------------------|--------------------|
| **D**amage         | How severe is the impact?                               | Ransomware encrypting critical files |
| **R**eproducibility | How easily can the attack be repeated?                  | SQL Injection attack with a simple input |
| **E**xploitability | How simple is the attack to execute?                     | Phishing email with a malicious link |
| **A**ffected Users | How many users will be impacted?                         | Data breach exposing millions of records |
| **D**iscoverability | How easy is it to find the vulnerability?               | Publicly known software exploit |

---

## **DREAD Scoring System**  

Each category is **scored from 0 to 10**, with **higher scores** indicating **greater risk**. The total DREAD score is calculated as:  

\[
\text{DREAD Score} = (D + R + E + A + D) / 5
\]

- **High-risk threats** (Score: **>7**) → Immediate mitigation needed  
- **Medium-risk threats** (Score: **4-7**) → Fix in next update  
- **Low-risk threats** (Score: **<4**) → Monitor but lower priority  

---

## **Example: DREAD Scoring for SQL Injection**  

| **Category**       | **Score** | **Reason** |
|--------------------|----------|------------|
| **Damage**        | **8** | Can expose or delete critical database records |
| **Reproducibility** | **9** | Can be repeated with automated scripts |
| **Exploitability** | **9** | Easy to execute with simple payloads |
| **Affected Users** | **7** | Many users' data could be exposed |
| **Discoverability** | **8** | Publicly known vulnerabilities exist |

**DREAD Score:**  
\[
(8 + 9 + 9 + 7 + 8) / 5 = 8.2 \quad (\text{High Risk})
\]  
✅ **Mitigation:** Use **parameterized queries**, input validation, and **Web Application Firewalls (WAFs)**.

---

## **DREAD vs STRIDE**  

| **Aspect** | **DREAD** | **STRIDE** |
|------------|----------|------------|
| **Purpose** | Risk assessment & prioritization | Threat classification |
| **Focus** | Impact and exploitability | Type of security threat |
| **Used For** | Prioritizing security fixes | Identifying security weaknesses |
| **Scoring?** | Yes (numerical risk score) | No |

---

## **Best Practices for Using DREAD**  

✅ Use **DREAD + STRIDE** together for **comprehensive threat modeling**.  
✅ Automate risk assessment with **threat modeling tools**.  
✅ Regularly **update scores** as new threats emerge.  
✅ Consider **business impact** along with technical risks.  

DREAD helps **prioritize security threats** so organizations can **focus on the most critical vulnerabilities first**.
