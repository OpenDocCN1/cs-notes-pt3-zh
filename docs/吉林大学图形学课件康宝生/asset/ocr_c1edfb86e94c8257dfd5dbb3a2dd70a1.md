```
void polygonc(int x0, int y0, int r,
int n, float af) {
int x, y, xs, ys, i;
float dtheta, theta;
if(n<3) return;
dtheta = 6.28314/n;
theta=af*0.0174533;
xs = x0 + r*cos(theta);
ys = y0 + r*sin(theta);
moveto(xs,ys);
for(i=1; i<n; i++) {
theta+=dtheta; x=x0+r*cos(theta);
y=y0+r*sin(theta); lineto(x,y); }
lineto(xs,ys);
}
```

```
void block (int x,int y,int a,int n, int theta){
int x0, y0, i, r; float t, f, af=45.0;
t = fabs(theta*0.0174533);
f=1.0/(cos(t)+sin(t));
r=a/1.414;
x0=x+0.5*a; y0=y-0.5*a;
for(i=1;i<=n;i++) {
polygonc(x0, y0, r, 4, af);
r=r*f; af=af+theta;
} }
```