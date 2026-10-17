```
```cpp
// constructor used when no dimensions specified
Box() {
    width = -1;   // use -1 to indicate
    height = -1;  // an uninitialized
    depth = -1;   // box
}

// constructor used when cube is created
Box(double len) {
    width = height = depth = len;
}

// compute and return volume
double volume() {
    return width * height * depth;
}
}
```
```

![](bbox=[0.596, 0.285, 1.0, 1.0])