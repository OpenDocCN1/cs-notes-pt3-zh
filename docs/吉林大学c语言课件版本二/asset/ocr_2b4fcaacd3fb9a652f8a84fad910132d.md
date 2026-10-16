```
void C(int i){
    if(i>0){
        B(i-1);x+=len;lineto(x,y);
        C(i-1);y+=len;lineto(x,y);
        C(i-1);x-=len;lineto(x,y);
        D(i-1);
    }
}
void D(int i){
    if(i>0){
        A(i-1);y-=len;lineto(x,y);
        D(i-1);x-=len;lineto(x,y);
        D(i-1);y+=len;lineto(x,y);
        C(i-1);
    }
}
```