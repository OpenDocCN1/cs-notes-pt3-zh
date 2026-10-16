```
/*输出检索结果函数*/
void out_ans er(struct bookcard card){
    int i,j,k;
    printf("NAME:%s\n", card.name );
    printf("AUTHOR:%s\n", card.author);
    printf("LANGUGE:%s\n", card.languge );
    printf("Publish date:%d-%d-%d"
        ,card.publishdate.year
        ,card.publishdate.month
        ,card.publishdate.day);
    printf("ABSTRACT:\n" );
    for ( i=0; i<3; i++ ) {
        printf("    ");
        for ( k=1; k<=64; k++ )
            printf("%c",card.abstract[64*i+j] );
        printf("\n");
    }
}
```