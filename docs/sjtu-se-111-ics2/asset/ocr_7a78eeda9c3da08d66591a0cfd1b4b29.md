# Graphical Representation

```
movl %eax,(%ecx)
movl (%ebx), %eax
addl $1,%eax
subl $1,%edx
jne loop
```

```
//inner-loop
while (cnt--) {
  *dest = val;
  val = (*src)+1;
}
```

%eax %ebx %ecx %edx

s_addr
s_data
load
add
sub
jne

%eax %ebx %ecx %edx