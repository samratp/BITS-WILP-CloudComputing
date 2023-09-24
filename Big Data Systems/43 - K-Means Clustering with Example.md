K-Means clustering is an unsupervised machine learning algorithm used for partitioning a dataset into K distinct, non-overlapping subsets (clusters). Each data point belongs to the cluster with the nearest mean, serving as a prototype of the cluster.

Here's a step-by-step explanation of how K-Means works, along with an example:

### Step 1: Initialization

1. **Choose the number of clusters (K)**: Decide how many clusters you want to divide your data into. This is a hyperparameter that you need to specify in advance.

2. **Initialize cluster centroids**: Randomly select K data points from the dataset and set them as the initial centroids. These points will serve as the starting points for each cluster.

### Step 2: Assignment

3. **Assign each data point to the nearest centroid**: For each data point in the dataset, calculate the distance (e.g., Euclidean distance) to each of the K centroids. Assign the data point to the cluster whose centroid is closest.

### Step 3: Update

4. **Update centroids**: Once all data points have been assigned to clusters, recalculate the centroids by computing the mean of all data points in each cluster. These new centroids serve as the updated cluster centers.

### Step 4: Repeat Assignment and Update

5. **Iterate Steps 2 and 3**: Repeat the assignment and update steps until a stopping criterion is met. This could be a fixed number of iterations, or until the centroids no longer change significantly.

### Example:

Let's work through a simple example with a small dataset. We'll use K=2 for simplicity.

**Dataset**:
```
Data Points: [2, 4, 10, 12, 3, 20, 30, 11, 25]
```

**Initialization**:

Randomly select two initial centroids, let's say `Centroid1 = 4` and `Centroid2 = 10`.

**Assignment**:

Assign each data point to the nearest centroid:

- Data Points: `[2, 4, 10, 12, 3, 20, 30, 11, 25]`
- Cluster 1 (Centroid 4): `[2, 4, 3]`
- Cluster 2 (Centroid 10): `[10, 12, 20, 30, 11, 25]`

**Update**:

Recalculate centroids:

- New Centroid 1: `mean([2, 4, 3]) = 3` 
- New Centroid 2: `mean([10, 12, 20, 30, 11, 25]) = 17.67` (rounded to 2 decimal places)

**Assignment and Update (Iteration 2)**:

Reassign data points and update centroids:

- Cluster 1 (Centroid 3): `[2, 4, 3]`
- Cluster 2 (Centroid 17.67): `[10, 12, 20, 30, 11, 25]`

New Centroids:

- New Centroid 1: `mean([2, 4, 3]) = 3`
- New Centroid 2: `mean([10, 12, 20, 30, 11, 25]) = 17.67`

Since there is no change in centroids after the second iteration, the algorithm converges and stops.

**Final Clusters**:

- Cluster 1: `[2, 4, 3]`
- Cluster 2: `[10, 12, 20, 30, 11, 25]`

This is a simplified example, but it illustrates the basic steps of the K-Means algorithm. In practice, the algorithm is often run for multiple iterations until convergence and may use more advanced initialization techniques.
