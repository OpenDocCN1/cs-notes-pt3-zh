# Naïve Bayesian Classifiers

+   - Bayesian classifiers require
+     - computation of $p(d \mid c_j)$
+     - precomputation of $p(c_j)$
+     - $p(d)$ can be ignored since it is the same for all classes
+   - To simplify the task, **naïve Bayesian classifiers** assume attributes have independent distributions, and thereby estimate
+     $p(d \mid c_j) = p(d_1 \mid c_j) * p(d_2 \mid c_j) * ... * (p(d_n \mid c_j)$
+     - Each of the $p(d_i \mid c_j)$ can be estimated from a histogram on $d_i$ values for each class $c_j$
+       - the histogram is computed from the training instances
+     - Histograms on multiple attributes are more expensive to compute and store