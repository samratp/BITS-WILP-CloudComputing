### What is a Dockerfile?

A **Dockerfile** is a plain text file that contains a list of instructions to **build a Docker image**. It automates the creation of Docker images by specifying the OS, dependencies, and commands needed to run your application.

---

### Common Dockerfile Instructions

| Instruction    | Description                                           |
| -------------- | ----------------------------------------------------- |
| `FROM`         | Sets the base image                                   |
| `RUN`          | Executes a command (e.g., install dependencies)       |
| `COPY` / `ADD` | Copies files from host to image                       |
| `WORKDIR`      | Sets the working directory inside the container       |
| `CMD`          | Sets the default command to run when container starts |
| `EXPOSE`       | Informs Docker that the container listens on a port   |
| `ENV`          | Sets environment variables                            |
| `ENTRYPOINT`   | Sets the executable that will always run              |

---

### Dockerfile Example 1: Python Web App (Flask)

```dockerfile
# Use official Python image from Docker Hub
FROM python:3.10-slim

# Set working directory inside the container
WORKDIR /app

# Copy current directory contents to /app in the container
COPY . .

# Install Python dependencies
RUN pip install --no-cache-dir -r requirements.txt

# Expose port 5000
EXPOSE 5000

# Run the app
CMD ["python", "app.py"]
```

Expected project structure:

```
/my-flask-app
├── app.py
├── requirements.txt
└── Dockerfile
```

---

### Dockerfile Example 2: Node.js App

```dockerfile
# Base image
FROM node:18

# Create app directory
WORKDIR /usr/src/app

# Copy package files first (for better caching)
COPY package*.json ./

# Install app dependencies
RUN npm install

# Copy the rest of the code
COPY . .

# App binds to port 3000
EXPOSE 3000

# Start the app
CMD ["npm", "start"]
```

---

### Dockerfile Example 3: Simple Static Site with Nginx

```dockerfile
FROM nginx:alpine

# Copy static HTML files to Nginx's default directory
COPY ./html /usr/share/nginx/html

EXPOSE 80
```

---

### Build and Run Commands

```bash
# Build the image
docker build -t my-image-name .

# Run a container
docker run -p 5000:5000 my-image-name
```
