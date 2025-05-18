**Docker** is an open-source platform used to **build, ship, and run containers**. It simplifies application development and deployment by packaging everything the application needs into one portable unit — a **Docker container**.

---

### What Docker Does

* **Build** apps using simple configuration files (`Dockerfile`)
* **Package** them with all dependencies into an image
* **Run** them as containers on any machine with Docker installed

---

### Core Components of Docker

| Component         | Description                                             |
| ----------------- | ------------------------------------------------------- |
| **Dockerfile**    | A script with instructions to build a container image   |
| **Image**         | A snapshot of the app and its environment               |
| **Container**     | A running instance of an image                          |
| **Docker Engine** | The core service that builds and runs containers        |
| **Docker Hub**    | A public registry where images can be stored and shared |

---

### Example Workflow

#### Step 1: Create a Dockerfile

```Dockerfile
# Use a Python base image
FROM python:3.10

# Copy your app code
COPY app.py .

# Install dependencies
RUN pip install flask

# Define the command to run the app
CMD ["python", "app.py"]
```

#### Step 2: Build the Docker Image

```bash
docker build -t my-flask-app .
```

#### Step 3: Run the Container

```bash
docker run -p 5000:5000 my-flask-app
```

---

### Why Use Docker?

* **Consistency** – Works the same in dev, test, and prod
* **Isolation** – Keeps apps separate from each other
* **Portability** – Run on any OS or cloud
* **Efficiency** – Lightweight and fast
* **Version Control** – Images can be tagged and rolled back

---

### Docker in the Real World

* **Developers** use it to share apps without “it works on my machine” problems
* **DevOps teams** use it in **CI/CD pipelines** for testing and deployment
* **ML Engineers** use it to package models with dependencies
* **LLM and LangChain apps** use Docker for reproducibility across environments
