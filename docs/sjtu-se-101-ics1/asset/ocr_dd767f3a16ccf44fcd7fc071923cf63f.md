# Structure

```
int area (struct rect *rp)
{
    return (*rp).width * (*rp).height;
}

void rotate_left (struct rect *rp)
{
    /* Exchange width and height */
    int t = rp->height;
    rp->height = rp->width;
    rp->width = t;
}
```