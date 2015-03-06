distributeRF: Splitting and Merging Random Forest Analysis and Results
========================================================

A random forest [Breiman:2001] is grown by _bagging_ [Breiman:1996] a collection of _classification and regression trees_ (CART) [cart:1984]. The method uses a set of $B$ bootstrap [bootstrap:1994] samples, growing an independent tree model on each sub-sample of the population. Each tree is grown by recursively partitioning the population based on optimization of a _split rule_ over the $p$-dimensional covariate space. At each split, a subset of $m \le p$ candidate variables are tested for the split rule optimization, dividing each node into two daughter nodes. Each daughter node is then split again until the process reaches the _stopping criteria_ of either _node purity_ or _node member size_, which defines the set of _terminal (unsplit) nodes_ for the tree. In regression trees, the split rule is based on minimizing the mean squared error, whereas in classification problems, the Gini index is used [Friedman:2000].

Random Forests sort each training set observation into one unique terminal node per tree. Tree estimates for each observation are constructed at each terminal node, among the terminal node members. The Random Forest estimate for each observation is then calculated by aggregating, averaging (regression) or votes (classification), the terminal node results across the collection of $B$ trees.

With careful random number seeding, it should be possible to grow multiple independent random forest models. If the models are independent, then prediction for a single observation can be obtained by averaging the prediction over all forests. Since variable importance, minimal depth, variable dependence and partial dependence are also averaging operations, they can be obtained over an aggregate of multiple forest models. 

This package contains functions growing a series of random forest models and aggregating the results from this process. 

## References

Breiman, L. (2001). Random forests, Machine Learning, 45:5-32.

Ishwaran H. and Kogalur U.B. (2014). Random Forests for Survival,
Regression and Classification (RF-SRC), R package version 1.5.5.

Ishwaran H. and Kogalur U.B. (2007). Random survival forests for R. R News
7(2), 25--31.

Ishwaran H., Kogalur U.B., Blackstone E.H. and Lauer M.S. (2008). Random
survival forests. Ann. Appl. Statist. 2(3), 841--860.

Wickham, H. ggplot2: elegant graphics for data analysis. Springer New York, 2009.


