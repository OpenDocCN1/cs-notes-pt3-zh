# Using the constructor

```
```cpp
int main() {
    Time t(12, 30);
    Time t2(-1, 78);
    t.print();
    cout << endl;
    t2.print();

    cout << endl << endl;
    return 0;
}
```
```

```
```cpp
Time(int hr, int mn) {
    setHour(hr);
    setMin(mn);
}
```
```

```
```cpp
void setHour(int hr) {
    hour = 0;
    if (hr >= 0 && hr <= 23) {
        hour = hr;
    }
} // end of setHour
```
```

![](bbox=[0.862, 0.819, 0.976, 0.875])