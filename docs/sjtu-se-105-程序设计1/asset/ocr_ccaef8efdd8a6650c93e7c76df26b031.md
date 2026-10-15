```
Matrix* trouble( Matrix *pm ){
    Matrix res;
    ...
    return &res;      //error
}
int main()
{
    Matrix m1;
    // ...
    Matrix* mainResult = trouble( &m1 ); //悬空指针
    // ...
}
```