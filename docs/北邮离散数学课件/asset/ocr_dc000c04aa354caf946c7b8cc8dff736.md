# # Computing the Closest Pair of Points by Brute-Force

+   - Algorithm for finding the closest pair in a set of n points.

```
```
procedure closest pair((x₁,y₁), (x₂,y₂), …, (xₙ,yₙ): xᵢ, yᵢ real numbers)
min = ∞
for i := 1 to n
  for j := 1 to i
    if (xⱼ - xᵢ)² + (yⱼ - yᵢ)² < min
    then min := (xⱼ - xᵢ)² + (yⱼ - yᵢ)²
    closest pair := (xᵢ, yᵢ), (xⱼ, yⱼ)
return closest pair
```
```

+   - The algorithm loops through n(n−1)/2 pairs of points, computes the value (xⱼ−xᵢ)²+(yⱼ−yᵢ)² and compares it with the minimum, etc. So, the algorithm uses Θ(n²) arithmetic and comparison operations.

+   - We will develop an algorithm with O(log n) worst-case complexity in Section 8.3.