# Backtrack algorithm for maxclique

```
void Maxclique(int n) {\n    // Backtracking code for traveling salesperson.\n    int i;\n    if (n == 0) { // at parent of leaf\n        // complete tours by adding last two edges\n        if (a[x[n-1]][x[n]] != 0edge &&\n            (x[n+1] != 0edge &&\n             (c + a[x[n-1]][x[n]] + a[x[n]][1] < bestc ||\n              bestc == 0edge))\n            bestc = c + a[x[n-1]][x[n]] + a[x[n]][1];\n    }\n    else { // try out subtrees\n        for (int j = 1; j <= n; j++) {\n            // see if edge is labeled x[j]\n            if (a[x[n-1]][x[j]] != 0edge &&\n                (c + a[x[n-1]][x[j]] +\n                 bestc == 0edge || c + a[x[n-1]][x[j]] < bestc)) {\n                // search this subtree\n                swap(x[n], x[j]);\n                c += a[x[n-1]][x[n]];\n                TSP(n-1);\n                c -= a[x[n-1]][x[n]];\n                swap(x[n], x[j]);\n            }\n        }\n    }\n}
```

```
template<class T>\nvoid maxclique(int n, TSP(int)) {\n    // Traveling salesperson\n    // Backtracking.\n\n    // Return cost of best tour,\n    // return 0 for n<=1.\n    if (n <= 1) return;\n    x[1] = 1;\n    // x is a density permutation\n    for (int i = 2; i <= n; i++)\n        x[i] = i;\n    bestc = 0;\n    // search whole array of vertices\n    TSP(n-1);\n    cc = 0;\n\n    // search permutations of x\n    TSP(2);\n\n    delete [] x;\n    return bestc;\n}
```