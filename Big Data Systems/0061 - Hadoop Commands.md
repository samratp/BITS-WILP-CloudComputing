Certainly! Below are examples of Hadoop Distributed File System (HDFS) commands:

### 1. **Copy from Local:**
   - Copy a local file to HDFS.
   ```bash
   hdfs dfs -copyFromLocal localfile /user/hadoop/hdfsfile
   ```

### 2. **Copy to Local:**
   - Copy a file from HDFS to the local file system.
   ```bash
   hdfs dfs -copyToLocal /user/hadoop/hdfsfile localfile
   ```

### 3. **Make Directory:**
   - Create a new directory in HDFS.
   ```bash
   hdfs dfs -mkdir /user/hadoop/newdir
   ```

### 4. **List Files:**
   - List files and directories in a HDFS directory.
   ```bash
   hdfs dfs -ls /user/hadoop
   ```

### 5. **Remove Directory:**
   - Remove a directory in HDFS.
   ```bash
   hdfs dfs -rm -r /user/hadoop/old_dir
   ```

### 6. **Put File:**
   - Copy a file from the local file system to HDFS.
   ```bash
   hdfs dfs -put localfile /user/hadoop/hdfsfile
   ```

### 7. **Get File:**
   - Copy a file from HDFS to the local file system.
   ```bash
   hdfs dfs -get /user/hadoop/hdfsfile localfile
   ```

### 8. **Move File:**
   - Move a file within HDFS.
   ```bash
   hdfs dfs -mv /user/hadoop/oldfile /user/hadoop/newfile
   ```

### 9. **Cat File:**
   - Display the content of a file in HDFS.
   ```bash
   hdfs dfs -cat /user/hadoop/hdfsfile
   ```

### 10. **Count Files and Directories:**
   - Count the number of files and directories in HDFS.
   ```bash
   hdfs dfs -count -q /user/hadoop
   ```

### 11. **Disk Usage:**
   - Display the disk usage of a file or directory in HDFS.
   ```bash
   hdfs dfs -du /user/hadoop/hdfsfile
   ```

### 12. **File Block Locations:**
   - Get the block locations of a file in HDFS.
   ```bash
   hdfs fsck /user/hadoop/hdfsfile -files -blocks -locations
   ```

### 13. **Chmod:**
   - Change the permissions of a file or directory in HDFS.
   ```bash
   hdfs dfs -chmod 755 /user/hadoop/hdfsfile
   ```

### 14. **Chown:**
   - Change the owner of a file or directory in HDFS.
   ```bash
   hdfs dfs -chown hadoop:hadoop /user/hadoop/hdfsfile
   ```

### 15. **Checksum:**
   - Get the checksum of a file in HDFS.
   ```bash
   hdfs dfs -checksum /user/hadoop/hdfsfile
   ```

### 16. **Tail:**
   - Display the last kilobyte of a file's contents in HDFS.
   ```bash
   hdfs dfs -tail /user/hadoop/hdfsfile
   ```

### 17. **Set Replication:**
   - Set the replication factor for a file in HDFS.
   ```bash
   hdfs dfs -setrep -w 2 /user/hadoop/hdfsfile
   ```

### 18. **File Compression:**
   - Compress a file in HDFS using gzip.
   ```bash
   hdfs dfs -Dmapreduce.output.fileoutputformat.compress=true -Dmapreduce.output.fileoutputformat.compress.codec=org.apache.hadoop.io.compress.GzipCodec -put localfile /user/hadoop/hdfsfile
   ```

### 19. **Read Configuration:**
   - Display HDFS configuration settings.
   ```bash
   hdfs getconf -confKey dfs.replication
   ```

### 20. **Trash:**
   - Move a file to the trash in HDFS.
   ```bash
   hdfs dfs -mv /user/hadoop/hdfsfile /user/hadoop/.Trash
   ```

### 21. **List Trash:**
   - List files in the HDFS trash.
   ```bash
   hdfs dfs -ls /user/hadoop/.Trash
   ```

### 22. **Snapshot:**
   - Create a snapshot of a directory in HDFS.
   ```bash
   hdfs dfs -createSnapshot /user/hadoop/snapshottable_dir snapshot_name
   ```

### 23. **List Snapshots:**
   - List all snapshots of a directory in HDFS.
   ```bash
   hdfs dfs -listSnapshots /user/hadoop/snapshottable_dir
   ```

### 24. **Rollback Snapshot:**
   - Rollback a directory in HDFS to a specific snapshot.
   ```bash
   hdfs dfs -rollback /user/hadoop/snapshottable_dir snapshot_name
   ```

### 25. **Set Quota:**
   - Set a namespace quota for a directory in HDFS.
   ```bash
   hdfs dfsadmin -setSpaceQuota 100G /user/hadoop/quota_dir
   ```

### 26. **NameNode Safe Mode:**
   - Enter or leave the safe mode for maintenance in HDFS.
   ```bash
   hdfs dfsadmin -safemode enter
   ```

### 27. **DataNode Decommission:**
   - Decommission a DataNode in HDFS.
   ```bash
   hdfs dfsadmin -refreshNodes
   ```

### 28. **Balancer:**
   - Run the HDFS balancer to balance data distribution.
   ```bash
   hdfs balancer
   ```

### 29. **Set Trash Interval:**
   - Set the trash interval for files in

 HDFS.
   ```bash
   hdfs dfsadmin -setTrashInterval 1440
   ```

### 30. **List Corrupt Files:**
   - List corrupt files in HDFS.
   ```bash
   hdfs fsck / -files -locations -list-corruptfileblocks
   ```

These commands cover a variety of HDFS operations and are essential for managing files and directories within a Hadoop cluster. Adjust parameters according to your specific HDFS setup.
