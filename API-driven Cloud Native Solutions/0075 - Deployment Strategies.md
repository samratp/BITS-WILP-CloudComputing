### Deployment Strategies for Zero-Downtime Releases

Zero-downtime deployments (also called **hot deployments**) are release strategies that aim to **update applications in production without disrupting the user experience**. These techniques ensure availability, minimize risk, and allow smoother rollouts.

Below are the common deployment strategies:

---

### 1. **Basic (Recreate) Deployment**

* **What it is**: The old version is shut down, and the new version is deployed.
* **Downtime**: Yes – brief downtime during the switchover.
* **Use Case**: Simple applications, dev/test environments.

---

### 2. **Ramped Deployment (Rolling Update)**

* **What it is**: Gradually replaces old instances of the application with new ones, one at a time or in batches.
* **How it works**:

  * Slowly terminates pods running the old version.
  * Simultaneously starts pods running the new version.
* **Downtime**: No, if done correctly.
* **Risk**: Medium – if there's an issue, rollback takes time.
* **Use Case**: Common in Kubernetes (`RollingUpdate` is the default strategy).

---

### 3. **Blue/Green Deployment**

* **What it is**: Two identical environments (blue and green). Blue is the current production; green is the new version.
* **How it works**:

  * Green is fully tested in parallel.
  * Once ready, traffic is switched from blue to green instantly.
  * Rollback is simple — just switch back to blue.
* **Downtime**: None.
* **Risk**: Low.
* **Cost**: Higher (requires duplicate environments).
* **Use Case**: Safer releases, production-critical systems.

---

### 4. **Canary Deployment**

* **What it is**: Gradually rolls out the new version to a small percentage of users, then slowly increases.
* **How it works**:

  * Start with 5% of users on the new version.
  * Monitor for issues.
  * Gradually increase to 100% if stable.
* **Downtime**: None.
* **Risk**: Very low.
* **Use Case**: High-risk features, production environments with observability.

---

### Summary Table

| Strategy   | Downtime | Risk     | Rollback Effort | Cost   | Best For                        |
| ---------- | -------- | -------- | --------------- | ------ | ------------------------------- |
| Basic      | Yes      | High     | Manual          | Low    | Dev/test setups                 |
| Ramped     | No       | Medium   | Medium          | Medium | Typical web apps in production  |
| Blue/Green | No       | Low      | Easy            | High   | Mission-critical apps           |
| Canary     | No       | Very Low | Very Easy       | Medium | Gradual rollout with monitoring |
