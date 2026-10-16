```
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

234E temp 3
程序输出：6 3
234A yy 2342
2346 xx 2340
swap 2344 返回值
main 2342 y 3
2340 x 6