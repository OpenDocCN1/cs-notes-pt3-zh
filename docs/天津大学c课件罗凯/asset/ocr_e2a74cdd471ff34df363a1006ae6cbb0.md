# Using Multi-Dimension Arrays

```
```cpp
int studentScores [NUM_CLASSES] [STDS_PER_CLASS];
int total = 0;

// grades are inputted into the array some how

for ( int i = 0; i < NUM_CLASSES; i++ ) {
    for ( int j = 0; j < STDS_PER_CLASS; j++ ) {
        total += studentScores [ i ] [ j ];
    }
}
cout << "Average Student Score: "
     <<  total / ( NUM_CLASSES * STDS_PER_CLASS )
     <<  endl;
```
```