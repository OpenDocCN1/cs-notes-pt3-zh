友元

引入

```
class aa{
    float a;  float b;
public:
    float &aaa(){return(a);}
    float &bbb(){return(b);}
};
aa sum(aa a,aa b)
{ aa c;
 c.aaa()=a.aaa()+b.aaa(); c.bbb()=a.bbb()+b.bbb();
    return(c);
}
void main()
{ aa a,b;
    a.aaa()=1; a.bbb()=2;  b.aaa()=3; b.bbb()=4;
    aa c=sum(a,b);
    cout<<c.aaa()<<endl<<c.bbb();
    for(long i=0;i<100000;i++) cout<<a.aaa()<<endl;
```