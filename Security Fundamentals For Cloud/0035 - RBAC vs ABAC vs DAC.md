### **RBAC vs. ABAC vs. DAC**  

| Feature               | **RBAC (Role-Based Access Control)** | **ABAC (Attribute-Based Access Control)** | **DAC (Discretionary Access Control)** |  
|----------------------|--------------------------------|--------------------------------|--------------------------------|  
| **Access Control Based On** | **Roles** (predefined permissions assigned to users) | **Attributes** (user, resource, environment conditions) | **Owner’s discretion** (creator of resource decides access) |  
| **Flexibility** | Medium (roles must be updated manually) | High (dynamic and context-aware) | High (users decide permissions) |  
| **Security** | Higher than DAC but static | Very High (fine-grained and context-aware) | Lower (users can misconfigure access) |  
| **Scalability** | Medium (manageable for enterprises) | High (suitable for large, complex systems) | Low (hard to manage in large systems) |  
| **Management Effort** | Medium (roles need to be assigned) | High (policies must be well-defined) | Low (owners manage access themselves) |  
| **Example Use Cases** | Corporate networks, databases, cloud IAM | Highly regulated industries (healthcare, finance) | Personal computers, small teams |  
| **Real-World Examples** | AWS IAM Roles, Windows Active Directory | Google Cloud IAM Conditions, Zero Trust Security | Windows File Permissions, Linux chmod |  

### **Key Takeaways**  
- **Use RBAC** if you need structured, predefined access control (e.g., employees in an organization).  
- **Use ABAC** if you need **dynamic, fine-grained** control based on multiple conditions.  
- **Use DAC** if you want **simple, user-controlled** access (best for personal use, not large enterprises).
