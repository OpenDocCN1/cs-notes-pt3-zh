

## Arrays of Structures

- Overall structure length multiple of K
- Satisfy alignment requirement for every element

```c
struct S2 {
    double v;
    int i[2];
    char c;
} a[10];
```

## Accessing Array Elements

- **Compute array offset 12*idx**
  - `sizeof(s3)`, including alignment spacers
- **Element j is at offset 8 within structure**
- **Assembler gives offset a+8**
  - Resolved during linking

```c
short get_j(int idx)
{
    return a[idx].j;
}
```

```asm
# %rdi = idx
leaq (%rdi,%rdi,2), %rax # 3*idx
movzwl a+8(,%rax,4), %eax
```

## Saving Space

- Put large data types first

```c
struct S4 {
  char c;
  int i;
  char d;
} *p;
```

```c
struct S5 {
  int i;
  char c;
  char d;
} *p;
```

- Effect (K=4)

## Example Struct Exam Question

**Problem 5. (8 points):**

*Struct alignment.* Consider the following C struct declaration:

```c
typedef struct {
    char a;
    long b;
    float c;
    char d[3];
    int *e;
    short *f;
} foo;
```

1. Show how `foo` would be allocated in memory on an x86-64 Linux system. Label the bytes with the names of the various fields and clearly mark the end of the struct. Use an X to denote space that is allocated in the struct as padding.

|   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |
|   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |
|   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |
|   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |
|   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |
|   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |
|   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |

[http://www.cs.cmu.edu/~213/oldexams/exam1-f12.pdf](http://www.cs.cmu.edu/~213/oldexams/exam1-f12.pdf)

## Example Struct Exam Question

### Problem 5. (8 points):

_Struct alignment._ Consider the following C struct declaration:

```c
typedef struct {
    char a;
    long b;
    float c;
    char d[3];
    int *e;
    short *f;
} foo;
```

1. Show how `foo` would be allocated in memory on an x86-64 Linux system. Label the bytes with the names of the various fields and **clearly mark the end of the struct**. Use an X to denote space that is allocated in the struct as padding.

http://www.cs.cmu.edu/~213/oldExams/exam1-f12.pdf

Bryant and O'Hallaron, Computer Systems: A Programmer's Perspective, Third Edition

43

## Example Struct Exam Question (Cont’d)

### Problem 5. (8 points):

_Struct alignment_. Consider the following C struct declaration:

```c
typedef struct {
    char a;
    long b;
    float c;
    char d[3];
    int *e;
    short *f;
} foo;
```

2. Rearrange the elements of `foo` to conserve the most space in memory. Label the bytes with the names of the various fields and clearly mark **the end of the struct**. Use an X to denote space that is allocated in the struct as padding.

http://www.cs.cmu.edu/~213/oldExams/exam1-f12.pdf

Bryant and O'Hallaron, Computer Systems: A Programmer's Perspective, Third Edition

44

## Example Struct Exam Question (Cont’d)

**Problem 5. (8 points):**

*Struct alignment.* Consider the following C struct declaration:

```c
typedef struct {
    char a;
    long b;
    float c;
    char d[3];
    int *e;
    short *f;
} foo;
```

2. Rearrange the elements of `foo` to conserve the most space in memory. Label the bytes with the names of the various fields and clearly mark the end of the struct. Use an X to denote space that is allocated in the struct as padding.

| a | d | d | d | c | c | c | c | b | b | b | b | b | b | b | b |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| e | e | e | e | e | e | e | e | f | f | f | f | f | f | f | f |
|   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |
|   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |
|   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |
|   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |

[http://www.cs.cmu.edu/~213/oldexams/exam1-f12.pdf](http://www.cs.cmu.edu/~213/oldexams/exam1-f12.pdf)

