```
int index(string S,string T,int pos)
{
    if(pos>0){
        n=strlen(s);  m=strlen(t);  i=pos;
        while(i<=n-m+1){
            substr(sub,S,i,m);
            if(strcmp(sub,T)!=0)++i;
            else return(i);
        }
    }
    return(0);
}
```