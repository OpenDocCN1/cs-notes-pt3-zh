# ## 2.15 Arrays versus Pointers

# ### Two C procedures

# #### Array version

```
```c
clear1 ( int  array[], int size )
{
    int  i;
    for ( i = 0 ; i < size ; i = i + 1 )
        array[i] = 0;
}
```
```

# #### Pointer version

```
```c
clear2 ( int *array, int size )
{
    int  *p;
    for ( p = &array[0]; p < &array[size]; p = p + 1 )
        *p = 0;
}
```
```