# # Backtrack algorithm for Knapsack

```
```cpp
template<class Tv, class Tp>
void KnapTv, Tp>::Knapsack(int i)
{ // Search the i - th node
    if (i > n) { // Leaf node
        bestp = cp;
        return;
    }
    if (remainweight >= w[i])
    { // Left subtree
        x[i] = 1; // try x[i] = 1
        cp += v[i];
        remainweight -= w[i];
        Knapsack(i + 1);
    }
    if (Bound(i + 1) > bestp) // try x[i] = 0
        Knapsack(i + 1);
}
```
```

```
```cpp
template<class Tv, class Tp>
Tp Knap<Tv, Tp>::Bound(int i)
{ // Return upper bound on value of
  // best leaf in i - subtree
    Tp c = cp; // remaining
    Tp bound = c; // profit bound
    while (i <= n && c + w[i] <= W)
    { // fill node of profit density
        c -= w[i];
        bound += v[i];
        i++;
    }
    if (i <= n)
        bound += (W - c) * p[i] / w[i];
    return bound;
}
```
```

# ## NEW

Assumed that items have been sorted by the profit density \(\left(\frac{p_i}{w_i}\right)\)