Now p has (⌈m/2⌉-2)+(⌈m/2⌉-1)+1=2⌈m/2⌉-2 ≤ m-1 keys. p is written to disk.

The number of keys in the parent, r, has been reduced by 1.

If r does not become deficient (i.e., it has at least 1 element if it is the root and ⌈m/2⌉-1 elements if it is not the root), the changed r is written to disk, done.

When r becomes deficient, if it is the root, it is discarded. Otherwise r has ⌈m/2⌉-2 keys, we can first attempt a rotation with one of its