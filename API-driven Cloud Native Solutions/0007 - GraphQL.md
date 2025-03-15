### **GraphQL: A Query Language for APIs**  

**GraphQL** is an API query language developed by **Facebook (Meta)** that allows clients to request exactly the data they need. Unlike **REST**, which returns fixed responses, **GraphQL** lets clients **fetch, update, and delete** data using flexible queries.

---

## **1. Why Use GraphQL?**  
✅ **Flexible Queries** – Fetch only required fields, reducing over-fetching.  
✅ **Single Endpoint** – No need for multiple REST endpoints.  
✅ **Strongly Typed Schema** – Defines API structure in a **schema**.  
✅ **Batch Requests** – Retrieve multiple resources in one query.  
✅ **Better for Frontend** – Avoids unnecessary API calls.  

---

## **2. GraphQL vs REST**  

| Feature          | GraphQL | REST |
|-----------------|---------|------|
| **Endpoints**   | Single (`/graphql`) | Multiple (`/users`, `/orders`) |
| **Data Fetching** | Client selects fields | Fixed response |
| **Over-fetching** | No | Yes |
| **Under-fetching** | No | Yes |
| **Versioning** | Not needed | `/v1`, `/v2` versions |
| **Performance** | Can be optimized | Can be inefficient |

---

## **3. GraphQL API Structure**  

A **GraphQL API** consists of:  
🔹 **Schema** – Defines data types & queries.  
🔹 **Queries** – Read (GET-like).  
🔹 **Mutations** – Create, update, delete (POST/PUT/DELETE).  
🔹 **Resolvers** – Backend logic to process queries.  

---

## **4. Example: GraphQL Query vs REST API**  

🔹 **REST API Request (GET)**
```http
GET /users/123
```
🔹 **REST API Response (JSON)**
```json
{
  "id": 123,
  "name": "John Doe",
  "email": "john@example.com",
  "posts": [
    {"id": 1, "title": "GraphQL Intro"},
    {"id": 2, "title": "REST vs GraphQL"}
  ]
}
```
🔹 **GraphQL Query (Fetch Only Name & Posts)**
```graphql
query {
  user(id: 123) {
    name
    posts {
      title
    }
  }
}
```
🔹 **GraphQL Response (Optimized)**
```json
{
  "data": {
    "user": {
      "name": "John Doe",
      "posts": [
        {"title": "GraphQL Intro"},
        {"title": "REST vs GraphQL"}
      ]
    }
  }
}
```
**✅ GraphQL avoids fetching unnecessary fields (`id`, `email`).**  

---

## **5. GraphQL Schema Example**  

### **Define a Schema (TypeScript, Node.js, Apollo Server)**  
```graphql
type User {
  id: ID!
  name: String!
  email: String!
  posts: [Post]
}

type Post {
  id: ID!
  title: String!
  content: String!
}

type Query {
  user(id: ID!): User
  posts: [Post]
}

type Mutation {
  createUser(name: String!, email: String!): User
}
```
📌 **Key GraphQL Types:**  
- `ID!` – Non-nullable unique identifier.  
- `String!` – Non-nullable string.  
- `[Post]` – Array of `Post` objects.  

---

## **6. Running a GraphQL API (Node.js + Apollo Server)**  

🔹 **Install Dependencies**  
```sh
npm install @apollo/server graphql express
```
🔹 **Setup Server (`server.js`)**
```javascript
const { ApolloServer, gql } = require("@apollo/server");
const { startStandaloneServer } = require("@apollo/server/standalone");

const typeDefs = gql`
  type User {
    id: ID!
    name: String!
  }

  type Query {
    user(id: ID!): User
  }
`;

const resolvers = {
  Query: {
    user: (_, { id }) => ({ id, name: "John Doe" }),
  },
};

const server = new ApolloServer({ typeDefs, resolvers });
startStandaloneServer(server, { listen: { port: 4000 } }).then(() => {
  console.log("🚀 Server running at http://localhost:4000");
});
```
🔹 **Run Server**  
```sh
node server.js
```
🔹 **Test in GraphQL Playground** (`http://localhost:4000`)  
```graphql
query {
  user(id: "1") {
    name
  }
}
```

---

## **7. GraphQL Mutations (Create/Update/Delete Data)**  

🔹 **Mutation Example (Create User)**
```graphql
mutation {
  createUser(name: "Alice", email: "alice@example.com") {
    id
    name
  }
}
```
🔹 **Mutation Response**
```json
{
  "data": {
    "createUser": {
      "id": "2",
      "name": "Alice"
    }
  }
}
```

---

## **8. GraphQL Best Practices**  
✅ **Use Pagination** – Avoid large queries (`first: 10, after: "cursor"`).  
✅ **Rate Limiting** – Prevent abuse (e.g., use API Gateway).  
✅ **Cache Responses** – Use **Dataloader** or **Redis**.  
✅ **Error Handling** – Return structured errors.  

🔹 **Example Error Response**  
```json
{
  "errors": [
    {
      "message": "User not found",
      "locations": [{ "line": 2, "column": 3 }],
      "path": ["user"]
    }
  ]
}
```

---

### **Final Thoughts**  
GraphQL is **powerful, flexible, and efficient**, especially for frontend-heavy applications like **React, Vue, Angular, and mobile apps**.
