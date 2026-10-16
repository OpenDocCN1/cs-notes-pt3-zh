```
void main(void)
{
    Student g= {1000, 23};
    Store<int> S1, S2;
    Store<Student> S3;
    Store<double> D;

    S1.PutElem(3);
    S2.PutElem(-7);
    cout << S1.GetElem() << "  " <<
    S2.GetElem() << endl;
```