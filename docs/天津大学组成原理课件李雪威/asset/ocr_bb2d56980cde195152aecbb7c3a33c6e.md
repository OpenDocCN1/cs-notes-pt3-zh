# # Branch Misprediction Invalidation

```
401029: vmulsd (%rdx), %xmm0, %xmm0
40102d: add $0x8, %rdx
401031: cmp %rax, %rdx
401034: jne 401029
```

```
401029: vmulsd (%rdx), %xmm0, %xmm0
40102d: add $0x8, %rdx
401031: cmp %rax, %rdx
401034: jne 401029
```

```
401029: vmulsd (%rdx), %xmm0, %xmm0
40102d: add $0x8, %rdx
401031: cmp %rax, %rdx
401034: jne 401029
```

```
401029: vmulsd (%rdx), %xmm0, %xmm0
40102d: add $0x8, %rdx
401031: cmp %rax, %rdx
401034: jne 401029
```

Assume vector length = 100

i = 98

Predict Taken (OK)

i = 99

Predict Taken (Oops)

i = 100

Invalidate

i = 101