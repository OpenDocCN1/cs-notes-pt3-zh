# Calling a Function with Multi-Dim Arrays

```
```cpp
const int NUM_CLSS = 5, NUM_STDS = 35;
```
```

```
```cpp
// function prototype
```
```

```
```cpp
int averageScore( int scores [][NUM_STDS] );
```
```

```
```cpp
// in main
```
```

```
```cpp
int studentScores [NUM_CLSS] [NUM_STDS];
int average = 0;
.......

average = averageScores( studentScores, NUM_CLSS );
```
```

> > What is wrong with this example?