# § 5.3 CSP简单实例

例2 哲学家就餐问题(假设有五位哲学家)

```
PHIL ::
    do true ⇒ THINK;
        room ! enter();
        fork(i) ! pickup();
        fork((i + 1) mod 5) ! pickup();
        EAT;
        fork (i) ! putdown();
        fork ((i + 1) mod 5) ! putdown();
        room ! exit()
    od
```