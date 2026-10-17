# # 7.5 File Access

eg1: file copy
#include <stdio.h>
main(int argc, char *argv[])
{	FILE *fp1, *fp2;
if(argc!=3)
{	printf("Usage: copy f1 f2\n");	exit(1);
}
if((fp1=fopen(argv[1]))==NULL || ((fp2 = fopen(argv[2]))=NULLL)
{	printf("Can't open file!\n");	exit(2);
}
while(putc(getc(fp1),fp2)!=EOF)
;
fclose(fp1);
fclose(fp2);
}