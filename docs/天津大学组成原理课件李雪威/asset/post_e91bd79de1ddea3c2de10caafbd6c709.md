
## Control Flow Example #4

```
0000000000400540 <multstore>:
    ...
    ...
400544:   callq   400550 <mult2>
400549:   mov     %rax,(%rbx)
    ...
    ...
```

```
0000000000400550 <mult2>:
400550:   mov     %rdi,%rax
    ...
    ...
400557:   retq
```

![](img/be2cf0737cec89669e7b18813ea2d3b7_278_0.png)

![](img/be2cf0737cec89669e7b18813ea2d3b7_278_1.png)

![](img/be2cf0737cec89669e7b18813ea2d3b7_278_2.png)

## Procedure Data Flow

### Registers

- First 6 arguments

![](img/be2cf0737cec89669e7b18813ea2d3b7_280_0.png)

### Return value

![](img/be2cf0737cec89669e7b18813ea2d3b7_280_1.png)

### Stack

![](img/be2cf0737cec89669e7b18813ea2d3b7_280_2.png)

- Only allocate stack space when needed

## Data Flow Examples

```c
void multstore
(long x, long y, long *dest)
{
    long t = mult2(x, y);
    *dest = t;
}
```

```
0000000000400540 <multstore>:
# x in %rdi, y in %rsi, dest in %rdx
...
400541: mov    %rdx,%rbx        # Save dest
400544: callq  400550 <mult2>   # mult2(x,y)
# t in %rax
400549: mov    %rax,(%rbx)      # Save at dest
...
```

```c
long mult2
(long a, long b)
{
    long s = a * b;
    return s;
}
```

```
0000000000400550 <mult2>:
# a in %rdi, b in %rsi
400550: mov    %rdi,%rax        # a
400553: imul   %rsi,%rax        # a * b
# s in %rax
400557: retq                  # Return
```

## Stack-Based Languages

### Languages that support recursion

- e.g., C, Pascal, Java
- Code must be "Reentrant"
- Multiple simultaneous instantiations of single procedure
- Need some place to store state of each instantiation
- Arguments
- Local variables
- Return pointer

### Stack discipline

- State for given procedure needed for limited time
- From when called to when return
- Callee returns before caller does

### Stack allocated in Frames

- state for single procedure instantiation

## Call Chain Example

```c
yoo (...) {
    ...
    who (); ;
    ...
}
```

```c
who (...) {
    ...
    amI (); ;
    ...
    amI (); ;
    ...
}
```

```c
amI (...) {
    ...
    amI (); ;
    ...
}
```

Procedure `amI()` is recursive

![](img/be2cf0737cec89669e7b18813ea2d3b7_284_0.png)

Bryant and O’Hallaron, Computer Systems: A Programmer’s Perspective, Third Edition

30

## Example

```c
yoo (...) {
  .
  .
  who ();
  .
  .
}
```

![](img/be2cf0737cec89669e7b18813ea2d3b7_286_0.png)

Bryant and O'Hallaron, Computer Systems: A Programmer's Perspective, Third Edition

32

## Example

![](img/be2cf0737cec89669e7b18813ea2d3b7_287_0.png)

## Example

![](img/be2cf0737cec89669e7b18813ea2d3b7_288_0.png)

## Example

![](img/be2cf0737cec89669e7b18813ea2d3b7_289_0.png)

## Example

![](img/be2cf0737cec89669e7b18813ea2d3b7_290_0.png)

![](img/be2cf0737cec89669e7b18813ea2d3b7_290_1.png)

![](img/be2cf0737cec89669e7b18813ea2d3b7_290_2.png)

## Example

![](img/be2cf0737cec89669e7b18813ea2d3b7_291_0.png)

## Example

![](img/be2cf0737cec89669e7b18813ea2d3b7_292_0.png)

Bryant and O'Hallaron, Computer Systems: A Programmer's Perspective, Third Edition

38

## Example

![](img/be2cf0737cec89669e7b18813ea2d3b7_294_0.png)

# Stack

`%rbp`

`%rsp`

## Example

![](img/be2cf0737cec89669e7b18813ea2d3b7_295_0.png)

## Example

```c
yoo (...) {
    ...
    who ();
    ...
}
```

![](img/be2cf0737cec89669e7b18813ea2d3b7_296_0.png)

![](img/be2cf0737cec89669e7b18813ea2d3b7_296_1.png)

## x86-64/Linux Stack Frame

### Current Stack Frame ("Top" to Bottom)

- "Argument build:"
  - Parameters for function about to call
- Local variables
  - If can’t keep in registers
- Saved register context
- Old frame pointer (optional)

### Caller Stack Frame

- Return address
  - Pushed by `call` instruction
- Arguments for this call

![](img/be2cf0737cec89669e7b18813ea2d3b7_297_0.png)

Bryant and O’Hallaron, Computer Systems: A Programmer’s Perspective, Third Edition
