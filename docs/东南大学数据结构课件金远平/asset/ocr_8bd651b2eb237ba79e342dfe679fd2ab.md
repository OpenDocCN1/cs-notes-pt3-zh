```
1 void String::Failurefunction()
2 { // compute the failure function of the pattern *this.
3   int LengthP= Length( );
4   f[0]= -1;
5   for (int j=1; j< LengthP; j++) // compute  f[j]
6   {
7     int i=f[j-1];
8     while ((* (str+j)!=*(str+i+1)) && (i>=0)) i=f[i]; // try for m
9     if ( *(str+j)==*(str+i+1))
10      f[j]=i+1;
11   else f[j]= -1;
12  }
13 }
```