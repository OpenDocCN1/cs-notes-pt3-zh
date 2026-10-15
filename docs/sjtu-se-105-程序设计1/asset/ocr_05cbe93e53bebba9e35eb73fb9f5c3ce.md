+   - 第九版本

```
#include "std_lib_facilities.h"

int main()
{
    int primeNumbers[50];
    int sizeOfPn = 0;
    for (int i=2;i<=100;i++){
        bool pn=true;
        for (int j=0; j<sizeOfPn ;j++)
            if (i%primeNumbers[j] == 0) {
                pn=false;
                break;
            }
        if (pn==true)
            primeNumbers[sizeOfPn++] = i;
    }
}
```