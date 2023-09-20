Kubernetes follows a master-worker architecture. Here are the key components of a Kubernetes cluster:

**Master Components:**

1. **API Server**: This is the entry point for all administrative tasks. It validates and configures data for the API objects, which include pods, services, replication controllers, and others.

2. **Controller Manager**: This component ensures that the current state of the cluster matches the desired state. It includes several controllers like the Replication Controller, Endpoints Controller, Namespace Controller, and more.

3. **Scheduler**: The scheduler is responsible for distributing work (in the form of pods) across multiple nodes. It considers factors like resource requirements, quality of service, and anti-affinity/affinity rules.

4. **etcd**: This is a distributed key-value store that holds the cluster's configuration data, representing the overall state of the cluster at any given point in time.

5. **Kube Controller Manager**: It is a daemon that embeds the core control loops that are shipped with Kubernetes. Examples of controllers include the Replication Controller for maintaining the correct number of pods, the Endpoints Controller for ensuring that services are correctly configured, and others.

**Node Components:**

1. **Kubelet**: This is the primary agent that runs on each node. It is responsible for maintaining the set of pods and making sure they are running and healthy.

2. **Kube Proxy**: This maintains network rules on nodes. These network rules allow network communication to your pods from network sessions inside or outside of your cluster.

3. **Container Runtime**: This is the software responsible for running containers. Kubernetes supports several container runtimes including Docker, containerd, and others.

**Add-ons:**

1. **DNS**: This is an add-on that allows DNS-based name resolution to pods.

2. **Dashboard**: The web-based UI for managing the cluster.

3. **Ingress Controllers**: They manage external access to the services in a cluster.

4. **Monitoring Tools**: Tools like Prometheus for monitoring the performance of the cluster.

**Other Components:**

1. **Service**: A way to expose a set of pods as a network service. This abstraction allows for decoupling between frontend and backend services.

2. **Pod**: The smallest unit in Kubernetes. It can contain one or more containers and shared resources.

3. **Volume**: A directory that is accessible to the containers in a pod.

4. **Namespace**: Provides a way to divide cluster resources between multiple users.

5. **ConfigMap and Secret**: These are used to separate configuration details from application code. ConfigMaps store configuration data as key-value pairs, and Secrets store sensitive information like passwords and tokens.

Kubernetes is designed to be highly scalable and fault-tolerant, making it suitable for managing containerized workloads in production environments.
