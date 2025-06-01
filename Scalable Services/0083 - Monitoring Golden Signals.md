**Monitoring Golden Signals**

The **Four Golden Signals** are a set of key metrics proposed by Google’s Site Reliability Engineering (SRE) practices to monitor the health and performance of scalable services. Monitoring these helps teams detect, diagnose, and resolve issues effectively in distributed systems.

---

### 1. **Latency**

**Definition:**
The time it takes to service a request, typically measured in milliseconds (ms) or seconds (s).

**Types:**

* **Successful Request Latency**: Time taken when everything works correctly.
* **Failed Request Latency**: May be faster (fail-fast) or much slower (timeouts).

**Use Cases:**

* Detect slow database queries or overloaded services.
* Track client-perceived performance (e.g., API response time).

**Example Alert:**
“95th percentile latency > 500ms for /checkout endpoint”

---

### 2. **Traffic**

**Definition:**
The amount of demand placed on your system, measured in requests per second (RPS), queries per second (QPS), or transactions per minute.

**Use Cases:**

* Understand workload patterns and plan scaling.
* Detect sudden drops or spikes in usage (which may indicate failures or DDoS attacks).

**Example Metrics:**

* HTTP request count.
* Kafka messages consumed per minute.
* API hits per endpoint.

---

### 3. **Errors**

**Definition:**
The rate of requests that fail due to client-side or server-side issues.

**Types:**

* **4xx Errors**: Client-side issues (bad input, unauthorized access).
* **5xx Errors**: Server-side problems (crashes, timeouts).
* **Application Errors**: Custom failure conditions (e.g., “payment declined”).

**Use Cases:**

* Identify degraded services or failed deployments.
* Track impact of external dependency failures.

**Example Alert:**
“5xx error rate > 2% in the last 5 minutes”

---

### 4. **Saturation**

**Definition:**
How "full" your system is — i.e., how close it is to its capacity limits.

**Metrics Monitored:**

* CPU/memory utilization.
* Thread pool usage.
* Disk I/O and database connection pool saturation.
* Queue lengths.

**Use Cases:**

* Detect risk of resource exhaustion before it causes downtime.
* Trigger autoscaling based on capacity.

**Example Alert:**
“CPU usage > 90% for more than 3 minutes”

---

### Summary Table

| Signal         | What It Measures        | Why It's Important                             |
| -------------- | ----------------------- | ---------------------------------------------- |
| **Latency**    | Response time           | Detect slowdowns or bottlenecks                |
| **Traffic**    | Volume of requests/data | Capacity planning and usage trends             |
| **Errors**     | Request failure rate    | Identify bugs, outages, and reliability issues |
| **Saturation** | Resource utilization    | Prevent overload and ensure scalability        |

---

Monitoring these four signals across all critical services gives teams a strong foundation for system observability and proactive incident management in scalable, microservice-based environments.
