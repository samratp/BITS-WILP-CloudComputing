**Docker**

**Introduction**
Docker is a platform for developing, shipping, and running applications inside lightweight, portable containers. Containers package an application and its dependencies, ensuring consistent environments across development, testing, and production.

---

**Dockerfile**
A Dockerfile is a text file containing instructions to build a Docker image.

**Example Dockerfile:**

```
# Use an official Node.js runtime as a base image
FROM node:16-alpine

# Set working directory inside container
WORKDIR /app

# Copy package files and install dependencies
COPY package.json package-lock.json ./
RUN npm install --production

# Copy the rest of the application code
COPY . .

# Expose application port
EXPOSE 3000

# Start the application
CMD ["node", "server.js"]
```

---

**Docker Best Practices**

* Use official base images and minimal images (e.g., alpine) to reduce size.
* Minimize the number of layers by combining commands with `&&`.
* Cache dependencies separately to speed up builds (copy package files before application code).
* Avoid storing secrets in Dockerfiles or images.
* Use `.dockerignore` to exclude unnecessary files.
* Tag images clearly with version numbers and metadata.
* Regularly scan images for vulnerabilities.
* Keep containers stateless; store persistent data outside containers using volumes.

---

**Docker Compose**
Docker Compose is a tool to define and run multi-container Docker applications using a YAML file.

**Example `docker-compose.yml`:**

```yaml
version: "3.8"
services:
  web:
    build: .
    ports:
      - "8080:3000"
    environment:
      - NODE_ENV=production
    volumes:
      - .:/app
  redis:
    image: "redis:alpine"
```

* Defines multiple services (`web`, `redis`) in one file.
* Supports networking between containers automatically.
* Simplifies running and managing multi-service applications locally or in development environments.

Docker and Docker Compose streamline building, packaging, and deploying scalable applications consistently across environments.
