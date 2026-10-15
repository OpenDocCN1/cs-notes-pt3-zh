# Policy parameterization

+   - Whenever you have a useful algorithm, you eventually want to parameterize it by a “policy”.
+     - For example, we need to parameterize sort by the comparison criteria

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