```
/*已知四点，求两条直线交点*/
void intersection(float rx,float ry,float sx,float sy ,
float tx,float ty,float ux,float uy ,
float *hx, float *hy){
	float l1_a,l1_b,l2_a,l2_b;/* 两条直线的斜率和截距 */
	equation(rx,ry,sx,sy,tx,ty,ux,uy ,
		&l1_a,&l1_b,&l2_a,&l2_b);
	inter(l1_a,l1_b,l2_a,l2_b,hx,hy);
}
```