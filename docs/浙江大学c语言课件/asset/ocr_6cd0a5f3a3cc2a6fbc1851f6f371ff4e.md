# ## 3.2 If-else

+   • Example:

```
```c
if (n>=0)
for(i=0;i<n;i++)
if (s[i]>0) {
printf("...");
return i;
}
else printf("error – n is negative \n");
```
```

```
```c
if (n>=0)
for(i=0;i<n;i++)
{
if (s[i]>0) {
printf("...");
return i;
}
}
else printf("error – n is negative \n");
```
```