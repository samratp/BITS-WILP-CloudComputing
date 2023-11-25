Here are some of the top Kubernetes commands along with examples:

1. **kubectl get**:
   - Used to retrieve resources from the server.

   Example: Get all pods in the default namespace.
   ```
   kubectl get pods
   ```

2. **kubectl create**:
   - Used to create a resource from a file or standard input.

   Example: Create a pod from a YAML file.
   ```
   kubectl create -f pod.yaml
   ```

3. **kubectl apply**:
   - Used to create or update resources from a file.

   Example: Apply a configuration from a file.
   ```
   kubectl apply -f deployment.yaml
   ```

4. **kubectl describe**:
   - Provides detailed information about a resource.

   Example: Describe a pod.
   ```
   kubectl describe pod my-pod
   ```

5. **kubectl delete**:
   - Deletes resources by name or from a file.

   Example: Delete a pod by name.
   ```
   kubectl delete pod my-pod
   ```

6. **kubectl exec**:
   - Runs a command in a container.

   Example: Execute a shell in a running pod.
   ```
   kubectl exec -it my-pod -- /bin/sh
   ```

7. **kubectl logs**:
   - Retrieves the logs of a container.

   Example: Get the logs of a pod.
   ```
   kubectl logs my-pod
   ```

8. **kubectl port-forward**:
   - Forwards local port to a pod.

   Example: Forward local port 8080 to port 80 in the pod.
   ```
   kubectl port-forward my-pod 8080:80
   ```

9. **kubectl get namespaces**:
   - Lists all namespaces.

   Example: Get all namespaces.
   ```
   kubectl get namespaces
   ```

10. **kubectl apply -f**:
    - Creates or updates a resource defined in a file.

    Example: Apply a configuration from a URL.
    ```
    kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v2.3.1/aio/deploy/recommended.yaml
    ```

11. **kubectl scale**:
    - Scales the number of pods in a deployment.

    Example: Scale a deployment to 3 replicas.
    ```
    kubectl scale deployment my-deployment --replicas=3
    ```

12. **kubectl rollout status**:
    - Checks the status of a rollout.

    Example: Check the status of a deployment rollout.
    ```
    kubectl rollout status deployment/my-deployment
    ```

13. **kubectl get events**:
    - Lists events in the cluster.

    Example: Get events in the default namespace.
    ```
    kubectl get events
    ```

14. **kubectl label**:
    - Adds or updates labels on resources.

    Example: Add a label to a pod.
    ```
    kubectl label pod my-pod app=my-app
    ```

15. **kubectl annotate**:
    - Adds or updates annotations on resources.

    Example: Add an annotation to a pod.
    ```
    kubectl annotate pod my-pod description="My Pod"
    ```

These are some of the commonly used `kubectl` commands. Remember to replace placeholders like `my-pod` and `my-deployment` with actual resource names in your cluster.
