# # Four bit carry look ahead adder

Then we get:
c4=G0+P0*c0 ; c8=G1+P1*c4
c12=G2+P2*c8 ; c16=G3+P3*c12
Assume:C1=c4,C2=c8,C3=c12,C4=c16
Then:
C1=G0+P0*c0 ; C2=G1+P1*C1
C3=G2+P2*C2 ; C4=G3+P3*C3
And,we can further get:
C1=G0+P0*c0 ;
C2= G1+P1*C1 = G1+P1*G0+ P1* P0*c0
C3=G2+P2*C2 = G2+P2*G1 + P2* P1*G0+ P2* P1* P0*c0
C4=G3+P3*C3= G3+P3*G2+P3*P2*G1+P3*P2*P1*G0+P3*P2*P1* P0*c0