```
// Insert element x into a disk resident B-tree.
Search the B-tree for an element E with key x.K;
if such an E is found, replace E with x and return;
else let p be the leaf into which x is to be inserted;
q = NULL;
for (e=x; p; p=p→parent())  // the parent of root is NULL
{ // (e, q) is to be inserted into p
    Insert (e, q) into appropriate position in node p;
    Let the resulting node have the form:
                    n, A₀, (E₁, A₁), ..., (Eₙ, Aₙ);
    if (n<=m-1) {  // the resulting node is not too big
        write node p to disk; return;
    }
}
```