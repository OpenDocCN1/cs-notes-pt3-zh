# BSP Tree

# Draw BSP Tree

```
function *draw*(bsptree *tree*, point *eye*)
if *tree.empty* then
    return
if *f*<sub>tree.root</sub>(*eye*) < 0
    draw (*tree.right*)
    rasterize(*tree.root*)
    draw(*tree.left*)
else
    draw (*tree.left*)
    rasterize(*tree.root*)
    draw(*tree.right*)
```

![](bbox=[0.454, 0.391, 0.924, 0.815])