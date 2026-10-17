# 3.5 Loops----While and For

# Example 1:

```
#include <ctype.h>
/*atoi: convey s to integer; version 2 */
int atoi(char s[])
{ int I,n, sign;
for(i=0;isspace(s[i]);i++; /*skip white space */
sign = (s[i] == '-')? -1:1;
if( s[i] == '-')? -1:1;
i++;
for(n=0; isdigit(s[i]);i++)
n=10*n +(s[i]- '0');
return sign *n ;
}
```