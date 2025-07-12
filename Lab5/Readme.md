Wine Dataset Clustering Analysis: Hierarchical vs. DBSCAN
This project provides a Python script to perform and compare two popular unsupervised clustering algorithms—Agglomerative Hierarchical Clustering and DBSCAN—on the Wine dataset from sklearn.datasets.

Overview
The primary goal is to partition the Wine dataset into distinct clusters and evaluate the effectiveness of each algorithm. The script walks through data loading, preprocessing, model application, visualization, and evaluation.

Features
Data Preparation: Loads the Wine dataset, examines its structure with pandas, and standardizes features using StandardScaler.

Hierarchical Clustering:

Applies Agglomerative Hierarchical Clustering.

Generates and displays a dendrogram to help visualize the hierarchical structure and determine an optimal number of clusters.

Visualizes the resulting clusters with scatter plots for different n_clusters values.

DBSCAN Clustering:

Applies the DBSCAN algorithm.

Experiments with different eps and min_samples parameters to show their impact on cluster formation.

Visualizes the clusters and highlights noise points identified by the algorithm.

Evaluation:

Computes and reports key clustering metrics for DBSCAN:

Silhouette Score

Homogeneity Score

Completeness Score

Analysis: Includes an in-code text analysis comparing the strengths and weaknesses of each algorithm based on the results.

Requirements
To run this script, you need Python 3 and the following libraries:

numpy

pandas

scikit-learn

matplotlib

scipy

You can install them using pip:

pip install numpy pandas scikit-learn matplotlib scipy

How to Run
Save the code as a Python file (e.g., clustering_analysis.py).

Run the script from your terminal:

python clustering_analysis.py

The script will print the data examination, evaluation metrics, and analysis to the console. Matplotlib plots will be displayed for the dendrogram and cluster visualizations.
