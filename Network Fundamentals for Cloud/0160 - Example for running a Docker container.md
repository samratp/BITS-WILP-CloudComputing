Certainly! Below is a simple example of running a Docker container using the `docker run` command. This example uses a basic Docker image, the official "hello-world" image provided by Docker to demonstrate a simple containerized application.

1. **Pull the Docker Image:**
   Before running a container, you need to pull the Docker image from the Docker Hub (if it's not already available locally).

   ```bash
   docker pull hello-world
   ```

2. **Run the Docker Container:**
   Once the image is pulled, you can run a container using the `docker run` command.

   ```bash
   docker run hello-world
   ```

   The output will be a brief message indicating that your Docker installation is working:

   ```
   Hello from Docker!
   This message shows that your installation appears to be working correctly.
   ...
   ```

   This "hello-world" image is a minimal image designed solely for the purpose of verifying that Docker is correctly installed and functioning.

3. **Check Running Containers:**
   You can check the list of running containers using the following command:

   ```bash
   docker ps
   ```

   However, in this case, the "hello-world" container is so lightweight that it runs and exits immediately. To see all containers (including those that have exited), you can use:

   ```bash
   docker ps -a
   ```

   The container ID, image used, status, and other details will be displayed.

4. **Cleanup (Optional):**
   If you want to remove the exited container, you can use the following command:

   ```bash
   docker rm <container_id_or_name>
   ```

   Replace `<container_id_or_name>` with the actual ID or name of the container.

This example demonstrates the basic steps to pull a Docker image and run a container. In real-world scenarios, you'd use more complex images corresponding to your applications, specifying additional configurations, environment variables, network settings, and volumes as needed.
