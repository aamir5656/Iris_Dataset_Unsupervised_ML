# Iris Dataset Clustering using KMeans (Unsupervised Learning)

This project demonstrates how to apply **unsupervised learning** to the well-known **Iris dataset** using the **KMeans clustering algorithm** from scikit-learn. The main objective is to group the flower data into clusters based only on their feature values (without using the actual labels).

> 📥 **Note:** This dataset was downloaded from **Kaggle** and is being used for **educational purposes** as a student practice project.

---

## 📚 Theory & Concepts

### ✅ What is Clustering?
Clustering is a type of unsupervised learning where the goal is to group similar data points into clusters. Unlike supervised learning, we don’t use target labels; instead, the algorithm finds patterns and structures in the data on its own.

### ✅ What is KMeans?
KMeans is a centroid-based clustering algorithm that aims to partition the dataset into **K distinct non-overlapping subgroups (clusters)**. It works by:

1. Choosing K initial cluster centers (centroids).
2. Assigning each point to the nearest cluster.
3. Recomputing the cluster centers.
4. Repeating steps 2 and 3 until convergence.

### ✅ Why Use Iris Dataset?
The Iris dataset is ideal for learning clustering because it contains 3 known classes (species), but we won’t use them during training. It has 150 rows and 4 numerical features:
- Sepal Length
- Sepal Width
- Petal Length
- Petal Width

---

## 📂 Dataset Preparation

1. **Import Data:**
   Load the Iris dataset using pandas.

2. **Drop the Label Column:**
   Since this is unsupervised learning, we remove the `species` column.

3. **Standardize the Features:**
   Use `StandardScaler` to bring all features to the same scale (mean = 0, std = 1).

---

## 📊 Visual Exploration

### Pairplot
A pairplot is created using seaborn to visualize the relationships between all feature pairs. This helps us see natural groupings and correlations in the data.

---

## 🔍 Finding the Optimal Number of Clusters

### Elbow Method
We run KMeans for cluster values from 1 to 20 and calculate WCSS (Within-Cluster Sum of Squares). A plot of WCSS vs cluster count shows an "elbow point," where adding more clusters doesn't significantly reduce WCSS.

### KneeLocator
We use the `kneed` library to detect the elbow point programmatically. However, sometimes it may return a slightly off value due to curve shape. In this project:
- **KneeLocator returns 4**
- **Visual inspection suggests 3 (which matches the actual species)**

> In real-world projects, it's often better to trust **visual analysis + domain knowledge** over automatic tools when they disagree.

---

## 📊 Apply KMeans Clustering

We apply KMeans using `n_clusters=3`, fit it to the dataset, and assign the resulting labels as a new column `predict`.

Another pairplot is created using this predicted cluster label to visually inspect how well the algorithm grouped the data.

---

## 🤝 Comparing with Actual Species

Even though the model didn't use species labels during training, we compare the predicted clusters with the original class distribution. The results are close, indicating that KMeans successfully discovered the natural grouping in the data.

---

## 🔹 Conclusion

- KMeans can effectively cluster the Iris dataset without using the labels.
- Visual elbow method is more reliable in this case than automated KneeLocator.
- The results are close to the actual species, showing the power of unsupervised learning.

---

## 📅 Future Improvements

- Use **Silhouette Score** for more accurate cluster evaluation.
- Try other clustering algorithms like **DBSCAN** or **Hierarchical Clustering**.
- Apply PCA to reduce dimensionality and visualize in 2D.

---

This project is a basic but powerful example of applying unsupervised learning to a well-known dataset. Great for beginners exploring clustering concepts.

