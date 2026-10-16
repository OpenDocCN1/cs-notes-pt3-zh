$d_1=y-\dot{y}_i=m(\dot{x}_i+1)+b-\dot{y}_i$

$d_2=(\dot{y}_i+1)-y=(\dot{y}+1)-m(\dot{x}_i+1)-b$

$d_1-d_2=2m(\dot{x}_i+1)-2\dot{y}_i+2b-1$

$d_1>d_2$，下一个象素点取 $(\dot{x}_i+1,\dot{y}_i+1)$

$d_1<d_2$，下一个象素点取 $(\dot{x}_i+1,\dot{y}_i)$

$d_1=d_2$，取两象素点中的任意一个