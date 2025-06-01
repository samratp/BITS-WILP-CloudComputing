**Storage in Kubernetes**

Kubernetes provides flexible storage options to support stateful applications by abstracting storage resources from underlying infrastructure. It enables persistent data storage that outlives pod lifecycles.

---

### Key Concepts

1. **Volumes**

   * A directory accessible to containers in a pod.
   * Kubernetes supports various volume types (emptyDir, hostPath, configMap, secret, persistentVolumeClaim, etc.).
   * Volumes exist as long as the pod runs; they do not persist beyond pod deletion unless backed by persistent storage.

2. **Persistent Volumes (PV)**

   * Cluster-wide storage resources provisioned by administrators or dynamically via Storage Classes.
   * Represents a piece of storage in the cluster (e.g., NFS, cloud disks).
   * Abstracts physical storage details.

3. **Persistent Volume Claims (PVC)**

   * Requests for storage by users or pods.
   * Bind to matching Persistent Volumes based on size and access modes.
   * Decouples storage provisioning from pod definition.

4. **Storage Classes**

   * Defines different types of storage (performance, backup policies, provisioning methods).
   * Enables dynamic provisioning of Persistent Volumes.
   * Allows administrators to offer multiple storage tiers.

---

### Access Modes

* **ReadWriteOnce (RWO):** Volume can be mounted as read-write by a single node.
* **ReadOnlyMany (ROX):** Volume can be mounted as read-only by many nodes.
* **ReadWriteMany (RWX):** Volume can be mounted as read-write by many nodes.

---

### Use Cases

* Storing database data persistently outside ephemeral pods.
* Sharing configuration or secrets securely among pods.
* Handling large datasets for batch or machine learning workloads.

---

### Summary

Kubernetes storage abstracts physical storage via Persistent Volumes and Claims, enabling stateful workloads to persist data reliably across pod restarts and rescheduling while supporting diverse storage backends and dynamic provisioning.
