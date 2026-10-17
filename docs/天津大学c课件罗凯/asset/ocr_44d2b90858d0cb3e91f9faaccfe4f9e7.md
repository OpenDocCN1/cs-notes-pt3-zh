# # strcpy: String copy for cstrings

or it could be written like this.....

```
```c
char * strcpy( char * dest, const char * source ) {
    char * start = dest;
    while( *dest++ = *source++ );    // empty loop
    return start;
}
```
```