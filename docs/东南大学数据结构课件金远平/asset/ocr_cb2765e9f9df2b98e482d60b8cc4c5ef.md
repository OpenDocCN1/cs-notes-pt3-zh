# Insertion sort:

Begin with the ordered sequence a[1], then successively insert a[2], a[3], ..., a[n] into the sequence.

```
template<class T>
void InsertionSort (Element *a, const int n)
{ //sort a[1:n] into nondescreasing order.
    for (int j=2; j<=n; j++) {
        T temp = a[j]; // necessary, because a[j] may change in
        // Insertion
        Insert (temp, a, j-1);
    }
}
```