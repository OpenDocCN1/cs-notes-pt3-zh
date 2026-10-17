# # Motivations

Let’s consider the 0/1 knapsack problem, its state space can be expanded in two ways using fixed length tuple representation of solution space: (n=4,c=7,p=[4,7,9,10], w=[1,2,3,5])

![](bbox=[0.1, 0.3, 0.9, 0.55])

Using DFS:

+   - E- node produces one child at a time

+   - It needs O(n)space to store live nodes