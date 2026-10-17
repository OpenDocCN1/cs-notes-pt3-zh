# Reference vs Pointers

+   - Reference can **only** be assigned (initialized) at creation

```
int num = 5, num2 = 8;
int & ref = num;
int * ptr = & num;

// later
ptr = & num2;  // can be changed a second variable
```

+   - Reference can be use like a normal variable (don't need to be dereferenced), but a pointer must be dereferenced

```
ref = 6;
*ptr = 9;
cout << ref << *ptr << endl;
```