# 非本地跳转的局限

+   - 工作在堆栈规则下
+     - 只能跳到被调用但尚未完成的函数环境中

```
jmp_buf env;

P1()
{
    if (setjmp(env)) {
        /* Long Jump to here */
    } else {
        P2();
    }
}

P2()
{ . . . P2(); . . . P3(); }

P3()
{
    longjmp(env, 1);
}
```

![](bbox=[0.66, 0.31, 0.99, 0.75])