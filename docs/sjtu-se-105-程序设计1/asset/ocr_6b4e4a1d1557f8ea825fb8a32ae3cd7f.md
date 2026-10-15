```
IntSet.java
package PolyJava;
public interface IntSet {
    public void insert(int v) throws IntSetException;
    // MODIFIES: this
    // EFFECTS: set = set + {v} if room, throws IntSetFull otherwise
    public void remove(int v) throws IntSetException;
    // MODIFIES: this
    // EFFECTS: set = set - {v}
    public boolean query(int v);
    // EFFECTS: returns true if v is in set, false otherwise
    public int size();
    // EFFECTS: returns |set|
    public IntSet getIntSet();
    // EFFECTS: returns instance of IntSet
}
```