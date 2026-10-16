```
if(fp1==NULL)
{ printf("can not open this file\n");
    exit(0);
}
printf("please input file2's name:");
scanf("%s",file2);
fp2=fopen(file2,"w");
if(fp2==NULL)
{ printf("can not open this file\n");
    exit(0);
}
ch=fgetc(fp1);
while(ch!=EOF)
    { fputc(ch,fp2); ch=fgetc(fp1); }
fclose(fp1);
fclose(fp2);
}
```