e.g. the calling sequence is like the following:

```
main()
{.....
    q();
}
p()
{.....}
q()
{
.....
p();
.....
}
```