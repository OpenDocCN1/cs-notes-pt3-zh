```
/* 翻译函数 */
bool convert(){
    char ch;
    float g;
    intflag=true;
    ch=getchar();
    /*滤掉前导空白字符*/
    while(ch==' ')
        ch=getchar();
    /*翻译整数部分*/
    n=0;
    while( isdigit(ch) ){
        n=n*radix + calculate_char(ch) ;
        ch=getchar();
    }
}
```