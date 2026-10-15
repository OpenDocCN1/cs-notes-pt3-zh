# The hashmap.h Interface

```
/*
 * Method: put
 * Usage: map.put(key, value);
 * --------------------------------
 * Associates key with value in this map.  Any previous value associated
 * with key is replaced by the new value.
 */
    void put(KeyType key, ValueType value);

/*
 * Method: get
 * Usage: ValueType value = map.get(key);
 * --------------------------------
 * Returns the value associated with key in this map.  If key is not
 * found, the get method signals an error.
 */
    ValueType get(KeyType key);

/*
 * Method: containsKey
 * Usage: if (map.containsKey(key)) . . .
 * --------------------------------
 * Returns true if there is an entry for key in this map.
 */
    bool containsKey(KeyType key);
```