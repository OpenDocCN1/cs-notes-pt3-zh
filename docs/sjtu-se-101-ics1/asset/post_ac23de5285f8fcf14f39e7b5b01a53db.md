
## Out-of-Bounds Memory References

Stack frame for caller

Stack frame for echo

Return address

Saved %ebp

Saved %ebx

[7] [6] [5] [4]

[3] [2] [1] [0]

%ebp

buf

![](img/b3f8b91675c485f1e811aa092ebbf3d4_610_0.png)

Stack frame for caller

Stack frame for echo

Return address

Saved %ebp

%ebp

Stack frame for echo

[11] [10] [9] [8]

[7] [6] [5] [4]

[3] [2] [1] [0]

buf

Stack frame for caller

Stack frame for echo

Return address

%ebp

buf

| [15] | 1[4] | [13] | [12] |
| [11] | [10] | [9] | [8] |
| [7] | [6] | [5] | [4] |
| [3] | [2] | [1] | [0] |

![](img/b3f8b91675c485f1e811aa092ebbf3d4_612_0.png)

![](img/b3f8b91675c485f1e811aa092ebbf3d4_613_0.png)

Stack frame for caller

Stack frame for echo

%ebp

buf

```
```c
/* This is very low-quality code.
   It is intended to illustrate bad programming practices.
   See Problem 3.43. */
char *getline()
{
    char buf[8];
    char *result;
    gets(buf);
    result = malloc(strlen(buf));
    strcpy(result, buf);
    return result;
}
```
```

```
1       080485c0 <getline>:
2       80485c0: 55              push    %ebp
3       80485c1: 89 e5              mov     %esp,%ebp
4       80485c3: 83 ec 28            sub     $0x28,%esp
5       80485c6: 89 5d f4            mov     %ebx,-0xc(%ebp)
6       80485c9: 89 75 f8            mov     %esi,-0x8(%ebp)
7       80485cc: 89 7d fc            mov     %edi,-0x4(%ebp)
    Diagram stack at this point
8       80485cf: 8d 75 ec            lea     -0x14(%ebp),%esi
9       80485d2: 89 34 24            mov     %esi,(%esp)
10      80485d5: e8 a3 ff ff ff      call    804857d <gets>
    Modify diagram to show stack contents at this point
```

```
2 push %ebp
3 mov %esp,%ebp
4 sub $0x28,%esp
5 mov %ebx,-0xc(%ebp)
6 mov %esi,-0x8(%ebp)
7 mov %edi,-0x4(%ebp)
```

*Diagram stack at this point*

```
8 lea -0x14(%ebp),%esi
9 mov %esi,(%esp)
```

+   - call 804857d <gets>

![](img/b3f8b91675c485f1e811aa092ebbf3d4_616_0.png)

```
2 push %ebp
3 mov %esp,%ebp
4 sub $0x28,%esp
5 mov %ebx,-0xc(%ebp)
6 mov %esi,-0x8(%ebp)
7 mov %edi,-0x4(%ebp)
Diagram stack at this point
8 lea -0x14(%ebp),%esi
9 mov %esi,(%esp)
• call 804857d <gets>
```

Return address
Saved %ebp
Saved %edi
Saved %esi
Saved %ebx

%ebp
%ebx
%edi
%esi

```
2 push %ebp
3 mov %esp,%ebp
4 sub $0x28,%esp
5 mov %ebx,-0xc(%ebp)
6 mov %esi,-0x8(%ebp)
7 mov %edi,-0x4(%ebp)
8 lea -0x14(%ebp),%esi
9 mov %esi,(%esp)
10 call 804857d <gets>
```

Modify diagram to show stack contents at this point

“012345678901234567890123”

## Malicious Use of Buffer Overflow

```
void foo() {
  bar();
  ...
}
```

```
void bar() {
  char buf[64];
  gets(buf);
  ...
}
```

return address A

Stack
after call to gets()

foo stack frame

data written by gets()

B

pad

exploit code

bar stack frame

B

- Input string contains byte representation of executable code
- Overwrite return address with address of buffer
- When bar() executes ret, will jump to exploit code

## The Famous Internet Worm of November 1988

- To gain access to many of the computers across the Internet
  - 4 different ways
  - One was a buffer overflow attack on the fingerd
- Hundreds of machines were effectively paralyzed
- The author of the worm was caught and prosecuted. He was sentenced to
  - 3 years probation
  - 400 hours of community service
  - and a $10,500 fine

## The Famous Internet Worm of November 1988

- Steps
  - invoked finger with an appropriate string
  - Made a process at a remote site have a buffer overflow
  - executed code that gave the worm access to the remote system
  - The worm replicated itself and consumed virtually all of the machine's computing resources
