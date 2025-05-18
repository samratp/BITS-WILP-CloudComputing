## Kubernetes Architecture

Kubernetes is an open-source container orchestration platform that automates deployment, scaling, and management of containerized applications. Its architecture is divided into two main components:

* Control Plane
* Worker Nodes

---

### 1. Control Plane (Master Node)

The Control Plane is responsible for managing the overall state of the Kubernetes cluster. It makes global decisions (like scheduling) and detects/responds to cluster events.

#### API Server

* Acts as the entry point for all administrative commands.
* Exposes the Kubernetes API and is the front-end of the control plane.
* Validates and processes REST requests, then updates the state of the cluster.

#### etcd

* A distributed, consistent key-value store that stores all cluster data.
* Serves as the source of truth for the cluster's state.
* Used for configuration, service discovery, and storing metadata.

#### Scheduler

* Assigns newly created pods to nodes.
* Chooses the best node based on factors such as resource availability, policies, and constraints.
* Ensures efficient resource utilization and load balancing.

#### Controller Manager

* Runs various controllers to regulate the state of the cluster.
* Includes Node Controller (monitors node health), ReplicaSet Controller (ensures desired number of pod replicas), and others.
* Watches the current state via the API server and takes actions to reach the desired state.

---

### 2. Worker Nodes

Worker nodes are the machines (physical or virtual) that run the containerized applications.

#### Kubelet

* An agent that runs on each worker node.
* Communicates with the API server.
* Ensures that containers are running in a pod as specified in the deployment.

#### Container Runtime

* The software responsible for running containers.
* Examples include Docker, containerd, and CRI-O.
* Executes the instructions received from Kubelet to run containers.

#### Kube Proxy

* Maintains network rules on nodes.
* Allows communication between pods within the cluster and handles request forwarding.
* Implements cluster-level service abstraction.

---

### 3. Pods

* A pod is the smallest deployable unit in Kubernetes.
* Each pod encapsulates one or more containers that share the same network namespace and storage volumes.
* Pods are ephemeral; Kubernetes automatically replaces failed pods to maintain the desired state.

---

## Summary Flow

Here is how a typical application deployment flows through the Kubernetes architecture:

1. A user submits a deployment via `kubectl` or a YAML configuration.
2. The API Server receives the request and stores the intended state in etcd.
3. The Scheduler identifies a suitable worker node and assigns the pod.
4. The Controller Manager ensures the deployment matches the intended state.
5. Kubelet on the selected worker node pulls the container image and runs the pod.
6. Kube Proxy handles networking and routing so the application can communicate within and outside the cluster.
