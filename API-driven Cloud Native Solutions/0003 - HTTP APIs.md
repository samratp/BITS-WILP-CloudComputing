### **HTTP APIs**  
HTTP APIs use the **Hypertext Transfer Protocol (HTTP)** to allow communication between clients (e.g., browsers, mobile apps) and servers. They follow a request-response model, where the client sends an HTTP request, and the server responds with data.

---

## **1. HTTP Methods (CRUD Operations)**
HTTP APIs typically use the following methods:

| HTTP Method | Operation  | Example Use Case |
|------------|-----------|-----------------|
| **GET**    | Read      | Fetch user details |
| **POST**   | Create    | Register a new user |
| **PUT**    | Update    | Edit user details |
| **DELETE** | Delete    | Remove a user account |

---

## **2. HTTP Status Codes**
Servers respond with **status codes** to indicate success or failure:

| Code  | Meaning                  | Example Scenario |
|------|--------------------------|----------------|
| **200** | OK                        | Successful GET request |
| **201** | Created                   | Successful POST request |
| **400** | Bad Request               | Invalid input from client |
| **401** | Unauthorized               | Missing or wrong credentials |
| **403** | Forbidden                  | No permission to access resource |
| **404** | Not Found                  | Requested resource does not exist |
| **500** | Internal Server Error      | Server-side issue |

---

## **3. RESTful APIs vs. Other HTTP APIs**
### **REST API (Representational State Transfer)**
- Uses **stateless** requests (each request is independent).
- Works with **JSON** or **XML** data formats.
- Follows a structured **URL path** for resources.

🔹 **Example REST API Request (GET request to fetch user data):**  
```http
GET /users/123 HTTP/1.1
Host: api.example.com
Authorization: Bearer <token>
```
🔹 **Response:**  
```json
{
    "id": 123,
    "name": "John Doe",
    "email": "johndoe@example.com"
}
```

### **GraphQL API (Alternative to REST)**
- Clients specify the exact data they need, reducing over-fetching.
- Uses a **single endpoint** (`/graphql`) for all operations.
  
🔹 **GraphQL Query Example:**  
```graphql
query {
  user(id: 123) {
    name
    email
  }
}
```
🔹 **Response:**  
```json
{
  "data": {
    "user": {
      "name": "John Doe",
      "email": "johndoe@example.com"
    }
  }
}
```

---

## **4. Authentication in HTTP APIs**
### **Common Authentication Methods:**
1. **API Key** – A secret key sent in the request header.  
2. **OAuth 2.0** – Secure authorization using tokens.  
3. **JWT (JSON Web Token)** – A signed token verifying user identity.  

🔹 **Example API Key Authentication:**  
```http
GET /users/123 HTTP/1.1
Host: api.example.com
x-api-key: YOUR_API_KEY
```

🔹 **Example OAuth 2.0 Bearer Token Authentication:**  
```http
GET /profile HTTP/1.1
Authorization: Bearer YOUR_ACCESS_TOKEN
```

---

## **5. Example: HTTP API in Python**
### **Making a GET request using `requests`**
```python
import requests

url = "https://api.example.com/users/123"
headers = {"Authorization": "Bearer YOUR_ACCESS_TOKEN"}

response = requests.get(url, headers=headers)
print(response.json())  # Output: User details
```
