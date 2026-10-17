
## Constants and Pointers

- A **constant pointer** is a pointer that cannot change the location that the pointer points to

```cpp
char c = 'c', e = 'e';

char * const ptr1 = &c;
ptr1 = &e;      // illegal
*ptr1 = 'k';    // ok
```

- A **pointer to constant data** is a pointer that points to data that can't be changed

```cpp
const char d = 'd';
const char * ptr2 = &d;
*ptr2 = 'f';      // illegal: cannot change d
                  // through ptr2
ptr2 = &e;       // ok
```

| C++ Code | Can point to diff data | Can change the data pointed to |
|---|---|---|
| `int * iptr;` | TRUE | TRUE |
| `const int *iptr;` | TRUE | FALSE |
| `int * const iptr;` | FALSE | TRUE |
| `const int * const iptr;` | FALSE | FALSE |

> Read from right to left and it becomes easy to understand

## So why use Pointers

- Seems like a lot of trouble to use......
  - now we have reference variables

## Big benefit of Pointers

- You can ask for memory while the program is running

```cpp
int numStd;
cout << "Please enter the number of students: ";
cin >> numStd;    // could be 10, 100, 1000
if ( numStd > 0 )
    int * studentScores = new int[ numStd ];
```

- This memory is called Dynamic memory

## New Operator Behavior

- Memory for dynamic variables
  - Requested from the free store
    - (or also called heap 堆duī or 堆栈 duī zhàn)

- If there is sufficient (enough) memory to satisfy the request
  - A pointer to the memory is returned by the operation

- If there is insufficient (not enough) memory to satisfy the request
  - An exception is generated
    - An exception is an error message which if not handled (corrected) causes the program to terminate
    - more on this next semester

## Differences: Local Variable vs Dynamic Memory

- **Local variables and parameters**
  - Variable memory is acquired automatically

- **Dynamic Memory**
  - Dynamic memory is acquired by program with a memory request (allocation)
    - **new** operation
  - Dynamic memory can exist beyond the function in which they were allocated
  - Dynamic memory is returned by a deallocation request
    - **delete** operation
