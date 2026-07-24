What does XGBoost mean?

X = Extreme

Gradient Boosting = A boosting algorithm

So,

XGBoost = Extreme Gradient Boosting

It is simply a highly optimized version of Gradient Boosting.

Why was XGBoost created?

Normal Gradient Boosting has some problems:

Slow training
Overfitting
Doesn't utilize hardware efficiently
Doesn't handle missing values well

XGBoost fixes all of these.

Advantages
Very fast
Highly accurate
Built-in regularization
Handles missing values
Parallel processing
Early stopping
Feature importance
Works well with large datasets
Main Idea

Instead of making one huge decision tree,

XGBoost builds many small trees.

Every new tree learns from the mistakes of previous trees.

Example

Tree 1

Predicts

80%

Mistakes remain.

↓

Tree 2

Learns only those mistakes.

↓

Tree 3

Corrects remaining mistakes.

↓

Tree 4

Again corrects errors.

Eventually,

Final Prediction

=
Tree1
+
Tree2
+
Tree3
+
Tree4
...
Difference

Decision Tree

One tree

Random Forest

Many independent trees
Average prediction

Gradient Boosting

Trees built one after another

XGBoost

Gradient Boosting
+
Optimization
+
Regularization
+
Speed
+
Parallelization
Important Parameters

These are the parameters you will use the most.

1. n_estimators

Number of trees.

Example

n_estimators=100

Means

100 trees

Higher value

Better learning

↓

Longer training

↓

Possible overfitting
2. learning_rate

How much each tree contributes.

Example

learning_rate=0.1

Large value

Fast learning

May overfit

Small value

Slow learning

Better accuracy
3. max_depth

Maximum depth of each tree.

Example

max_depth=6

Small depth

Simple model

Large depth

Complex model

Can overfit
4. subsample

Fraction of training samples used for each tree.

Example

subsample=0.8

Means

Each tree sees only

80%

of data

Helps reduce overfitting.

5. colsample_bytree

Fraction of features used for each tree.

Example

colsample_bytree=0.8

Means

Each tree uses

80%

of columns
6. gamma

Minimum improvement required before splitting.

Large gamma

Less splitting

Simpler trees

Small gamma

More splitting
7. reg_alpha

L1 Regularization.

Removes unnecessary complexity.

8. reg_lambda

L2 Regularization.

Prevents overfitting.