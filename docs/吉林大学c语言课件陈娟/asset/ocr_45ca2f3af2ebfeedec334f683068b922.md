```
#include "stdio.h"
char x,y;
int i;
void main(){
    for (x='A';x<='F';x++){
        // 前六行
        for (y=x;y<='I';y++) printf(" %c",y);
        for (y='A';y<x;y++) printf(" %c",y);
        for(i=1;i<=(5-(x-'A'))*2);i++) printf(" ");
        for(i=1;i<=2*(x-'A')+1;i++) printf(" %c",x);
        for(i=1;i<=(5-(x-'A'))*2);i++) printf(" ");
        for (y=x+1;y<='T';y++) printf(" %c",y);
        for (y='A';y<=x;y++) printf(" %c",y);
        printf("\n");
    }
}
```