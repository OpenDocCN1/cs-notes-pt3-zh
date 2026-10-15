# 子类不是子类型

```
class PosIntSet : public IntSet {
    // OVERVIEW: a subclass, but not a subtype
public:
    void insert(int v);
    // EFFECTS: if v is non-negative and s has room to include it, s=s+{v}
    // if v is negative throw int -1; if s is full thrown int MAXELTS
};

void PosIntSet::insert(int v) {
    if (v < 0) throw -1;
    IntSet::insert(v);
}
```