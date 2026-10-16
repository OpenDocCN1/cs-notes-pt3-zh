```
main()
{
    int pid1,pid2,pid3,pid4,pid5,pid6,pid7,pid8;
    int end_p1=end_p2=end_p3=end_p4=end_p5=...=end_p8=0;
    int pid, status;

    if((pid1=fork())==0) execl("P1",0);
    wait(&status);
    if((pid2=fork())==0) execl("P2",0);
    if((pid3=fork())==0) execl("P3",0);
    if((pid4=fork())==0) execl("P4",0);
    do{    //等待P2结束
        pid=wait(&status);
        if(pid==pid2) end_p2=1;
        if(pid==pid3) end_p3=1;
        if(pid==pid4) end_p4=1;
    }while(end_p2==0);
```