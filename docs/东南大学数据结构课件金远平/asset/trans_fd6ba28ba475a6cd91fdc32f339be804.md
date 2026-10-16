

```cpp
Polynomial Polynomial::Add (Polynomial b)
{
    // return the sum of the polynomials *this and b.
    Polynomial c;
    int aPos=0, bPos=0;
    while (( aPos < terms) && (bPos < b.terms))
        if (termArray[aPos].exp==b.termArray[bPos].exp) {
            float t = termArray[aPos].coef + termArray[bPos].coef;
            if (t) c.NewTerm (t, termArray[aPos].exp);
            aPos++; bPos++;
        }
        else if (termArray[aPos].exp < b.termArray[bPos].exp) {
            c.NewTerm (b.termArray[bPos].coef, b.termArray[bPos].exp);
            bPos++;
        }
else {
    c.NewTerm (termArray[aPos].coef, termArray[aPos].exp);
    aPos++;
}
// add in the remaining terms of *this
for (; aPos < terms; aPos++)
    c.NewTerm(termArray[aPos].coef, termArray[aPos].exp);
// add in the remaining terms of b
for (; bPos < b.terms; bPos++)
    c.NewTerm(b.termArray[bPos].coef, b.termArray[bPos].exp);
return c;
}
```

```cpp
void Polynomial::NewTerm(const float theCoeff, const int theExp)
{ // add a new term to the end of termArray.
    if (terms == capacity)
    { // double capacity of termArray
        capacity *= 2;
        term *temp = new term[capacity]; // new array
        copy(termArray, termArray + terms, temp);
        delete [] termArray; // deallocate old memory
        termArray = temp;
    }
    termArray[terms].coef = theCoeff;
    termArray[terms++].exp = theExp;
}
```

## Analysis of doubling capacity:

- the time for doubling is linear in the size of new array
- initially, c.capacity is 1
- suppose when Add terminates, c.capacity is 2^k
- the total time spent over all array doubling is

`O(∑_{i=1}^{k} 2^i) = O(2^{k+1}) = O(2^k)`

- since c.terms > 2^{k-1} and m + n ≥ c.terms, the total time for array doubling is

`O(c.terms) = O(m + n)`

- so, even consider array doubling, the total run time of Add is O(m + n).
- experiments show that array doubling is responsible for very small fraction of the total run time of Add.

Exercises: P93-2,6, P94-9

## 2.4 Sparse Matrices

### 2.4.1 Introduction

A general matrix consists of m rows and n columns (m × n) of numbers, as:

![](img/15e8d7d94d8ddf02cb6839870195a31e_72_0.png)

|   | 0 | 1 | 2 | 3 | 4 | 5 |
|---|----|----|----|----|----|----|
| 0 | 15 | 0 | 0 | 22 | 0 | -15 |
| 1 | 0 | 11 | 3 | 0 | 0 | 0 |
| 2 | 0 | 0 | 0 | -6 | 0 | 0 |
| 3 | 0 | 0 | 0 | 0 | 0 | 0 |
| 4 | 91 | 0 | 0 | 0 | 0 | 0 |
| 5 | 0 | 0 | 28 | 0 | 0 | 0 |

Fig. 2.2(b) 6×6

A matrix of m × m is called a square.

A matrix with many zero entries is called sparse.

Representation:

- A natural way --- a[m][n], access element by a[i][j], easy operations. But for sparse matrix, wasteful of both memory and time.
- Alternative way --- store nonzero elements explicitly. 0 as default.

## ADT 2.4  **SparseMatrix**

```
class SparseMatrix
{
  // a set of <row, column, value>, where row, column are
  // non-negative integers and form a unique combination;
  // value is also an integer.
public:
  SparseMatrix ( int r, int c, int t);
  // creates a r×c SparseMatrix with a capacity of t nonzero
  // terms
  SparseMatrix Transpose( );
  // return the SparseMatrix obtained by transposing *this
  SparseMatrix Add ( SparseMatrix b);
  SparseMatrix Multiply ( SparseMatrix b);
};
```

## 2.4.2 Sparse Matrix Representation

Use triple <row, col, value>, sorted in ascending order by <row, col>.

We need also the number of rows and the number of columns and the number of nonzero elements. Hence,

```
class SparseMatrix;
class MatrixTerm {
friend class SparseMatrix;
private:
    int row, col, value;
};
```

# And in class SparseMatrix:

**private:**  
&nbsp;&nbsp;&nbsp;&nbsp;`Int` rows, cols, terms, capacity;  
&nbsp;&nbsp;&nbsp;&nbsp;`MatrixTerm *smArray;`

Now we can store the matrix of Fig.2.2 (b) as Fig.2.3 (a).

|  | row | col | value |
|---|---:|---:|---:|
| sm.Array[0] | 0 | 0 | 15 |
| [1] | 0 | 3 | 22 |
| [2] | 0 | 5 | -15 |
| [3] | 1 | 1 | 11 |
| [4] | 1 | 2 | 3 |
| [5] | 2 | 3 | -6 |
| [6] | 4 | 0 | 91 |
| [7] | 5 | 2 | 28 |

![](img/15e8d7d94d8ddf02cb6839870195a31e_78_0.png)

