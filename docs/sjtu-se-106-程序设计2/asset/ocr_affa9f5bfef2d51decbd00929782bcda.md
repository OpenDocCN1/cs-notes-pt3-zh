# Comparisons

```
```cpp
// Different comparisons for Rec objects:

struct Cmp_by_name {
    bool operator()(const Rec& a, const Rec& b) const
        { return a.name < b.name; }        // look at the name field of Rec
};

struct Cmp_by_addr {
    bool operator()(const Rec& a, const Rec& b) const
        { return 0 < strncmp(a.addr, b.addr, 24); }        // correct?
};

// note how the comparison function objects are used to hide ugly
// and error-prone code
```
```