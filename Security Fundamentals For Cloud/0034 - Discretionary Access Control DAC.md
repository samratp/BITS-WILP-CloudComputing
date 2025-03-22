### **Discretionary Access Control (DAC)**  

DAC is an access control model where the **owner of a resource** has the discretion to grant or revoke permissions for other users. It is **flexible but less secure** compared to models like Role-Based Access Control (RBAC) and Attribute-Based Access Control (ABAC).  

---

### **Key Characteristics of DAC**  
1. **Owner-Controlled Access** – The creator (owner) of a resource decides who can access it.  
2. **Discretionary Policy** – Access permissions are not enforced by system-wide rules but by user-defined policies.  
3. **Identity-Based Access** – Permissions are assigned to users or groups explicitly.  
4. **Inheritance of Permissions** – If a user has access to a resource, they may share access with others (if allowed).  

---

### **How DAC Works**  
- When a user **creates a file or resource**, they automatically become the **owner**.  
- The owner can assign **read, write, execute, or delete** permissions to other users.  
- The system enforces these permissions but does not restrict the owner from modifying them at any time.  

---

### **DAC Example**  

| **User**  | **File**  | **Permissions**  |  
|-----------|----------|-----------------|  
| Alice (Owner) | report.doc | Read, Write, Execute |  
| Bob  | report.doc | Read Only |  
| Charlie | report.doc | No Access |  

- **Alice**, as the owner, can grant or revoke access for **Bob** and **Charlie** at any time.  
- If **Bob** is allowed, he might share the file with **Charlie** (if the system permits delegation).  

---

### **DAC vs. Other Access Control Models**  

| **Feature** | **DAC** | **RBAC** | **ABAC** |  
|------------|--------|--------|--------|  
| **Control** | User-defined | Role-based | Attribute-based |  
| **Flexibility** | High | Medium | High |  
| **Security** | Lower (can be misconfigured) | Higher (roles restrict access) | Very High (context-aware policies) |  
| **Scalability** | Low (difficult to manage large users) | Medium | High |  

---

### **Advantages of DAC**  
✅ **Easy to Implement** – Simple permission model.  
✅ **Flexible** – Users can control their own data access.  
✅ **Common in Operating Systems** – Used in Windows, Linux, and macOS file permissions.  

### **Disadvantages of DAC**  
❌ **Less Secure** – Users can accidentally grant access to unauthorized people.  
❌ **Not Scalable** – Difficult to manage in large organizations.  
❌ **Vulnerable to Malware** – A user with access can run malicious programs.  

---

### **Best Practices for DAC**  
1. **Use Least Privilege Principle** – Grant only necessary permissions.  
2. **Regularly Audit Permissions** – Prevent excessive access.  
3. **Combine with MFA** – Adds extra security.  
4. **Use Role-Based Access Control (RBAC) for Critical Systems** – Avoid misconfigurations in sensitive environments.  

DAC is **easy to implement** but **less secure for large-scale environments**, making it ideal for personal and small-scale systems but risky for high-security applications.
