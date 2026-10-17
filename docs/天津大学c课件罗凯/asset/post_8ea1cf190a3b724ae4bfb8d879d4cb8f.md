
## What is the output?

```cpp
int cntr1 = 0, cntr2 = 0, cntr3 = 0, cntr4 = 0, cntr5 = 0;
cntr1++;

for (int i = 1; i <= 10; ++i) {
    cntr2++;

    for (int j = 1; j <= 20; ++j) {
        cntr3++;
    }

    cntr4++;
}

cntr5++;

cout << "cntr1: " << cntr1 << endl
     << "cntr2: " << cntr2 << endl
     << "cntr3: " << cntr3 << endl
     << "cntr4: " << cntr4 << endl
     << "cntr5: " << cntr5 << endl;
```

## Class Exercise

- Write code to display a grid.
  - For each position, display the location's row and column number. Put two blanks between each location.

Ex:

```text
1,1   1,2   1,3 ....  1,9
2,1   2,2     ....      2,9
....
8,1   8,2     ....      8,9
9,1   9,2   9,3 ......  9,9
```

### One solution to grid exercise

```cpp
for(int row = 1; row < 10; row++ ){

    for(int col = 1; col < 10; col++) {
        cout << row << ',' << col << "  ";
    } // end of col loop

    cout << endl;

}  // end of row loop
```

## Another use of break

- break can be used to exit a loop

```cpp
// in some game

while ( life > 0 ) {
    ..........                 // play game
    cout << "Do you want to quit(q):";
    cin >> userResponse;
    if (userResponse == 'q' )
        break;
} // end while loop
```

not the best example

### A better solution

```cpp
// in some game
userResponse = 'c';
while ( life > 0 && userResponse != 'q' ) {
    // play game
    ....
    cin >> userResponse;
} // end while loop
```

### The best solution

```cpp
// in some game

do {
    // play game
    ...
    cin >> userResponse;
} while ( life > 0 && userResponse != 'q' );
```

## Another use of break

- break will only exit out of **one** loop (if embedded)

```cpp
for ( int row = 1; row < 10; row++ ) {

    for ( int col = 1; col < 10; col++) {
        // do something

        if ( ???? )
            break;    // this will stop the col loop
    }  // col loop

}  // row loop
```

## Continue, the brother of break

- The key word, **continue**, will cause execution to skip to the boolean expression

```cpp
while( something == true ) {
    // do something
    if ( x > 0 )
        continue;        // skip to end of block
    // do some more
    ....
}  // end of while
```

![](img/844f1d9b9fc3acdef1abfe5a062e4e8f_412_0.png)

## Using break and continue in loops

- First look for a solution that does not use **break** or **continue**
  - Only use break and continue
    - if it is the _only_ solution, or
    - it makes the code _easier_ to understand

**Note:** always avoid using **goto**.... there is almost always a better way

![](img/844f1d9b9fc3acdef1abfe5a062e4e8f_414_0.png)

## Chapter 5: Functions

### Intro to Functions

- Functions in math may be a good illustration of functions in C++
- Example from math functions:

  f(x) = 2x

  f(3) = ???

  y = 4 + f(5)    so y = ???

### Functions { Math vs Programming }

- Functions in math
- **Example:**

  f(x) = 2x

- When f(x) is solved it is just a number

  y = 4 + f(5)

- In math, there are no data types, so x is some number.
- Functions in C++
  - The same math function could be written as...

```cpp
int f ( int x ) {
    int num;
    num = x * 2;
    return num;
}
```

- C++ has different data types, and so we have to add this information
