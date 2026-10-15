
## Array

```
struct ccc {
    char c1;
    short a[3];
    char c2;
};

struct sss s[2];
```

![](img/b3f8b91675c485f1e811aa092ebbf3d4_595_0.png)

## Array

```
struct iii {
    char c1;
    int a[3];
    char c2;
};

struct iii i[2];
```

![](img/b3f8b91675c485f1e811aa092ebbf3d4_596_0.png)

## Understanding Pointers
Buffer Overflow

## Outline

- Understanding Pointers
- Buffer Overflow
- Suggested reading
  - Chap 3.10, 3.12

## Pointers

- Every pointer has a type
  - If the object has type T
    - A pointer to this object has type T *
  - Special void * type
    - Represents a generic pointer
    - malloc returns a generic pointer
- Every pointer has a value

## Pointers

- Pointers are created with the & operator
  - Applied to lvalue expression
    - Lvalue expression can appear on the left side of assignment
- Pointers are dereferenced with the operator *
  - The result is a value having the type associated with the pointer
- Arrays and pointers are closed related
  - The name of array can be viewed as a pointer constant
  - ip[0] is equivalent to *ip

## Pointer Arithmetic

- Addition and subtraction
  - p+i , p-i (result is a pointer)
  - p-q (result is a int)
- Referencing & dereferencing
  - *p, &E
- Subscription
  - A[i], *(A+i)

## Pointers can point to functions

- void (*f)(int *)
- f is a pointer to function
- The function taken int * as argument
- The return type of the function is void
- Assignment makes f point to func
  - f = func
- Notice the precedence of the operators
  - void *f(int *) declares f is a function
    - (void *) f(int *)

## Pointer Declaration

- char **argv ;
- int (*daytab)[13]
- int (*comp)()
- char (*(*x())[])()
  - Function returning pointer to array[ ] of pointer to function returning char
- char (*(*x[3])())[5]
  - Array[3] of pointer to function returning pointer to array[5] of char

## C operators

| Operators | Associativity |
|---|---|
| () [] -> . ++ -- | left to right |
| ! ~ ++ -- + - * & (type) sizeof | right to left |
| * / % | left to right |
| + - | left to right |
| << >> | left to right |
| < <= > >= | left to right |
| == != | left to right |
| & | left to right |
| ^ | left to right |
| | | left to right |
| && | left to right |
| || | left to right |
| ?: | right to left |
| = += -= *= /= %= &= ^= != <<= >>= | right to left |
| , | left to right |

Note: Unary +, -, and * have higher precedence than binary forms

## Parameter Passing

- Call by value
  - f(xp)
- Call by reference
  - f(&xp)

## Out-of-Bounds Memory References

```
1 /* Implementation of library function gets() */
2 char *gets(char *s)
3 {
4     int c;
5     char *dest = s;
6     int got_char = 0; /*Has at least one character been read? */
7     while ((c = getchar()) != '\n' && c != EOF) {
8         *dest++ = c;    /* No bounds checking */
9         gotchar = 1;
10    }
```

## Out-of-Bounds Memory References

```
11  *dest++ = '\0';          /* Terminate String */
12  if (c == EOF && !gotchar)
13      return NULL;  /* End of file or error */
14  return s;
15 }
16
```

Type ctrl-d at keyboard means EOF

## Out-of-Bounds Memory References

```c
14 /* Read input line and write it back */
15 void echo()
16 {
17     char buf[8];     /* Way too small! */
18     gets(buf);
19     puts(buf);
20 }
```

## Out-of-Bounds Memory References

```
1 echo:
2 pushl    %ebp                Save %ebp on stack
3 movl     %esp, %ebp
4 pushl    %ebx                Save %ebx
5 subl     $20, %esp           Allocate 20 bytes on stack
6 leal     -12(%ebp), %ebx     Compute buf as %ebp-12
7 movl     %ebx, (%esp)        Store buf at top of stack
8 call     gets                Call gets
9 movl     %ebx, (%esp)        Store buf at top of stack
10 call    puts                Call puts
11 addl    $20, %esp           Deallocate stack space
12 popl    %ebx                Restore %ebx
13 popl    %ebp                Restore %ebp
14 ret                         Return
```
