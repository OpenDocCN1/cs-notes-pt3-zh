# Strcpy使用举例：

```
#include <iostream.h>
#include<fstream.h>
main()
{char filewing[20]="wing.txt",filefuse[20]="fuselage.txt",filetail[20]="tail.txt";
    cout<<"请输入飞机部件类型"<<"\n";
    cout<<"1----机翼"<<"\n";
    cout<<"2----机身"<<"\n";
    cout<<"3----尾翼"<<"\n";
    cin>>numpart;
    switch(numpart)
    case 1: {strcpy(filedes,filewing); break;}
    case 2: {strcpy(filedes,filefuse); break;}
    case 3: {strcpy(filedes,filetail); break; }
    case 4: default;
    ifstream in(filedes,ios::in);
    if(!in){cout<<"cannot open Inputfile "<<"\n";exit(1);}
}
```