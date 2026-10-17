# # Buffer Overflow Stack Example #3 Explained

# ## After call to gets

| **Stack Frame** |
| **for call_echo** |
| 00 | 00 | 00 | 00 |
| 00 | 48 | 83 | 80 |
| 00 | 00 | 00 | 00 |
| 00 | 40 | 06 | 00 |
| 33 | 32 | 31 | 30 |
| 39 | 38 | 37 | 36 |
| 35 | 34 | 33 | 32 |
| 31 | 30 | 39 | 38 |
| 37 | 36 | 35 | 34 |
| 33 | 32 | 31 | 30 |

# ### register_tm_clones:

```
```asm
400600: mov %rsp,%rbp
400603: mov %rax,%rdx
400606: shr $0x3f,%rdx
40060a: add %rdx,%rax
40060d: sar %rax
400610: jne 400614
400612: pop %rbp
400613: retq
```
```

```
```c
void call_echo() {
    echo();
}
```
```

"Returns" to unrelated code
Lots of things happen, without modifying critical state
Eventually executes retq back to main – call_echo has no local variables