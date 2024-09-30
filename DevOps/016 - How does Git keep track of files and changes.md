Git uses a highly efficient system to track files and changes in a repository. It’s based on snapshots of the project's file system over time, with several mechanisms for ensuring performance, reliability, and flexibility. Let’s break down how Git manages this process:

### 1. **Snapshots, Not Deltas**
Unlike other version control systems that track file changes as deltas (or differences) between versions, Git takes snapshots of the project each time a commit is made. When you commit changes, Git doesn’t store the actual differences but a full snapshot of all the files at that point in time. However, it optimizes storage by saving only the files that changed, and for unchanged files, it just adds references to the previous version of the file.

#### Key Idea:
- **Snapshot**: Each commit in Git is a complete snapshot of the project’s state, not just a diff.
- **Efficient Storage**: If files haven’t changed, Git just references the previously stored file.

### 2. **Object Model**
Git stores data as a series of objects in a key-value database, where each object is identified by a **SHA-1 hash** (a 40-character string). These objects fall into three main categories:
   - **Blob (Binary Large Object)**: Stores the actual content of a file.
   - **Tree**: Represents a directory and contains pointers to blobs and other trees (subdirectories).
   - **Commit**: Represents a snapshot of the repository, containing metadata like the author, message, and a pointer to the root tree object of that snapshot.

#### Example:
When you commit, Git creates:
- A **blob** object for each file's content.
- A **tree** object to represent the file structure.
- A **commit** object linking to the root tree object and storing metadata about the commit.

### 3. **Index (Staging Area)**
The **index** (or staging area) is a temporary area where Git stores information about the files that are about to be committed. When you run `git add`, changes are added to the index, but they are not yet committed. This allows you to carefully control which files and changes will go into the next commit.

#### Key Idea:
- **Staging Area**: Prepares changes for the next commit. Files can be staged individually.

#### Example:
```bash
git add file1.txt
# Adds file1.txt to the index (staging area) but doesn’t commit it yet.
```

### 4. **Tracking Changes with SHA-1 Hashes**
Git uses a cryptographic **SHA-1 hash** to identify each file, commit, and tree uniquely. Each time you commit, Git generates a unique hash based on the content of the files and the commit history. This ensures that even the smallest change in the file will generate a different hash.

#### Key Idea:
- **SHA-1 Hash**: A unique identifier for each object, ensuring content integrity.
  
#### Example:
When you run `git log`, the SHA-1 hash is visible as the commit ID:
```bash
git log
# Shows:
# commit 1a2b3c4d5e6f...
# Author: User <email>
# Date: Mon Sep 27 09:32:15 2024
# Message: Initial commit
```

### 5. **Working Directory and HEAD**
Git maintains three states for your files:
   - **Working Directory**: The actual files on your filesystem, where you make changes.
   - **Index (Staging Area)**: The files that are marked for inclusion in the next commit.
   - **HEAD**: Points to the latest commit on the current branch, representing the most recent snapshot.

When you modify files, they are in your working directory. Running `git add` stages them, and `git commit` moves them from the staging area into the repository, updating `HEAD` to point to the new commit.

#### Key Idea:
- **HEAD** points to the latest commit in the branch.
- **Working Directory**: Where you actively modify files.
- **Staging Area**: Prepares changes for the next commit.

---

### **How Git Records and Tracks Changes**
To summarize the process:

1. **Modify Files**: You make changes to files in your working directory.
2. **Stage Changes** (`git add`): You add the modified files to the staging area (index), which prepares them for committing.
3. **Commit Changes** (`git commit`): Git takes a snapshot of the project’s state, calculates SHA-1 hashes for the objects (files, directories, and commit), and stores them in the repository.
4. **Link to Previous Commits**: The commit object contains references to the previous commit(s), forming a history chain.
   
### Example Workflow:
```bash
# Modify a file in your working directory
echo "Hello World" > file.txt

# Stage the changes
git add file.txt

# Commit the changes (takes a snapshot)
git commit -m "Added file.txt with Hello World"

# Git creates a blob for file.txt, a tree for the directory, and a commit referencing the tree and previous commit.
```

---

### 6. **Branches and Merging**
Git tracks changes across branches, which are simply pointers to commits. When you create a new branch, Git creates a new pointer to a commit, and you can switch between branches without losing any work.

- **Branch**: A lightweight pointer to a specific commit.
- **Merge**: Combines changes from one branch into another, either automatically or with manual conflict resolution.

#### Example:
```bash
# Create a new branch
git branch new-feature

# Switch to the new branch
git checkout new-feature

# Make changes, then merge them back into the main branch
git checkout main
git merge new-feature
```

---

### 7. **Tracking Untracked and Ignored Files**
- **Untracked Files**: Files that are not yet being tracked by Git will show up when you run `git status`. You need to `git add` them to start tracking them.
- **.gitignore**: If there are files you don’t want Git to track (such as build artifacts or sensitive data), you can list them in a `.gitignore` file.

#### Example `.gitignore` file:
```bash
# Ignore log files
*.log

# Ignore node_modules directory
node_modules/
```

---

### 8. **Garbage Collection**
Git also has a built-in mechanism for cleaning up unnecessary files and optimizing storage. When you delete branches or commits, Git doesn't immediately remove them but marks them as unreachable. Over time, Git runs **garbage collection** (via `git gc`) to remove these unreachable objects, freeing up space.

---

### **Summary**

Git tracks files and changes using:
- **Snapshots**, not diffs, for efficient version control.
- An **object database** consisting of blobs, trees, and commits, each identified by a unique **SHA-1 hash**.
- A **staging area** (index) that allows for controlled commits.
- **Branches** and **merges** to manage parallel workstreams.
- **Garbage collection** to clean up unused objects.

This structure ensures that Git is fast, scalable, and flexible, making it a popular choice for version control in software development.
