# Ways of traversing a vector

```
```cpp
for(int i = 0; i<v.size(); ++i)              // why int?
    ...  // do something with v[i]

for(vector<int>::size_type i = 0; i<v.size(); ++i)    // longer but always correct
    ...  // do something with v[i]

for(vector<int>::iterator p = v.begin(); p!=v.end(); ++p)
    ...  // do something with *p
```
```

+   - know both ways (iterator and subscript)
+     - The subscript style is used in essentially every language
+     - The iterator style is used in C (pointers only) and C++
+     - The iterator style is used for standard library algorithms
+     - The subscript style doesn’t work for lists (in C++ and in most languages)
+   - use either way for vectors
+     - There are no fundamental advantage of one style over the other
+     - But the iterator style works for all sequences
+     - Prefer `size_type` over plain `int`
+       - pedantic, but quiets compiler and prevents rare errors