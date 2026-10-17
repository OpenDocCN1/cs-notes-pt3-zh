# # Crude texture mapping code

```
// for each vertex we have x,y,z and u,v
for (x=xleft; x < xright; x++) {
    if (z < zbuffer[x][y] ) {
        z[x][y] = z;
        raster[x][y] = texture[u][v]; // replacing color
    }
    z=z+dz;
    u=u+dv;
    v=v+dv;
}
```