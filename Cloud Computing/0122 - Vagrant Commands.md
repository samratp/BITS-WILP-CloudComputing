Vagrant provides a set of command-line tools that allow users to manage virtualized development environments easily. Here are some commonly used Vagrant commands:

### Initializing and Configuring:

1. **`vagrant init [box]`:**
   - Initializes a new Vagrant environment with an optional base box. This command creates a `Vagrantfile` in the current directory.

   ```bash
   vagrant init ubuntu/bionic64
   ```

2. **`vagrant up`:**
   - Creates and provisions the virtual machine based on the configurations specified in the `Vagrantfile`.

   ```bash
   vagrant up
   ```

3. **`vagrant status`:**
   - Displays the status of the virtual machine (running, halted, etc.).

   ```bash
   vagrant status
   ```

### Accessing and Managing:

4. **`vagrant ssh`:**
   - Connects to the virtual machine via SSH. Provides direct access to the command line of the virtual machine.

   ```bash
   vagrant ssh
   ```

5. **`vagrant halt`:**
   - Stops the virtual machine.

   ```bash
   vagrant halt
   ```

6. **`vagrant suspend`:**
   - Suspends the virtual machine, saving its current state.

   ```bash
   vagrant suspend
   ```

7. **`vagrant resume`:**
   - Resumes a suspended virtual machine.

   ```bash
   vagrant resume
   ```

8. **`vagrant reload`:**
   - Reloads the virtual machine, applying changes to the `Vagrantfile`.

   ```bash
   vagrant reload
   ```

9. **`vagrant provision`:**
   - Re-runs the provisioning scripts defined in the `Vagrantfile` without restarting the virtual machine.

   ```bash
   vagrant provision
   ```

### Cleanup and Deletion:

10. **`vagrant destroy`:**
    - Destroys the virtual machine, deleting all associated resources. Use with caution, as this is irreversible.

    ```bash
    vagrant destroy
    ```

### Information and Debugging:

11. **`vagrant global-status`:**
    - Displays the status of all Vagrant environments on the host machine.

    ```bash
    vagrant global-status
    ```

12. **`vagrant port`:**
    - Displays the mapping of ports between the host and the guest machine.

    ```bash
    vagrant port
    ```

### Networking:

13. **`vagrant share`:**
    - Shares your Vagrant environment with others using a public URL.

    ```bash
    vagrant share
    ```

### Plugin Management:

14. **`vagrant plugin install [plugin_name]`:**
    - Installs a Vagrant plugin.

    ```bash
    vagrant plugin install vagrant-disksize
    ```

15. **`vagrant plugin list`:**
    - Lists all installed Vagrant plugins.

    ```bash
    vagrant plugin list
    ```

16. **`vagrant plugin uninstall [plugin_name]`:**
    - Uninstalls a Vagrant plugin.

    ```bash
    vagrant plugin uninstall vagrant-disksize
    ```

### Box Management:

17. **`vagrant box add [box_name]`:**
    - Adds a box to Vagrant. Boxes are the base images used to create virtual machines.

    ```bash
    vagrant box add ubuntu/bionic64
    ```

18. **`vagrant box list`:**
    - Lists all available boxes on the local machine.

    ```bash
    vagrant box list
    ```

19. **`vagrant box remove [box_name]`:**
    - Removes a box from Vagrant.

    ```bash
    vagrant box remove ubuntu/bionic64
    ```

These are some of the essential Vagrant commands. Remember to check the [official Vagrant documentation](https://www.vagrantup.com/docs/cli) for more detailed information on each command and its options.
