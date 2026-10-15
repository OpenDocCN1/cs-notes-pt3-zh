
## Structure
```
int area (struct rect *rp)
{
    return (*rp).width * (*rp).height;
}

void rotate_left (struct rect *rp)
{
    /* Exchange width and height */
    int t = rp->height;
    rp->height = rp->width;
    rp->width = t;
}
```

## Structures
- Memory layout
  - All the components are stored in a contiguous region of memory
  - A pointer to a structure is the address of its first byte

## Structure
```
struct rec {
    int i;
    int j;
    int a[3];
    int *p;
} *r;
```

| Offset | 0 | 4 | 8 |  |  | 20 |
|---|---|---|---|---|---|---|
| Contents | i | j | a[0] | a[1] | a[2] | p |

## Structure
- References to structure elements
  - Using offsets as displacements

r->j = r->i   (Copy element r->i to element r->j)

r is in register %edx.

```
1 movl    (%edx), %eax    Get r->i
2 movl    %eax,    4(%edx)  Store in r->j
```

| Offset | 0 | 4 | 8 | 20 |
| Contents | i | j | a[0] | a[1] | a[2] | p |

## Structure
&(r->a[i])

r in %eax, i in %edx:

```
1 leal 8(%eax,%edx,4),%ecx Generate &(r->a[i])
```

| Offset | 0 | 4 | 8 |  |  | 20 |
| Contents | i | j | a[0] | a[1] | a[2] | p |

## Unions
- A single object can be referenced by using different data types
- The syntax of a union declaration is identical to that for structures, but its semantics are very different
- Rather than having the different fields reference different blocks of memory, they all reference the same block

## Unions
```
struct NODE {
    struct NODE *left;
    struct NODE *right;
    double data;
};

union NODE {
    struct {
        union NODE *left;
        union NODE *right;
    } internal;
    double data;
};
```

## Unions
```
struct NODE {
    int is_leaf;
    union {
        struct {
            struct NODE *left;
            struct NODE *right;
        } internal;
        double data;
    } info;
};
```

## Unions
```
1 unsigned float2bit(float f)
2 {
3     union {
4         float f;
5         unsigned u;
6     } temp;
7     temp.f = f;
8     return temp.u;
9 }
```

```
1 movl    8(%ebp),    %eax
```

## Unions
```
1 unsigned copy (unsigned u)
2 {
3     return u;
4 }
```

```
1 movl    8(%ebp),    %eax
```

## Alignment
- Alignment restrictions
  - The address for some type of object must be a multiple of some value k (typically 2, 4, or 8)
  - Simplify the hardware design of the interface between the processor and the memory system

## Alignment
- In IA32
  - hardware will work correctly regardless of the alignment of data
  - Aligned data can improve memory system performance

## Alignment
- Linux alignment restriction
  - 1-byte data types are able to have any address
  - 2-byte data types must have an address that is multiple of 2
  - Any larger data types must have an address that is multiple of 4

## Alignment
- Alignment is enforced by
  - Making sure that every data type is organized and allocated in such a way that every object within the type satisfies its alignment restrictions.
- malloc()
  - Returns a generic pointer that is void *
  - Its alignment requirement is 4

## Alignment
- Structure data type
  - may need to insert gaps in the field allocation
  - may need to add padding to the end of the structure

## Simple Example
```
struct xxx {
    int i;
    char c;
    double d;
};

struct xxx x[2];
```

![](img/b3f8b91675c485f1e811aa092ebbf3d4_592_0.png)

## Complex Example
```
struct xxx {
    short s;
    char c0;
    int i;
    long l;
    char c1;
    char a[2];
    double d;
    char c2;
};

struct xxx x[2];
```

0x00
0x04
0x08
0x0C
0x10
0x14
0x18
0x1C

&x[0].s
&x[0].c0
&x[0].i
&x[0].l
&x[0].c1
&x[0].a[0]
&x[0].a[1]
&x[0].d
&x[0].c2
&x[1].s

## Array
```
struct ccc {
    char c1;
    char a[3];
    char c2;
};

struct ccc c[2];
```

![](img/b3f8b91675c485f1e811aa092ebbf3d4_594_0.png)
