# 把循环loop变成 Goto形式

```
void lower1(char *s)
{
    size_t i = 0;
    if (i >= strlen(s))
        goto done;
    loop:
        if (s[i] >= 'A' && s[i] <= 'Z')
            s[i] -= ('A' - 'a');
        i++;
        if (i < strlen(s))
            goto loop;
    done:
}
```

+   - strlen每次循环都要重复执行