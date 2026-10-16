```
bool want(){
    int x=0,y=0,z=0; char ch;
    do{   ch=getchar();
        switch(ch){
        case'{':x++;break;
        case'}':x--;break;
        case'[':y++;break;
        case']':y--;break;
        case'(':z++;break;
        case')':z--;   break;
        }
    }while(ch!='\r'&&ch!='\n');
    if(x!=0||y!=0||z!=0){
        if(x!=0)printf("{\ is wrong!\n");
        if(y!=0)printf("[\ is wrong!\n");
        if(z!=0)printf("(\ is wrong!\n"); return false;
    }else return true;
}
```