# 例8-11 用4*3指针数组保存每个月份名称

```
char * mp( char *[4][3] ,int );
int main(void){
    char * name[][3]={
        {"Jan","Feb","Mar"},
        {"Apr","May","Jun"},
        {"Jul","Aug","Sep"},
        {"Oct","Nov","Dec"} }
    char *p ;
    int  m ;
    printf("Inputer a number of month:"); /*读入月份*/
    scanf("%d",&m);
    p=mp( name, m );                 /*求月份字符串指针*/
    printf( "the %dth month is%s\n", m , p );  /*输出*/
}
```