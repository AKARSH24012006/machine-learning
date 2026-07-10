K-Means Clustering
What is K-Means?

K-Means is an Unsupervised Machine Learning Algorithm.

Since it is unsupervised,

there are no labels.

Example:

Customer	Age	Salary
A	22	30000
B	23	32000
C	50	90000
D	48	85000

There is no column like

Young

Old

The algorithm itself finds groups.

Why is it called K-Means?

Two parts:

K

Means the number of clusters.

Example

K = 2

Two clusters.

K = 5

Five clusters.

Means

Means Centroid.

A centroid is simply the average point of a cluster.

Suppose

(2,4)

(4,6)

(6,8)

Centroid

((2+4+6)/3,
 (4+6+8)/3)

=

(4,6)

So,

K-Means means

Find K centroids and assign every point to its nearest centroid.

Real Life Example

Suppose a shopping mall has customer data.

Age

Income

Plot:

High Income

      ● ● ●

      ● ●

------------------------

● ● ●

● ●

Low Income

Without knowing anything,

K-Means automatically says

Group 1

Group 2

Useful for

Marketing
Offers
Customer segmentation
Main Idea

Imagine

10 students

Need

3 groups

K-Means repeatedly performs

Guess centers

↓

Assign points

↓

Move centers

↓

Assign again

↓

Move again

↓

Repeat

↓

Stop
How K-Means Works

Suppose

K = 2

Data

A

B

C

D

E

F
Step 1

Choose K random centroids.

Example

●

          ●

Random.

Step 2

Compute distance from every point to every centroid.

Suppose

Point A

Distance

Centroid1 = 2

Centroid2 = 8

Nearest

Centroid1

So

Assign A to Cluster 1.

Point E

Centroid1 = 10

Centroid2 = 2

Assign to Cluster 2.

Now

Cluster1

A

B

C

Cluster2

D

E

F
Step 3

Move the centroid.

Calculate average.

Suppose Cluster1

(2,3)

(3,4)

(4,5)

New centroid

(3,4)

Centroid moves.

Step 4

Assign again.

Some points change clusters.

Step 5

Again calculate average.

Move centroid.

Repeat until

Centroids stop moving.

Visualization

Initially

X    X


          O

X

             O

       X

O = centroid

Assign clusters

Cluster1

X

X

Cluster2

X

X

Move centroid

Repeat.

Eventually

Cluster1

XXXXX

Cluster2

XXXXX

Done.

K-Means Algorithm
Choose K

↓

Initialize K centroids randomly

↓

Assign every point

↓

Compute new centroids

↓

Repeat

↓

Centroids stop changing

↓

Finished
Distance Used

Usually

Euclidean Distance

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

A=(1,1)

B=(4,5)

Distance

√((4-1)^2+(5-1)^2)

=5
Centroid Formula

Suppose

Cluster

(2,4)

(6,8)

(4,6)

Centroid

x

=

(2+6+4)/3

=4

y

=

(4+8+6)/3

=6

Centroid

(4,6)
Objective Function ⭐⭐⭐

K-Means minimizes

Within-Cluster Sum of Squares (WCSS)

Also called

Inertia
SSE (Sum of Squared Errors)

Formula

∑∣∣x
i
	​

−μ∣∣
2

Meaning

Every point should be as close as possible to its centroid.

Smaller WCSS

↓

Better clustering.

How to Choose K?

Most important question.

Answer:

Elbow Method ⭐⭐⭐⭐⭐

Example

K	WCSS
1	800
2	500
3	220
4	180
5	160
6	150

Graph

WCSS

800 *

600 *

400 *

250 *

200      *

180        *

160          *

------------------------
1 2 3 4 5 6

Notice

Huge drop

Until

K=3

After that

Very little improvement.

Looks like an elbow.

Choose

K=3
Silhouette Score ⭐⭐⭐⭐

Another method.

Range

-1

to

1

Near

1

Very good clusters.

Near

0

Overlapping clusters.

Negative

Bad clustering.

Advantages

✅ Easy

✅ Fast

✅ Scalable

✅ Works well on large datasets

✅ Easy to understand

Disadvantages

❌ Must choose K beforehand.

❌ Sensitive to outliers.

❌ Different random initial centroids can produce different results.

❌ Works best with roughly spherical, similarly sized clusters.

Time Complexity
O(n×k×i×d)

where:

n = number of samples
k = number of clusters
i = number of iterations until convergence
d = number of features
Real Applications
Customer segmentation
Image compression
Market basket analysis
Recommendation systems
Fraud detection
Medical data grouping
News article clustering
Social media user analysis