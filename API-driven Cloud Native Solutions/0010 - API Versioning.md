### **API Versioning**  

API versioning is the practice of managing changes and updates to an API without breaking existing clients. It allows developers to introduce new features, deprecate old ones, and make changes while ensuring backward compatibility.

---

## **1. Why API Versioning?**  
✅ **Backward Compatibility** – Existing clients continue working after updates.  
✅ **Flexibility** – Introduce breaking changes without disrupting users.  
✅ **Control** – Maintain multiple versions simultaneously.  

---

## **2. API Versioning Strategies**  

### **1. URI Versioning (Path Versioning)**  
The version is specified directly in the URL path.

**Example:**
```http
GET /api/v1/users
GET /api/v2/users
```

### **Advantages:**
- Simple and explicit.
- Easy to identify which version is being used.

### **Disadvantages:**
- Can result in version bloat with multiple versions.
- Requires updates to the API documentation and client code for each new version.

---

### **2. Query Parameter Versioning**  
The version is specified as a query parameter in the request URL.

**Example:**
```http
GET /api/users?version=1
GET /api/users?version=2
```

### **Advantages:**
- Less intrusive than URI versioning.
- More flexible and easy to change.

### **Disadvantages:**
- Can lead to confusion if the query parameter is not clearly documented.
- Makes the URL less clean and intuitive.

---

### **3. Header Versioning**  
The version is sent via an HTTP header.

**Example:**
```http
GET /api/users
X-API-Version: 1
```

### **Advantages:**
- Keeps the URL clean.
- Can easily handle complex versioning strategies (like multiple versions in parallel).
  
### **Disadvantages:**
- Requires clients to understand and include the header.
- Harder to debug and log (since the version is hidden in headers).

---

### **4. Content Negotiation (Accept Header Versioning)**  
Versioning is specified through the `Accept` header by defining a custom media type.

**Example:**
```http
GET /api/users
Accept: application/vnd.myapi.v1+json
```

### **Advantages:**
- Clean URL without versioning in the path.
- Very flexible, supports different formats for different versions.

### **Disadvantages:**
- Not all clients understand the `Accept` header (especially older ones).
- More complex than other methods.

---

### **5. Subdomain Versioning**  
Version is specified through different subdomains for different versions.

**Example:**
```http
GET https://v1.api.example.com/users
GET https://v2.api.example.com/users
```

### **Advantages:**
- Fully isolates versions at the network level.
- Can support different infrastructure for different versions.

### **Disadvantages:**
- More difficult to manage subdomains.
- May involve more setup and routing complexity.

---

## **3. Best Practices for API Versioning**  

1️⃣ **Avoid Breaking Changes**: If possible, **don't** break existing functionality between versions. Add new features rather than modifying existing ones.

2️⃣ **Document Versions Clearly**: Provide comprehensive **documentation** for each version and highlight **deprecated** features.

3️⃣ **Deprecation Strategy**: For deprecated versions, provide clients with a timeline for **end-of-life** and inform them of upcoming changes.

4️⃣ **Minimal Versioning**: Try to **version only when necessary**. Small, non-breaking changes should not trigger new versions.

5️⃣ **Semantic Versioning**: If you choose a versioning approach, consider using **semantic versioning** (`major.minor.patch`) to indicate the type of changes:
   - **Major**: Backward-incompatible changes.
   - **Minor**: Backward-compatible new features.
   - **Patch**: Backward-compatible bug fixes.

---

## **4. Versioning Use Case Examples**  

### **Example 1: URI Versioning**  
```http
GET /api/v1/products
GET /api/v2/products
```
- The `v1` and `v2` represent major version changes, likely with backward-incompatible changes between them.

### **Example 2: Header Versioning**  
```http
GET /api/users
X-API-Version: 2
```
- No changes to the URL. Only the header determines the API version.

### **Example 3: Query Parameter Versioning**  
```http
GET /api/users?version=1
GET /api/users?version=2
```
- Clients can easily switch between versions by modifying the query parameter.

---

## **5. When to Version an API?**  
Versioning is essential when:
- **You introduce breaking changes** (e.g., deleting or renaming fields).
- **You add new features** without breaking existing features.
- **You have long-term support** for multiple versions of an API.

For example:
- **Breaking change**: Changing the structure of the response (e.g., removing a field).
- **Non-breaking change**: Adding new fields or options without affecting existing behavior.

---

## **6. Tools for API Versioning**  
- **Swagger/OpenAPI**: Define API versions in your API specifications.  
- **Postman**: Manage different versions and test them easily.  
- **API Gateways**: Handle versioning, authentication, and traffic routing for multiple API versions (e.g., Kong, NGINX, AWS API Gateway).

---

### **Final Thoughts**  
API versioning ensures flexibility and backward compatibility as your application evolves. Choose a versioning strategy based on the complexity of your application, user needs, and client interaction.
