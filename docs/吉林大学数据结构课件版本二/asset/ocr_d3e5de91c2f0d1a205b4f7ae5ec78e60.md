```
while(flag==1)
{
printf("\n\n\n1:queue 2:seedoctor 3:seequeue 0:stopwork please select:");
scanf("%d",&sel);
switch(sel)
{
case 0:if(q->front!=q->rear)
printf("\nplease see doctor tomorrow!");
flag=0;
break;
```