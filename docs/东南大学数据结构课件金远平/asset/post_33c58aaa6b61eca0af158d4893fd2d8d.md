
![](img/15e8d7d94d8ddf02cb6839870195a31e_272_0.png)

| Level | p | level | p | level | p | level | p |
|---|---|---|---|---|---|---|---|
| 1 | b | 1 | b | 5 | x | 3 | u |
| 2 | s | 2 | r | 4 | w | 2 | r |
| 3 | t | 3 | u | 3 | u | 3 | 0 |
| 4 | 0 | 4 | w | 4 | v | 2 | r |
| 3 | t | 5 | x | 5 | 0 | 1 | b |
| 2 | s | 6 | 0 | 4 | v |  |  |

## 4.10.2.2 List Equality

Two lists are identical if they have the same structure and the same data in corresponding data members.

### Equal

```
// Driver
template <class T>
bool GenList<T>::operator==(const GenList<T>& l) const
{ // *this and l are non-recursive lists
// returns true if the two lists are identical.
return Equal(first, l.first);
}
```

```
//Workhorse– assume to be a friend of GenListNode
template <class T>
bool Equal(GenListNode<T>* s, GenListNode<T>* t)
{
    if ((!s) && (!t)) return true;
    if ( s && t && (s->tag == t->tag) )
        if (s->tag)
            return Equal(s->down, t->down)
                && Equal(s->next, t->next);
        else return (s->data == t->data)
                && Equal(s->next, t->next);
    return false;
}
```

## Computing time:

No more than linear when no sublists are shared.
Note if a sublist is shared, it may be visited many times.

Note the algorithm terminates as soon as it discover two lists are not identical.

## 4.10.2.3 List Depth

Depth(s)= { 0 if s is an atom or empty list 1+max{depth(x₀),..., depth(xₙ₋₁)} if s is the list (x₀, ... , xₙ₋₁) n≥0 }

### Depth

```
// Driver
template <class T>
int GenList::Depth()
{ // compute the depth of a non-recursive list
    return Depth(first);
}
```

## 4.10.3 Reference Counts,Shared and Recursive Lists

Sharing of sublists:

- saving storage.
- consistency.

To facilitate specification, extend the definition of a list to allow for naming of sublist. E.g.: A=(a, (b,c)), Z=(b,c) ➔ A=(a, Z(b, c)) and to be consistent, A is written as A(a, Z(b, c)).

## Problems with lists sharing:

- (1) Refer to the Fig. on the slide 93, if the first node of B is deleted, the pointers from C should be updated, but normally we do not know all the pointers from which a particular list is being referenced. --- solution: head node.
- (2) How to determine whether or not the lists nodes may be actually freed? --- solution: reference counts, using the head node. The reference count of a list is the number of pointers to it.

## We need some change in the class GenListNode:

```
template <class T>
class GenListNode<T> {
friend class GenList<T>;
private:
    GenListNode<T> *next;
    int tag; // 0 for data, 1 for down, 2 for ref
    union {
        T data;
        GenListNode<T> *down;
        int ref;
    };
};
```

With head node, lists A= (), B = (a, (b, c)), C = (B, B, ()) and D = (a, D) will be represented as in the next slide.

a.first

A=0

b.first

B=(a, (b.c))

c.first

C=(B, B, ())

d.first

D=(a, D)

Now the ideas of erasing list:
Decrement the reference count by 1, if it becomes 0, then examining the top level nodes, any sublists encountered are erased and finally, the top level nodes are linked into the av list.

```
~GenList
// Driver
template <class T>
GenList::~GenList()
{ // Each head node has a reference count.
    if (first) { Delete(first); first = 0;}
}
```

```
// Workhorse
template <class T>
void GenList<T>::Delete(GenListNode<T>* x)
{
    x->ref--; // decrement reference count of the head node
    if (!x->ref)
    {
        GenListNode<T>* y=x; // y traverses top level of x.
        while (y->next) {
            y=y->next;  if (y->tag==1) Delete(y->down);
        }
        y->next = av;
        av = x;
    }
}
```

Refer to slide 106, a call to b.~GenList( ) makes:

- ref(b)→2. After that

A call to c.~GenList( ) results in:

- ref(c)→0, ref(b)→1→0.
- all the six nodes of B(a, (b, c)) returned to av list.
- the empty list node of C(B, B, ()) returned to av.
- the top level nodes of c returned to av.
