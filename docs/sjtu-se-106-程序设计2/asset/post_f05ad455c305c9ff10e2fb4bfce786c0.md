
## Algorithms and iterators

- An iterator points to (refers to, denotes) an element of a sequence
- The end of the sequence is “one past the last element”
  - *not* “the last element”
  - That’s necessary to elegantly represent an empty sequence
  - One-past-the-last-element isn’t an element
    - You can compare an iterator pointing to it
    - You can’t dereference it (read its value)
- Returning the end of the sequence is the standard idiom for “not found” or “unsuccessful”

![](img/af430dff16b82a0fe61ce7dee05dcf9c_164_0.png)

## Predicates

- A predicate (of one argument) is a function or a function object that takes an argument and returns a `bool`
- For example
  - A function

```cpp
bool odd(int i) { return i % 2; } // % is the remainder (modulo) operator
odd(7);                            // call odd: is 7 odd?
```

  - A function object

```cpp
struct Odd {
    bool operator()(int i) const { return i % 2; }
};

Odd odd;        // make an object odd of type Odd
odd(7);         // call odd: is 7 odd?
```

## Function objects

- A concrete example using state

```
template<class T> struct Less_than {
    T val;     // value to compare with
    Less_than(int x) : val(x) { }
    bool operator()(const T& x) const { return x < val; }
};

// find x < 43 in vector<int>:
p=find_if(v.begin(), v.end(), Less_than(43));

// find x “perfection” in list<string>:
q=find_if(ls.begin(), ls.end(), Less_than("perfection"));
```

## Function objects

- A very efficient technique
  - inlining very easy
    - and effective with current compilers
  - Faster than equivalent function
    - And sometimes you can't write an equivalent function
- The main method of policy parameterization in the STL
- Key to emulating functional programming techniques in C++

## Policy parameterization

- Whenever you have a useful algorithm, you eventually want to parameterize it by a “policy”.
  - For example, we need to parameterize sort by the comparison criteria

```
struct Record {
  string name;      // standard string for ease of use
  char addr[24];    // old C-style string to match database layout
  // ...
};

vector<Record> vr;
// ...
sort(vr.begin(), vr.end(), Cmp_by_name());    // sort by name
sort(vr.begin(), vr.end(), Cmp_by_addr());    // sort by addr
```

## Comparisons

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

## vector

```
template<class T> class vector {
    T* elements;
    // ...
    typedef ??? iterator; // the type of an iterator is implementation defined
    // and it (usefully) varies (e.g. range checked iterators)
    // a vector iterator could be a pointer to an element

    typedef ??? const_iterator;

    iterator begin();                // points to first element
    const_iterator begin() const;
    iterator end();                  // points one beyond the last element
    const_iterator end() const;

    iterator erase(iterator p);      // remove element pointed to by p
    iterator insert(iterator p, const T& v); // insert a new element v before p
};
```

## erase() from vector

```
p = v.erase(p); // leaves p pointing at the element after the erased one
```

- vector elements move when you insert() or erase()
- Iterators into a vector are invalidated by insert() and erase()

![](img/af430dff16b82a0fe61ce7dee05dcf9c_173_0.png)
