### **📌 AWS Shared Responsibility Model**  

The **AWS Shared Responsibility Model** defines **who is responsible** for security between **AWS (Amazon Web Services)** and its **customers**.  

🔹 **AWS is responsible for the security "OF" the cloud** – securing the infrastructure, networking, and physical environment.  
🔹 **Customers are responsible for security "IN" the cloud** – securing data, applications, and access management.  

---

## **1️⃣ AWS Responsibilities (Security "OF" the Cloud)**  
AWS secures the underlying cloud infrastructure, including:  

🔒 **Physical Security**  
✅ Protecting data centers, servers, and hardware  
✅ Controlling access with biometrics, CCTV, and guards  

🔒 **Network Security**  
✅ Firewalls, DDoS protection, and network isolation  
✅ AWS Shield, AWS WAF (Web Application Firewall)  

🔒 **Hypervisor & Virtualization Security**  
✅ Isolating virtual machines (EC2 instances)  
✅ Protecting containerized workloads (EKS, ECS, Fargate)  

🔒 **Compliance & Certifications**  
✅ SOC 2, ISO 27001, GDPR, HIPAA, PCI-DSS compliance  

🔒 **Service Availability & Maintenance**  
✅ Ensuring high availability (AWS Global Infrastructure)  
✅ Automatic patching and security updates for managed services  

---

## **2️⃣ Customer Responsibilities (Security "IN" the Cloud)**  
Customers must secure their own **data, applications, and access** in AWS:  

🔒 **Data Protection & Encryption**  
✅ Encrypt data using **AWS KMS (Key Management Service)**  
✅ Enable **S3 bucket encryption and access control**  

🔒 **Identity & Access Management (IAM)**  
✅ Use **IAM roles, policies, and least privilege access**  
✅ Enable **Multi-Factor Authentication (MFA)**  

🔒 **Application Security**  
✅ Patch vulnerabilities in applications and OS  
✅ Use AWS services like **AWS Inspector** for security scanning  

🔒 **Network Security & Firewalls**  
✅ Configure **Security Groups, NACLs (Network ACLs), and VPC Peering**  
✅ Use **AWS WAF (Web Application Firewall)** for protection  

🔒 **Logging & Monitoring**  
✅ Enable **AWS CloudTrail** and **Amazon GuardDuty** for threat detection  
✅ Monitor with **AWS Security Hub**  

---

## **3️⃣ AWS Shared Responsibility Model by Service Type**  

| **Responsibility**          | **IaaS (EC2, S3, RDS, VPC)** | **PaaS (AWS Lambda, DynamoDB, RDS Managed)** | **SaaS (AWS S3, Glue, Redshift, Route 53)** |
|----------------------------|-----------------------------|--------------------------------|------------------------------|
| **Data Security**          | Customer                    | Customer                     | Customer                     |
| **Application Security**   | Customer                    | Customer                     | Provider                     |
| **OS Security & Updates**  | Customer                    | Provider                      | Provider                      |
| **Network Security**       | Shared                      | Provider                      | Provider                      |
| **IAM & Access Controls**  | Customer                    | Customer                     | Customer                     |
| **Physical Security**      | Provider                    | Provider                      | Provider                      |

---

## **4️⃣ Why is the AWS Shared Responsibility Model Important?**  
✅ **Prevents Misconfigurations** – Clarifies who secures what  
✅ **Enhances Cloud Security** – Reduces vulnerabilities and breaches  
✅ **Ensures Compliance** – Helps meet GDPR, HIPAA, PCI-DSS requirements  
✅ **Optimizes Cost & Performance** – AWS handles infrastructure, customers focus on workloads  

---

## **📌 Conclusion**  
The **AWS Shared Responsibility Model** ensures **AWS secures the cloud infrastructure**, while **customers secure their own data, applications, and access controls**. Understanding this model is **critical** to properly securing cloud workloads. 🚀
