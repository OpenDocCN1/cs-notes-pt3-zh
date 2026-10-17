# # strcpy: String copy for cstrings

It could be written like this.....

```
char * strcpy( char * dest, const char * source ) {
    char * start = dest;
    while( (*dest = *source) != '\0' ) {
        dest++;
        source++;
    }
    return start;
}
```