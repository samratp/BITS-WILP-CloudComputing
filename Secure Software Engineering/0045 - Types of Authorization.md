### **Types of Authorization: RBAC, ABAC, and CBAC**  

Authorization is the process of controlling access to resources based on policies. The three main types of authorization models are **RBAC (Role-Based Access Control), ABAC (Attribute-Based Access Control), and CBAC (Context-Based Access Control)**.  

---

## **1. Role-Based Access Control (RBAC)**  

🔹 **Definition:** Access is granted based on **user roles** within an organization.  
🔹 **Example:** A **Manager** can approve leave requests, but an **Employee** cannot.  

### **RBAC Structure**  
- **Users** → Individuals (e.g., Alice, Bob).  
- **Roles** → Groups of users with similar permissions (e.g., Admin, HR, Developer).  
- **Permissions** → Allowed actions for each role (e.g., "View Reports," "Edit Payroll").  

### **RBAC Example Table**  

| **Role**   | **Permissions** |
|------------|----------------|
| **Admin**  | Read, Write, Delete |
| **HR**     | Read, Edit Employee Records |
| **Employee** | Read Only |

🔹 **Use Case:** Enterprise applications (e.g., **ERP systems, corporate email, database management**).  

🔹 **Pros:**  
✅ Simple to implement.  
✅ Easy to manage for large teams.  

🔹 **Cons:**  
❌ Not flexible—users are bound by fixed roles.  
❌ Difficult to scale with dynamic access needs.  

---

## **2. Attribute-Based Access Control (ABAC)**  

🔹 **Definition:** Access is granted based on **user attributes** (e.g., role, department, location, device).  
🔹 **Example:** A **doctor** can access patient records **only in their hospital branch**.  

### **ABAC Rules & Policies**  
ABAC policies are written as **rules combining multiple attributes**:  

**Example Policy:**  
```plaintext
IF user.role = "Doctor" AND user.location = "Hospital_A"
THEN allow access to "Patient Records"
```

### **ABAC Attribute Types**  

| **Attribute Type** | **Example** |
|-------------------|-------------|
| **User Attributes** | Role (Doctor), Department (HR), Clearance (Top Secret) |
| **Resource Attributes** | Data Type (Medical Record), File Sensitivity (Confidential) |
| **Environment Attributes** | Location (USA), Device Type (Company Laptop) |

🔹 **Use Case:** **Cloud security, healthcare, banking, and military applications.**  

🔹 **Pros:**  
✅ More flexible than RBAC.  
✅ Fine-grained access control based on real-time data.  

🔹 **Cons:**  
❌ Complex to configure and maintain.  
❌ Requires **advanced policy management tools**.  

---

## **3. Context-Based Access Control (CBAC)**  

🔹 **Definition:** Access is granted based on the **context of a request**, such as location, time, device, or behavior.  
🔹 **Example:** A user can log in **only from a company-issued laptop** and **during work hours**.  

### **CBAC Rules & Conditions**  
CBAC policies evaluate **real-time conditions**:  

**Example Policy:**  
```plaintext
IF user.device = "Company Laptop" AND user.time = "9 AM - 5 PM"
THEN allow login
```

### **CBAC Context Types**  

| **Context Type** | **Example** |
|-----------------|-------------|
| **Time-Based** | Allow access only between 9 AM - 5 PM |
| **Location-Based** | Deny access from outside the corporate network |
| **Device-Based** | Allow login only from managed devices |
| **Behavior-Based** | Block access if login behavior is suspicious |

🔹 **Use Case:** **Zero Trust security, financial transactions, adaptive authentication.**  

🔹 **Pros:**  
✅ **Dynamic access control** that adapts to real-time security conditions.  
✅ Enhances **security against insider threats and phishing attacks**.  

🔹 **Cons:**  
❌ Can be **resource-intensive** to monitor real-time contexts.  
❌ Requires integration with **identity and threat detection tools**.  

---

## **Comparison Table: RBAC vs. ABAC vs. CBAC**  

| **Feature**        | **RBAC** | **ABAC** | **CBAC** |
|--------------------|---------|---------|---------|
| **Access Based On** | Roles | Attributes (User, Resource, Environment) | Context (Time, Device, Behavior) |
| **Flexibility** | Low | High | Very High |
| **Best For** | Enterprise applications | Cloud security, healthcare | Zero Trust, adaptive authentication |
| **Example** | Admin can edit payroll | Managers in the US can access reports | Employees can log in only from company laptops |
| **Security Level** | Basic | Advanced | Very Advanced |

---

## **Conclusion**  

✅ **RBAC** is simple but lacks flexibility.  
✅ **ABAC** is more dynamic and scalable.  
✅ **CBAC** is **best for Zero Trust security** and real-time threat prevention.  

🔹 **Which one to choose?**  
- Use **RBAC** for **basic role-based access control** in traditional enterprise apps.  
- Use **ABAC** when **fine-grained access control** is needed.  
- Use **CBAC** for **adaptive security** in **high-risk environments**.
