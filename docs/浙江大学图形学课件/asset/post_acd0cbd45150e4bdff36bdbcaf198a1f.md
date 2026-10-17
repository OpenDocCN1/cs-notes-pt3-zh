

## OpenGL Perspective

```c
glFrustum(left, right, bottom, top, near, far);
```

![](img/94fd648dd12ff5c2cbed197b5038ba1a_325_0.png)

```c
glMatrixMode(GL_PROJECTION);
```

```c
glLoadIdentity();
```

```c
glFrustum(left, right, bottom, top, near, far);
```

## OpenGL Perspective

gluPerspective(fovy, aspect, near, far);

![](img/94fd648dd12ff5c2cbed197b5038ba1a_326_0.png)

fov is the angle between the top and bottom planes

## gluPerspective(fovy, aspect, near, far)

```c
{
    GLdouble m[4][4];
    double sine, cotangent, deltaZ;
    double radians = fovy / 2 * __glPi /
        180;

    deltaZ = zFar - zNear;
    sine = sin(radians);
    if ((deltaZ == 0) || (sine == 0) ||
        (aspect == 0)) {
        return;
    }
    cotangent = cos(radians) / sine;

    __gluMakeIdentity(&m[0][0]);
    m[0][0] = cotangent / aspect;
    m[1][1] = cotangent;
    m[2][2] = -(zFar + zNear) / deltaZ;
    m[2][3] = -1;
    m[3][2] = -2 * zNear * zFar / deltaZ;
    m[3][3] = 0;
    glMultMatrixd(&m[0][0]);
}
```

## A More Intuitive Approach Offered by glu:

```c
gluLookAt(eyex, eyey, eyez, atx, aty,
atz,
upx, upy, upz);
```

eyex, eyey, eyez specify the position of the eye point and are mapped to the origin.

atx, aty, atz specify a point being looked at, which will be rendered in center of view port. It is mapped to the -z axis.

upx, upy, upz specify components of the camera up vector.

## gluLookAt

```c
{
float forward[3], side[3], up[3];
GLfloat m[4][4];

forward[0] = centerx - eyex;
forward[1] = centery - eyey;
forward[2] = centerz - eyez;
up[0] = upx;
up[1] = upy;
up[2] = upz;

normalize(forward);

/* Side = forward x up */
cross(forward, up, side);
normalize(side);

/* Recompute up as: up = side x forward */
/* */
cross(side, forward, up);

__gluMakeIdentityf(&m[0][0]);
m[0][0] = side[0];
m[1][0] = side[1];
m[2][0] = side[2];

m[0][1] = up[0];
m[1][1] = up[1];
m[2][1] = up[2];

m[0][2] = -forward[0];
m[1][2] = -forward[1];
m[2][2] = -forward[2];

glMultMatrixf(&m[0][0]);
glTranslated(-eyex, -eyey, -eyez);
}
```

63

## Ex3

- Switch between orthographic and perspective camera
- Moving the camera with arrow keys

![](img/94fd648dd12ff5c2cbed197b5038ba1a_330_0.png)

## THANK YOU

## Viewing in 2D/3D

## Viewing

- Goal is to visualize information (3D worlds, scientific results, mathematical functions) as images, animations and virtual walkthroughs

**VIEWING** becomes fundamental

- By viewing we mean transforming the objects from the world coordinates (2D, 3D .... ) to eye coordinates to device/screen coordinates (usually 2D).

## 2D Viewing

- By applying **appropriate transformations** we can map the world seen through the window on to the screen

![](img/94fd648dd12ff5c2cbed197b5038ba1a_335_0.png)

## 2D World

![](img/94fd648dd12ff5c2cbed197b5038ba1a_335_1.png)

## Screen

## 2D Viewing Transformation

- Mapping the 2D world seen in the **window** on to the **viewport** is 2D **viewing transformation** also called **window to viewport transformation**

![](img/94fd648dd12ff5c2cbed197b5038ba1a_336_0.png)

## Deriving 2D Viewing Transformation

$$\frac{v_x-vx_L}{vx_R-vx_L}=\frac{w_x-wx_L}{wx_R-wx_L}$$
$$\frac{v_y-vy_B}{vy_T-vy_B}=\frac{w_y-wy_B}{wy_T-wy_B}$$

$$v_x=\frac{vx_R-vx_L}{wx_R-wx_L}\cdot(wx-wx_L)+vx_L$$
$$v_y=\frac{vy_T-vy_B}{wy_T-wy_B}\cdot(wy-wy_B)+vy_B$$

## OpenGL Commands

| Command | Description |
|---|---|
| **gluOrtho2D( left, right, bottom, top )** | Creates a matrix for projecting 2D coordinates onto the screen and multiplies the current matrix by it. |

| Command | Description |
|---|---|
| **glViewport( x, y, width, height )** | Define a pixel rectangle into which the final image is mapped.  
(x, y) specifies the lower-left corner of the viewport.  
(width, height) specifies the size of the viewport rectangle. |

