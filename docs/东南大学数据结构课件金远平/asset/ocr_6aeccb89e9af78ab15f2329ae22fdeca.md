```
26   rq=rn[q];
27   // reconstruct the tree of losers
28   for (int t=(k+q)/2;t; t/=2) // t is initialized to be parent of q
29     if (rn[l[t]]<rq || rn[l[t]]==rq && r[l[t]]<r[q])
30     { // t is the winner
31       swap(q, l[t]);
32       rq = rn[q];
33     }
34   } // end of while
35   delete [] r; delete [] rn; delete [] l;
36}
```