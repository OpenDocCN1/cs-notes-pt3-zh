# Additionally, we add the following public member functions to Chain:

ChainIterator begin() { **return** ChainIterator(first);}

ChainIterator end() { **return** ChainIterator(0);}

# We may initialize an iterator object yi to the start of a chain of integers y using the statement:

```
Chain<int>::ChainIterator yi = y.begin();
```

# And we may sum the elements in y using the statement:

```
sum = accumulate(y.begin(), y.end(), 0);
```

```
// note sum does not require access to private members
```