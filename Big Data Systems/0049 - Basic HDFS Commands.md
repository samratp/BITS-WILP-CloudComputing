Here are some basic HDFS (Hadoop Distributed File System) commands that you can use to interact with the file system:

1. **Listing Files/Directories**:
   - List files and directories in a given path.
   ```
   hdfs dfs -ls <path>
   ```

2. **Creating a Directory**:
   - Create a new directory in HDFS.
   ```
   hdfs dfs -mkdir <path>
   ```

3. **Copying Files**:
   - Copy files or directories from the local file system to HDFS.
   ```
   hdfs dfs -put <source> <destination>
   ```

4. **Copying Files (from HDFS to local)**:
   - Copy files or directories from HDFS to the local file system.
   ```
   hdfs dfs -get <source> <destination>
   ```

5. **Removing Files/Directories**:
   - Remove files or directories from HDFS.
   ```
   hdfs dfs -rm <path>
   ```

6. **Removing Files/Directories (recursive)**:
   - Remove files or directories and their contents recursively.
   ```
   hdfs dfs -rm -r <path>
   ```

7. **Moving Files/Directories**:
   - Move files or directories within HDFS.
   ```
   hdfs dfs -mv <source> <destination>
   ```

8. **Creating an Empty File**:
   - Create an empty file in HDFS.
   ```
   hdfs dfs -touchz <path>
   ```

9. **Viewing File Content**:
   - View the content of a file in HDFS.
   ```
   hdfs dfs -cat <file>
   ```

10. **Checking File Existence**:
    - Check if a file or directory exists in HDFS.
    ```
    hdfs dfs -test -e/-d <path>
    ```

11. **Checking File Permissions**:
    - Check the permissions of a file or directory in HDFS.
    ```
    hdfs dfs -ls -d <path>
    ```

12. **Changing File Permissions**:
    - Change the permissions of a file or directory in HDFS.
    ```
    hdfs dfs -chmod <permissions> <path>
    ```

13. **Changing File Ownership**:
    - Change the owner and group of a file or directory in HDFS.
    ```
    hdfs dfs -chown <owner>:<group> <path>
    ```

14. **Getting File Information**:
    - Get detailed information about a file or directory in HDFS.
    ```
    hdfs dfs -stat <path>
    ```

15. **Checking Disk Usage**:
    - Check the disk usage of a file or directory in HDFS.
    ```
    hdfs dfs -du -s <path>
    ```

16. **Setting Replication Factor**:
    - Set the replication factor for a file in HDFS.
    ```
    hdfs dfs -setrep <replication_factor> <path>
    ```

Remember to replace `<path>`, `<source>`, and `<destination>` with the actual paths or file names you are working with. These commands will help you perform basic operations in HDFS.
