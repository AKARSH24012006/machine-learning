Agglomerative Hierarchical Clustering
What is Hierarchical Clustering?

Hierarchical Clustering is an Unsupervised Machine Learning algorithm.

Remember:

Supervised → Data has labels
Unsupervised → No labels

Example:

Student	Height	Weight
A	170	65
B	172	67
C	155	50
D	158	52

No labels.

The algorithm itself finds groups.

Why is it called Hierarchical?

Because it creates a tree-like hierarchy of clusters.

Imagine family tree.

                All Data
              /          \
        Cluster A      Cluster B
        /      \        /      \
      A        B      C        D

This tree is called a Hierarchy.

Two Types

There are only two.

1. Agglomerative (Bottom-Up)

Start with

A

B

C

D

Every point is its own cluster.

Gradually merge.

A  B   C   D

↓

AB   C   D

↓

AB   CD

↓

ABCD

Small → Big

Bottom → Top

This is the one used most.

2. Divisive (Top-Down)

Opposite.

ABCD

↓

AB   CD

↓

A B C D

Starts with one cluster and divides.

Rarely used.

Most libraries mainly implement Agglomerative.

Intuition

Suppose you have

A

B

C

D

Coordinates

A = (1,1)

B = (2,2)

C = (9,9)

D = (10,10)

Clearly

A and B are close.

C and D are close.

Algorithm:

Initially

A

B

C

D

Step 1

Nearest clusters

A and B

Merge

AB

C

D

Step 2

Nearest

C and D

Merge

AB

CD

Step 3

Merge both

ABCD

Finished.

Main Idea

Agglomerative clustering repeatedly performs

Find nearest clusters

↓

Merge them

↓

Repeat

Until

desired clusters reached
OR
everything becomes one cluster.
Visual
Initially

A

B

C

D

↓

Merge nearest

AB

C

D

↓

Merge nearest

AB

CD

↓

Merge

ABCD
Biggest Question

How do we decide

Which clusters are nearest?

This is where Linkage comes.

Linkage Methods

Very important.

Interview favorite.

There are four major ones.

1. Single Linkage

Uses

Minimum distance.

Cluster 1

A

B

Cluster 2

C

D

Distances

A-C = 7

A-D = 8

B-C = 5

B-D = 6

Minimum = 5

Single linkage distance = 5

Formula

min(distance)

Think

Closest friends.

Advantage

Can detect irregular shapes.

Disadvantage

Chain effect.

A----B----C----D----E

Everything becomes one cluster.

2. Complete Linkage

Uses

Maximum distance.

Formula

max(distance)

Example

5
7
9
4

Maximum

9

Ensures every point is close.

Creates compact clusters.

3. Average Linkage

Uses

Average.

Formula

(sum of distances)
/ total

Most balanced.

4. Ward Linkage ⭐⭐⭐

Most important.

Default in many implementations.

Instead of distances,

it merges clusters that produce the smallest increase in variance (within-cluster sum of squares).

Think

"Merge the pair that keeps clusters as compact as possible."

Usually gives the best-looking spherical clusters.

Comparison
Linkage	Uses
Single	Minimum distance
Complete	Maximum distance
Average	Mean distance
Ward	Minimum increase in variance
Distance Metrics

How is distance calculated?

Usually Euclidean.

Formula

(x
2
	​

−x
1
	​

)
2
+(y
2
	​

−y
1
	​

)
2
	​


Example

(1,1)

(4,5)

Distance

√((4-1)^2+(5-1)^2)

=√25

=5

Other metrics:

Manhattan
Cosine
Minkowski

Most common

Euclidean

Dendrogram ⭐⭐⭐⭐⭐

This is the heart of hierarchical clustering.

A dendrogram is simply a tree showing how clusters were merged.

Example

|

|          ______C
|         |
|    _____|
|   |     |______D
|___|
|   |______A
|
|__________B

Height = distance at which merge happened.

Suppose

A and B merge at distance 1

C and D merge at distance 2

Both merge at distance 8
8        ________
        |        |

2    ____|        |

     |    |       |

1    |   A B     C D

-------------------------

Large height

Means clusters were very different.

How to Decide Number of Clusters?

Using the dendrogram.

Draw a horizontal line.

Example

          |
          |
    ------- ← cut here

   /       \

AB          CD

You get

2 clusters

If cut lower

A

B

CD

Three clusters.

Rule:

Cut where there is the biggest vertical gap.

Algorithm

Step 1

Every point becomes its own cluster.

n points

↓

n clusters

Step 2

Compute pairwise distances.

Step 3

Find nearest clusters.

Step 4

Merge them.

Step 5

Update distances.

Step 6

Repeat.

Time Complexity

Naive implementation:

O(n³)

Memory:

O(n²)

Much slower than algorithms like K-Means for large datasets.

Suitable for:

Small datasets
Medium datasets

Not ideal for millions of points.

Advantages

✅ No need to specify clusters beforehand (if using a dendrogram).

✅ Easy to visualize.

✅ Works well for small datasets.

✅ Can capture hierarchical relationships.

Disadvantages

❌ Slow.

❌ High memory usage.

❌ Sensitive to noise and outliers.

❌ Cannot undo a wrong merge.

Real Applications
Customer segmentation
Document clustering
Gene analysis
Image segmentation
Recommendation systems
Social network analysis
Anomaly detection (small datasets)