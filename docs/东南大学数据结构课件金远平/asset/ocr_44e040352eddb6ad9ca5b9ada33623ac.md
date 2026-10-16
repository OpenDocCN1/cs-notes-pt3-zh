# ADT 5.3

```
template <class K, class E>
class Dictionary {
public:
    virtual bool IsEmpty () const = 0;
        // return true iff the dictionary is empty
    virtual pair<K,E>* Get(const K&) const = 0;
        // return pointer to the pair with specified key;
        // return 0 if no such pair
    virtual void Insert(const pair<K,E>&) = 0;
        // insert the given pair; if key is a duplicate
        // update associated element
    virtual void Delete(const K&) = 0;
        // delete pair with specified key
};
```