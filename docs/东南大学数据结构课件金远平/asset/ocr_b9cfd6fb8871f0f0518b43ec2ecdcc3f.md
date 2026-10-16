# Definition: An m-way search tree, either is empty or satisfies the following properties:

+   (1) The root has at most m subtrees and has the following structure:
+   
+   n, A₀, (E₁, A₁), (E₂, A₂), ..., (Eₙ, Aₙ)
+   
+   where the Aᵢ, 0≤i≤n<m, are pointers to subtrees, and Eᵢ, 1≤i≤n<m, are elements. Each Eᵢ has a key Eᵢ.K.

+   (2) Eᵢ.K < Eᵢ₊₁.K, 1≤i<n.

+   (3) Let E₀.K = -∞ and Eₙ₊₁.K = ∞. All key values in subtree Aᵢ are less than Eᵢ₊₁.K and greater than Eᵢ.K, 0≤i≤n.

+   (4) The subtrees Aᵢ, 0≤i≤n, are also m-way search trees.