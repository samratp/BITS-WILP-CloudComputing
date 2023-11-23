In Hadoop 2, YARN (Yet Another Resource Negotiator) plays a crucial role in managing resources and scheduling tasks on a Hadoop cluster. Let's delve into the details of YARN and the key components involved:

### YARN Components:

1. **ResourceManager (RM):**
   - The ResourceManager is the central authority that manages resources across the Hadoop cluster.
   - It consists of two main components:
     - **Scheduler:** Allocates resources to various applications based on policies and constraints.
     - **ApplicationManager (AM):** Manages the lifecycle of individual applications.

2. **NodeManager (NM):**
   - NodeManagers run on each machine in the cluster and are responsible for managing resources on that node.
   - They report the available resources and the utilization back to the ResourceManager.
   - NodeManagers are responsible for launching and monitoring containers, which are the basic units of computation in YARN.

3. **ApplicationMaster (AM):**
   - Each application running on YARN has its own ApplicationMaster.
   - The AM negotiates resources with the ResourceManager and works with the NodeManagers to execute and monitor tasks.
   - It is responsible for dynamic resource management and handling failures.

### YARN Workflow:

1. **Application Submission:**
   - A user submits a YARN application, specifying the application's resource requirements and the location of the application code.

2. **ResourceManager Allocation:**
   - The ResourceManager receives the application submission and negotiates resources based on the application's requirements.
   - It allocates a container on a NodeManager for the ApplicationMaster.

3. **ApplicationMaster Execution:**
   - The ApplicationMaster is launched on the allocated container and takes over the management of the application's lifecycle.
   - It negotiates additional resources with the ResourceManager for running tasks.

4. **Task Execution:**
   - The ApplicationMaster negotiates resources for tasks with the ResourceManager and works with NodeManagers to launch containers for those tasks.
   - Containers run tasks, which can be Map or Reduce tasks in the context of MapReduce jobs.

5. **Resource Monitoring:**
   - ResourceManager and NodeManagers continuously monitor resource utilization and report back to each other.

### NodeManager Components:

1. **Container:**
   - A container is a logical unit of resource allocation in YARN.
   - It represents resources such as CPU, memory, and network.
   - Containers are launched by NodeManagers to execute tasks.

2. **Local Resource Manager (LMR):**
   - Manages resources on a specific node and communicates with the ResourceManager to request or release resources.

3. **Application Container Manager (ACM):**
   - Manages the lifecycle of containers for a specific application.
   - It launches, monitors, and reports the status of containers to the ResourceManager.

### YARN Nodes:

1. **ResourceManager Node:**
   - The ResourceManager runs on a designated node in the cluster.
   - It coordinates resource allocation across the entire cluster.

2. **NodeManager Nodes:**
   - NodeManagers run on every machine in the cluster that can contribute resources.
   - They manage resources on individual nodes and execute containers.

### Conclusion:

YARN's architecture allows for a flexible and scalable resource management framework in Hadoop 2. By separating resource management from application execution, YARN enables Hadoop to support a diverse set of processing engines beyond MapReduce, making it a versatile platform for big data processing.
