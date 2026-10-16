```
if(fabs(a)<=1e-6)
    printf("is not a quadratic") ;
else
{disc=b*b-4*a*c;
if(fabs(disc)<=1e-6)
    printf("has two equal roots:%8.4f\n",-b/(2*a));
else if( disc>1e-6)
{ x1=(-b+sqrt(disc))/(2*a);
x2=(-b-sqrt(disc))/(2*a);
打印实根(略);
}
else
{ realpart=-b/(2*a);
imagpart=sqrt(-disc)/(2*a);
printf("has complex roots:\n") ;
打印虚根(略);
}
}
```