# # Constants and Pointers

+   - A constant pointer is a pointer that cannot change the location that the pointer points to

```
char c = 'c', e = 'e';
char * const ptr1 = &c;
ptr1 = &e;       // illegal
*ptr1 = 'k';     // ok
```

+   - A **pointer to constant data** is a pointer that points to data that can't be changed

```
const char d = 'd';
const char * ptr2 = &d;
*ptr2 = 'f';      // illegal: cannot change d
                  // through ptr2
ptr2 = &e;       // ok
```