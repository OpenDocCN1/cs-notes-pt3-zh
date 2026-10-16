```
```c
1 main(int argc, char *argv[])
{
    int i;
    printf("The program name is:%s\n", argv[0]);
    if (argc > 1){
        printf("The other arguments are following:\n");
        for (i = 1; i<argc; i++)
        {
            printf("%s\n", argv[i]);
        }
    }
}
```
```