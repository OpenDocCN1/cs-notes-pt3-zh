```
```c
void swap(int *xx, int *yy){
    int temp;
    temp=*xx;
    *xx=*yy;
    *yy=temp;
}
void main(){
    int x,y;
    scanf("%d %d", &x,&y);
    if(x<y)
        swap(&x,&y);
    printf("\n%d\t%d\n",x,y);
}
```
```

![](bbox=[0.466, 0.119, 0.999, 0.713])