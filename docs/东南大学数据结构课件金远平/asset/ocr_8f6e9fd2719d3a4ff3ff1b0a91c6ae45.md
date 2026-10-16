```
void Chain::Insert50 (ChainNode *x)
{
    if (first)
        // insert after x
        x→link = new ChainNode(50, x→link);
    else
        // insert into empty chain
        first = new ChainNode(50);
}
```

Exercises: P183-1,2