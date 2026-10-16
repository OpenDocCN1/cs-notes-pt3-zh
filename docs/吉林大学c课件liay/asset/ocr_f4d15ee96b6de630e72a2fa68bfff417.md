# I/O类

```
#include <iostream>
using namespace std;
class aa{
    float a;  float b;
public:
    float &aaa(){return(a);}
    float &bbb(){return(b);} };
ostream & operator <<(ostream &out,aa &a)
{ out<<a.aaa()<<a.bbb()<<endl;
    return(out);
}
void main()
{ aa a;
    a.aaa()=1; a.bbb()=2;
    cout<<a;}
```