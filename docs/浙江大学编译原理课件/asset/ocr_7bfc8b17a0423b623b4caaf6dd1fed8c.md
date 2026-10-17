# example

```
**Figure 8.1 Sample TINY program**
```text
{ sample program
  in TINY language --
computes factorial
}
read x ; { input an integer }
if 0 < x then { don’t compute if x <= 0 }
  fact:=1;
  repeat
    fact:=fact*x;
    x:=x-1
  until x=0;
write fact { output factorial of x }
  end
```
```

```
**Figure 8.2 Three-address code**
```text
read x
t1=x>0
if_false t1 goto L1
fact=1
label  L2
t2 = fact * x
fact = t2
t3 = x - 1
x = t3
t4 = x == 0
if_false t4 goto L2
write fact
label  L1
halt
```
```