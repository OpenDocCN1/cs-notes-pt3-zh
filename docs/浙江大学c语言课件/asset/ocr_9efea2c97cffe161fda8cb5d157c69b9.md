# # 7.6 Line Input and Output

```
char *fgets(char *s, int n, FILE *iop)
{	register int c;
	register char *cs;
	cs=s;
	while(--n > 0 && (c=getc(iop))!= EOF)
		if((*cs++ = c)=='\n')
			break;
	*cs='\0';
	return (c==EOF && cs == S)? NULL : s;
}
int fputs(char *s, FILE *iop)
{	int c;
	while( c =*s++)
		putc(c,iop);
	return ferror(ip) ? EOF : 0;
}
```