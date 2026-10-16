```
```c
void mul(int a[],int b[],int c[],int n){
    int m[2*L];
    int i,j,k,l,pos,sign,tmp;
    for(i=0;i<2*L;i++){
        c[i]=0; m[i]=0;
    }
    for(i=0;i<n;i++){
        pos=0; sign=0;
        for(j=0;j<n;j++){
            tmp=b[j]*a[i]+sign;
            m[pos]=tmp%10;
            sign=tmp/10;
            pos++;
        }
        m[pos]=sign;
```
```