To describe these, we define a value low for each w∈V(G), as:

low(w)=min { dfn(w),
    min { low(x) | x is a child of w },
    min { dfn(x) | (w, x) is a back edge }
}

Thus u is an articulation point iff u is either the root of the spanning tree and has two or more children or u is not the root and u has a child w such that low(w)≥dfn(u).