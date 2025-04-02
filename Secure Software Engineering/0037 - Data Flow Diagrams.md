### **Data Flow Diagrams (DFDs)**  

A **Data Flow Diagram (DFD)** is a visual representation of how data moves within a system. It helps in understanding the system’s data processes, inputs, outputs, storage, and interactions.  

---

## **Why Use DFDs?**  
✅ Helps identify potential security risks and vulnerabilities.  
✅ Provides a clear overview of data movement in a system.  
✅ Useful in **threat modeling** (e.g., STRIDE analysis).  
✅ Enhances communication between developers, security teams, and stakeholders.  

---

## **DFD Components**  

1. **External Entities (Sources/Sinks)**  
   - Represent users, systems, or devices interacting with the system.  
   - **Symbol:** Squares.  
   - **Example:** A **customer** entering data into a website.  

2. **Processes (Transformations)**  
   - Represent actions performed on the data.  
   - **Symbol:** Circles or ovals.  
   - **Example:** A **login authentication system** validating credentials.  

3. **Data Stores**  
   - Represent storage locations where data is held.  
   - **Symbol:** Open rectangles or parallel lines.  
   - **Example:** A **user database storing login details.**  

4. **Data Flows**  
   - Represent the movement of data between entities, processes, or storage.  
   - **Symbol:** Arrows.  
   - **Example:** **User credentials** sent from a login form to a database.  

---

## **DFD Levels**  

### **1. Level 0 (Context Diagram)**  
- A high-level view of the system showing external entities and data flow.  
- **Example:** A simple representation of an **online banking system** where users interact with the bank server.  

### **2. Level 1 DFD**  
- Breaks down the system into major **processes** and data flows.  
- Shows how input data is processed and stored.  

### **3. Level 2+ (Detailed DFDs)**  
- Further breaks down complex processes from Level 1.  
- Shows internal workflows and subprocesses.  

---

## **Example: DFD for User Authentication System**  

```
         +------------+          (1) User submits login credentials
         |  User      |  --->  [Authenticate User] --->  | User Database |
         +------------+                                  |  (Verify Password)  |
```

🔹 **Process:** Authenticate User  
🔹 **Data Store:** User Database  
🔹 **Data Flow:** Login credentials → Authentication → Verified user response  

---

## **DFDs in Security and Threat Modeling**  

🔍 **Identify weak points** – Where sensitive data is stored and transmitted.  
🔍 **Apply STRIDE threats** – Find risks like **spoofing**, **tampering**, or **data leakage**.  
🔍 **Ensure encryption** – Secure **data flows** to prevent exposure.  

By integrating DFDs with **threat modeling**, organizations can **design secure systems** and **reduce attack surfaces** effectively.
