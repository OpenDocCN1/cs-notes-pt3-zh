# # Simulating Selection Sort

```
```cpp
int main() {

void sort(Vector<int> & vec) {
    for ( int lh = 0 ; lh < vec.size() ; lh++ ) {
        int rh = findSmallest(vec, lh, vec.size() - 1);
        swap(vec[lh], vec[rh]);
    }
}
```
```

![](bbox=[0.55, 0.474, 0.864, 0.55])

| 809 | 503 | 946 | 367 | 987 | 838 | 259 | 236 | 659 | 361 |
|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 |