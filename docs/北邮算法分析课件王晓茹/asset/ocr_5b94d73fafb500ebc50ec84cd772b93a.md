```
template < class Type > class HeapNode
class bbnode
{
    friend void AddLiveNode( MaxHeap < HeapNode <int >> &, bbnode *, int, bool, int );
    friend int MaxLoading ( int *, int, int, int *);
    firend class AdjacencyGraph;
    private:
        bbnode *parent;
        bool LChild;
};
```

```
Temple < class Type>
class HeapNode
{
    frined void AddLiveNode( MaxHeap <HeapNode < Type >>&, bbnode *, Type, bool, int );
    friend Type MaxLoading( Type *, Type , int, int *);
    public:
        operator Type () const { return uweight; }
    private:
        bbnode *ptr;
        Type uweight;
        int level;
};
```