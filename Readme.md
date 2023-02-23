<h1>K-means for Higher Dimensional Data using minkowski distance</h1>
<h2> Introduction </h2>

Clustering can be defined as the task of identifying subgroups in the data such that data points in the same
subgroup (cluster) are very similar while data points in different clusters are very different. One of the most
classical algorithm for clustering a data set is K-Means algorithm (also known as Lloyd’s Algorithm). Tradi-
tionally, Euclidean distance is used as a measure to determine the similarity between any two points(the lesser
the distance the more similar the 2 points are to each other), but here we have used Minkowski distance( L-k
Norm distance) as a measure of similarity between any two points. We have used some higher dimensional
datasets( of dimension >= 32) as test cases for testing our algorithm and the corresponding results of the same
have been attached below as well.
The quality of a clustering algorithm can be decided based on the dissimilarity or similarity metric, i.e. the
inter and intra cluster distance of the various clusters. Since the main aim of clustering is to group together the
data points which are most similar to each other and to separate the most dissimilar ones. Silhouette Index is
one such measure that takes into consideration both the intra and inter cluster distance to measure the quality
of the clusters formed from a given dataset.
The Silhouette Index is defined as below :-

```
S(o) = (a(o)−b(o))/max(a(o), b(o))
```
where 
- S(o) is the silhouette coefficient of the data point o.
- a(o) is the average distance between o and all the other data points in the cluster to which o belongs.
- b(o) is the minimum average distance from o to all clusters to which o does not belong.

## Algorithm

```
1 Initialize k centroids with random values
2
3   for i in range(iterations):
4     iterate through the items:
5     Find the closest centroid to the item and label it accordingly
6     Update the mean by recalculating the mean centroids using all the points in a particular label
```


  <h2> Difficulties we ran into and some observations </h2>

```
1.Figuring out the initialisation of centroids:For the clustering algorithm to work correctly we need
to have the initial centroids estimation in the correct cluster regions. As this is done randomly using
pseudo-random generators in python, the selection of seed becomes crucial. To solve this we implemented
KMeans++ initialisation method which is the standard which sklearn itself uses. However for 2D data
we still notice inaccuracy in centroid estimation arising from precision in python operations. However for
higher dimension dataset we couldn’t confirm much the validity of the implementation as the dataset had
well defined clusters.
```
```
2.Finding metrics which highlights the changes for the same dataset and different value of p
in l-p norm: All defined standard metrics usually focus on the quality of clustering and would yield
similar results. With increase in the value of p other than intra cluster distances, we were unable to find
metrics which supported any observation we can claim as we increased p.
```
## GitHub Link

Please visit this for the source code.
https://github.com/MnCSSJ4x/Clustering-Project

## References

1.http://cs.uef.fi/sipu/datasets/dim032.txt(32 dimensional dataset)

2.http://cs.uef.fi/sipu/datasets/dim064.txt(64 dimesional dataset)

3.http://cs.uef.fi/sipu/datasets/dim128.txt(128 dimensional dataset)

4.http://cs.uef.fi/sipu/datasets/dim256.txt(256 dimensional dataset)

5.http://cs.uef.fi/sipu/datasets/dim512.txt(512 dimensional dataset)

6.http://cs.uef.fi/sipu/datasets/dim1024.txt(1024 dimensional dataset)

7.https://en.wikipedia.org/wiki/K-means_clustering

8. Documentation of the APIs used in the code (i.e. scipy, numpy, scikit, panda, matplotlib and sklearn).

9.https://medium.com/@cmukesh8688/silhouette-analysis-in-k-means-clustering-cefa9a7ad

