**Kubernetes Architecture**

Kubernetes architecture is designed as a distributed system that manages containerized applications across a cluster of machines. It consists of a set of components that work together to ensure application deployment, scaling, and management are automated and resilient.

---

### 1. **Cluster**

* A Kubernetes cluster is a set of machines (physical or virtual) that run containerized applications.
* It consists of at least one **Control Plane (Master)** node and multiple **Worker (Node)** machines.

---

### 2. **Control Plane**

The Control Plane manages the overall cluster state, making global decisions about the cluster and detecting/responding to events.

**Main components:**

* **API Server (kube-apiserver):**

  * Frontend of the control plane.
  * Exposes Kubernetes API used by users, CLI (kubectl), and components.
  * Validates and configures data for API objects.

* **etcd:**

  * A consistent and highly-available key-value store.
  * Stores all cluster data, including configuration and state.

* **Controller Manager (kube-controller-manager):**

  * Runs controller processes that regulate the state of the cluster.
  * Examples: Node controller, replication controller, endpoint controller.
  * Ensures the desired state matches the actual cluster state.

* **Scheduler (kube-scheduler):**

  * Assigns newly created pods to nodes based on resource availability and constraints.
  * Balances load across nodes and considers affinity, taints, and tolerations.

---

### 3. **Worker Nodes**

* Nodes run containerized applications and host the necessary components to manage and run pods.

**Components on each Node:**

* **Kubelet:**

  * Agent that communicates with the control plane.
  * Ensures containers described in PodSpecs are running and healthy.

* **Container Runtime:**

  * Software responsible for running containers (e.g., Docker, containerd, CRI-O).

* **Kube-Proxy:**

  * Manages network rules on nodes to enable service discovery and load balancing.
  * Handles forwarding of requests to the correct pods.

---

### 4. **Pods**

* The smallest deployable unit in Kubernetes.
* Encapsulates one or more containers, shared storage, and network.
* Pods run on nodes and are managed by the control plane.

---

### 5. **Services**

* Abstract a logical set of pods and provide a stable IP and DNS name.
* Enable communication between microservices and external access.

---

### 6. **Add-ons**

* Additional components that extend Kubernetes functionality.
* Examples: DNS (CoreDNS), Dashboard UI, monitoring tools (Prometheus), network plugins (CNI).

---

### Summary Diagram (Conceptual):

```
+-----------------------+
|      Control Plane     |
| +-------------------+ |
| | API Server        | |
| | etcd              | |
| | Scheduler         | |
| | Controller Manager| |
| +-------------------+ |
+-----------|-----------+
            |
            |
  +---------+----------+
  |                    |
+---------+        +---------+
| Worker  |        | Worker  |
| Node 1  |        | Node 2  |
| +-----+ |        | +-----+ |
| |Kube-| |        | |Kube-| |
| |let  | |        | |let  | |
| |Proxy| |        | |Proxy| |
| |CRI  | |        | |CRI  | |
| +-----+ |        | +-----+ |
+---------+        +---------+
```

---

This modular architecture allows Kubernetes to be highly scalable, fault-tolerant, and extensible, making it ideal for managing microservices in production environments.
