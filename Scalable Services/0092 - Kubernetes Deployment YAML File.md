**Kubernetes Deployment YAML File**

A Deployment YAML file is a declarative configuration used to describe a Kubernetes Deployment object. It defines the desired state of an application, including the number of replicas, the container image, update strategy, and more.

---

### Example of a Basic Deployment YAML

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: my-app
  labels:
    app: my-app
spec:
  replicas: 3                                  # Number of pod replicas
  selector:
    matchLabels:
      app: my-app                             # Selector to match pods managed by this Deployment
  template:
    metadata:
      labels:
        app: my-app                           # Labels applied to pods
    spec:
      containers:
      - name: my-container
        image: my-app-image:v1                # Container image to run
        ports:
        - containerPort: 80                   # Port exposed by the container
        readinessProbe:                       # Optional readiness probe
          httpGet:
            path: /health
            port: 80
          initialDelaySeconds: 5
          periodSeconds: 10
        resources:                           # Optional resource requests and limits
          requests:
            cpu: "100m"
            memory: "200Mi"
          limits:
            cpu: "500m"
            memory: "500Mi"
  strategy:
    type: RollingUpdate                       # Update strategy (RollingUpdate or Recreate)
    rollingUpdate:
      maxUnavailable: 1                       # Max pods unavailable during update
      maxSurge: 1                            # Max pods created above desired during update
```

---

### Key Sections Explained

* **apiVersion:** Specifies Kubernetes API version (e.g., `apps/v1` for Deployments).
* **kind:** Resource type (`Deployment`).
* **metadata:** Contains resource identifiers like `name` and `labels`.
* **spec:** Defines the desired state:

  * **replicas:** Number of pods to run.
  * **selector:** Label selector to identify pods managed by this Deployment.
  * **template:** Pod template specifying metadata and pod spec.
* **containers:** List of containers inside the pod, each with:

  * **name:** Container name.
  * **image:** Container image.
  * **ports:** Container ports exposed.
  * **readinessProbe:** Probe to check if the container is ready to receive traffic.
  * **resources:** CPU and memory resource requests and limits.
* **strategy:** Defines the update strategy for rolling updates or recreations.

---

This YAML file, when applied via `kubectl apply -f deployment.yaml`, creates or updates a Deployment that manages pod replicas to run the specified application reliably and scalably.
