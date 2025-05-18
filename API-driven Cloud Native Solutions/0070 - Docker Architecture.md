### Docker Architecture Overview

Docker follows a **client-server** architecture, where the client communicates with the Docker daemon to build, run, and manage containers.

---

### Key Components

#### 1. **Docker Client**

* The command-line tool (`docker`) used by users.
* Sends commands like `docker run`, `docker build`, etc. to the **Docker Daemon**.
* Communicates with the daemon using REST APIs.

#### 2. **Docker Daemon (`dockerd`)**

* Core engine that does the heavy lifting: builds, runs, and manages containers and images.
* Listens for API requests and manages Docker objects (containers, images, networks, volumes).

#### 3. **Docker Images**

* Read-only templates used to create containers.
* Built from a `Dockerfile`.
* Stored in image registries like **Docker Hub** or private registries.

#### 4. **Docker Containers**

* Runnable instances of Docker images.
* Lightweight and isolated.
* Share the host OS kernel but have their own filesystem and resources.

#### 5. **Dockerfile**

* A script containing a set of instructions to build an image.
* Examples: specify base image, copy files, install dependencies.

#### 6. **Docker Registry**

* A storage and distribution system for Docker images.
* Examples:

  * Public: [Docker Hub](https://hub.docker.com)
  * Private: AWS ECR, GitHub Container Registry

#### 7. **Docker Engine**

* The combination of Docker Daemon and CLI tools.
* Manages the complete container lifecycle.

---

### Visual Diagram (Text-based)

```
+------------------+       REST API        +----------------------+
|   Docker Client  |  <------------------> |     Docker Daemon     |
|  (CLI or GUI)    |                      |     (dockerd)         |
+------------------+                      +----------+-----------+
                                                    |
                                 +------------------+-----------------+
                                 |        Docker Engine Core           |
                                 |                                     |
                                 |  +-----------+   +---------------+ |
                                 |  |  Images   |   |   Containers  | |
                                 |  +-----------+   +---------------+ |
                                 |                                     |
                                 +------------------+-----------------+
                                                    |
                                         Pull / Push Images
                                                    |
                                           +------------------+
                                           | Docker Registry   |
                                           | (Hub or Private)  |
                                           +------------------+
```

---

### Lifecycle Example

1. You run: `docker build -t myapp .`
2. Docker client sends build instructions to the daemon.
3. Daemon builds the image and stores it locally.
4. You run: `docker run myapp`
5. Daemon spins up a container using the image.
