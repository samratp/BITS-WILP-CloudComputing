### What is Kubernetes?

**Kubernetes** (often abbreviated as **K8s**) is an **open-source container orchestration platform** designed to **automate** the deployment, scaling, and management of containerized applications.

Developed by Google and now maintained by the **Cloud Native Computing Foundation (CNCF)**, Kubernetes helps you manage **clusters** of containers across multiple servers.

---

### Why Use Kubernetes?

| Feature                 | Description                                                          |
| ----------------------- | -------------------------------------------------------------------- |
| **Scalability**         | Automatically scale apps up or down based on demand                  |
| **Self-Healing**        | Restarts failed containers, replaces unresponsive ones               |
| **Load Balancing**      | Distributes network traffic to maintain availability and performance |
| **Rollouts/Rollbacks**  | Deploy app updates gradually and revert if needed                    |
| **Service Discovery**   | Automatically exposes containers using DNS and IPs                   |
| **Resource Management** | Efficient usage of CPU, memory, etc. across containers               |

---

### Key Components of Kubernetes

| Component                  | Role                                                                         |
| -------------------------- | ---------------------------------------------------------------------------- |
| **Pod**                    | Smallest unit. A group of one or more containers with shared storage/network |
| **Node**                   | A machine (VM or physical) where pods are deployed                           |
| **Cluster**                | A set of nodes managed by Kubernetes                                         |
| **Deployment**             | Defines how to deploy and update Pods                                        |
| **Service**                | Exposes a set of Pods as a network service                                   |
| **ReplicaSet**             | Ensures the desired number of pod replicas are running at all times          |
| **ConfigMap** / **Secret** | Manage configuration data and sensitive information                          |
| **Ingress**                | Manages external access to services (e.g., via HTTP/HTTPS)                   |

---

### Basic Kubernetes Architecture

```
+-------------------------------------------------------------+
|                        Kubernetes Cluster                   |
|                                                             |
|  +-------------------+      +---------------------------+   |
|  |    Master Node    | <--> |     Worker Nodes (Pods)   |   |
|  |-------------------|      |---------------------------|   |
|  | - API Server      |      | - Kubelet                |    |
|  | - Controller Mgr  |      | - Container Runtime      |    |
|  | - Scheduler       |      | - Pods                   |    |
|  | - etcd (DB)       |      |                           |   |
+-------------------------------------------------------------+
```

---

### Basic Workflow

1. Write a **Deployment YAML** file for your app.
2. Apply it using `kubectl apply -f deployment.yaml`.
3. Kubernetes schedules the app on nodes and manages its lifecycle.
4. Use **Services** to expose the app.
5. Kubernetes monitors and scales as needed.

---

### Example: Simple Deployment YAML

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: my-app
spec:
  replicas: 2
  selector:
    matchLabels:
      app: my-app
  template:
    metadata:
      labels:
        app: my-app
    spec:
      containers:
      - name: my-app-container
        image: my-image:latest
        ports:
        - containerPort: 80
```

---

### Basic `kubectl` Commands

| Command                            | Description                 |
| ---------------------------------- | --------------------------- |
| `kubectl get pods`                 | List all pods               |
| `kubectl get deployments`          | List deployments            |
| `kubectl apply -f deployment.yaml` | Apply configuration         |
| `kubectl delete pod <pod-name>`    | Delete a pod                |
| `kubectl logs <pod-name>`          | View logs from a pod        |
| `kubectl exec -it <pod> -- bash`   | Get shell access into a pod |
