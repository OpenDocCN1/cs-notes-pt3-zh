
## 2.4.3 Transposing a Matrix

### Transpose:

If an element is at position [ i ][ j ] in the original matrix, then it is at position [ j ][ i ] in the transposed matrix.

Fig.2.3(b) shows the transpose of Fig2.3(a).

| smArray | row | col | value |
|---|---|---:|---:|---:|
| smArray[0] | 0 | 0 | 15 |
| [1] | 0 | 4 | 91 |
| [2] | 1 | 1 | 11 |
| [3] | 2 | 1 | 3 |
| [4] | 2 | 5 | 28 |
| [5] | 3 | 0 | 22 |
| [6] | 3 | 2 | -6 |
| [7] | 5 | 0 | -15 |

![](img/15e8d7d94d8ddf02cb6839870195a31e_80_0.png)

# Fig 2.3 (b)

### First try:

For (each row i)
	take element (i, j, value) and
	store it in (j, i, value) of the transpose;

**Difficulty:** not knowing where to put (j, i, value)
until all other elements preceding it have been
processed.

### Improvement:

For (all elements in column j)
store (i, j, value) of the original matrix as
(j, i, value) of the transpose;

Since the rows are in order, we will locate elements in the correct column order.

```
1 SparseMatrix SparseMatrix::Transpose ()
2 { // return the transpose of *this
3   SparseMatrix b(cols, rows, terms);
4   if (terms > 0)
5   {  //nonzero matrix
6   int currentB = 0;
7    for ( int c=0; c<cols; c++ ) // transpose by columns
8      for ( int i=0; i<terms; i++ )
9      // find and move terms in column c
10     if ( smArray[i].col == c )
11     {
12       b.smArray[CurrentB].row = c;
13       b.smArray[CurrentB].col = smArray[i].row;
14       b.smArray[CurrentB++].value= smArray[i].value;
15     }
16   } // end of if (terms > 0)
17   return b;
18 }
```

we can get an easy O(cols* rows ) algorithm as:

```
for (int j=0;j < columns;j++)
    for (int i=0; i < rows; i++) B[j][i] = A[i][j];
```

### Further improvement:

If we use some more space to store some knowledge about the matrix, we can do much better: doing it in O(cols + terms).

- get the number of elements in each column of *this = the number of elements in each row of b;
- obtain the starting point in b of each of its rows;
- move the elements of *this one by one into their right position in b.

Now the algorithm FastTranspose.

```
1 SparseMatrix SparseMatrix::FastTranspose ()
2 { // return the transpose of *this in O(terms+cols) time.
3   SparseMatrix b(cols, rows, terms);
4   if (terms > 0)
5   { // nonzero matrix
6     int *rowSize = new int[cols];
7     int *rowStart = new int[cols];
8     // compute rowSize[i] = number of terms in row i of b
9     fill(rowSize, rowSize + cols, 0); // initialze
10   for (i=0; i<terms; i++ ) rowSize[smArray[i].col]++;
22    delete [ ] rowSize;
23    delete [ ] rowStart;
24 } // end of if
25 return b;
26 }
```

For Fig.2.3(a), after line 13, we get :

|  | [0] | [1] | [2] | [3] | [4] | [5] |
|---|---:|---:|---:|---:|---:|---:|
| RowSize= | 2 | 1 | 2 | 2 | 0 | 1 |
| RowStart= | 0 | 2 | 3 | 5 | 7 | 7 |

Note the error in P101 of the text book!

## 2.6 The String Abstract data Type

A string  S = s₀, s₁, ..., sₙ₋₁\nwhere  sᵢ ∈ char, 0 ≤ i < n, n is the length.

### ADT 2.5 String

```
class String
{
    // a finite set of zero or more characters;
public:
    String (char *init, int m);
    // initialize *this to string init of length m
```

```
bool operator == (String t );
// if *this equals t, return true else false.
bool operator ! ( );
// if *this is empty return true else false.
int Length ();
// return the number of chars in *this
String Concat (String t);
String Substr (int i, int j);
int Find (String pat);
// return i such that pat matches the substring of *this that
// begins at position i. Return −1 if pat is either empty or not
// a substring of *this.
};
```

## 2.6.1 String Pattern Matching: A Simple Algorithm

![](img/15e8d7d94d8ddf02cb6839870195a31e_95_0.png)

The idea is showed in the function Find .
