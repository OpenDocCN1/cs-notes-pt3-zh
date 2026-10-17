# Constants and Pointers

| C++ Code | Can point to diff data | Can change the data pointed to |
|---|---|---|
| `int * iptr;` | TRUE | TRUE |
| `const int *iptr;` | TRUE | FALSE |
| `int * const iptr;` | FALSE | TRUE |

> > Read from right to left and it becomes easy to understand