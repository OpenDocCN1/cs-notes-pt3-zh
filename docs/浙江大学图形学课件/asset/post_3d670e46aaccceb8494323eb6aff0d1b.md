

## Maintaining Aspect Ratio

scaleFactor = screenHeight / windowHeight

scaleFactor = screenWidth / windowWidth

![](img/94fd648dd12ff5c2cbed197b5038ba1a_276_0.png)

![](img/94fd648dd12ff5c2cbed197b5038ba1a_276_1.png)

![](img/94fd648dd12ff5c2cbed197b5038ba1a_276_2.png)

![](img/94fd648dd12ff5c2cbed197b5038ba1a_276_3.png)

## OpenGl Commands

### gluOrtho2D( left, right, bottom, top )

Creates a matrix for projecting 2D coordinates onto the screen and multiplies the current matrix by it.

### glViewport( x, y, width, height )

Define a pixel rectangle into which the final image is mapped.
(x, y) specifies the lower-left corner of the viewport.
(width, height) specifies the size of the viewport rectangle.

## 2D Rendering-1

```c
void myReshape(GLsizei w, GLsizei h)
{
    glViewport(0, 0, w, h); // 设置视口

    glMatrixMode(GL_PROJECTION); // 指明当前矩阵为 GL_PROJECTION
    glLoadIdentity(); // 将当前矩阵置换为单位阵

    // 定义二维正视投影矩阵
    if (w <= h)
        gluOrtho2D(-1.0, 1.5, -1.5, 1.5 * (GLfloat)h / (GLfloat)w);
    else
        gluOrtho2D(-1.0, 1.5 * (GLfloat)w / (GLfloat)h, -1.5, 1.5);

    glMatrixMode(GL_MODELVIEW); // 指明当前矩阵为 GL_MODELVIEW
}
```

## 2D Rendering-2

```c
void myDisplay(void)
{
    glClear(GL_COLOR_BUFFER_BIT); // buffer 设置为颜色可写

    glBegin(GL_TRIANGLES); // 开始画三角形
    glShadeModel(GL_SMOOTH); // 设置为光滑明暗模式

    glColor3f(1.0, 0.0, 0.0); // 设置第一个顶点为红色
    glVertex2f(-1.0, -1.0); // 设置第一个顶点的坐标为 (-1.0, -1.0)

    glColor3f(0.0, 1.0, 0.0); // 设置第二个顶点为绿色
    glVertex2f(0.0, -1.0); // 设置第二个顶点的坐标为 (0.0, -1.0)

    glColor3f(0.0, 0.0, 1.0); // 设置第三个顶点为蓝色
    glVertex2f(-0.5, 1.0); // 设置第三个顶点的坐标为 (-0.5, 1.0)
    glEnd(); // 三角形结束

    glFlush(); // 强制 OpenGL 函数在有限时间内运行
}
```

## 2D Rendering-3

![](img/94fd648dd12ff5c2cbed197b5038ba1a_280_0.png)

![](img/94fd648dd12ff5c2cbed197b5038ba1a_281_0.png)

## User Interactions

### *Panning*

![](img/94fd648dd12ff5c2cbed197b5038ba1a_282_0.png)

![](img/94fd648dd12ff5c2cbed197b5038ba1a_282_1.png)

> *Zoom Out*

> *Zoom In*

## Modelling vs Viewing

- **Viewing transformations** are not same as **modelling transformations**
- *Modeling transformations* actually position the objects in the world, but *viewing transformations* are applied only to make a mapping from world to the screen
- *Viewing transformations* do not change the actual world in any fashion

## Modelling Coordinates

![](img/94fd648dd12ff5c2cbed197b5038ba1a_284_0.png)

Objects are usually defined in their own local coordinate system (instance transformation).

Place (transform) these objects in a single scene, in world coordinates (modelling transformation).

## Screen Coordinates

![](img/94fd648dd12ff5c2cbed197b5038ba1a_285_0.png)

Finally, we want to project these objects onto the screen.

## 3D Viewing

- Aim is to display a *3D world* onto a *2D screen*
- Specification becomes complicated because there are many parameters to control
- Additional task of reducing dimensions from 3D to 2D (projection)
- 3D viewing is analogous to taking a picture with a camera

## The Pinhole Camera

### Camera Obscura Leonardo da Vinci

The principle upon which all camera equipment works is traced to artist / inventor Leonardo da Vinci who showed that all that was needed to project an image was a small pinhole through which light could pass. The smaller the hole the sharper the image.

The basic camera, called a pinhole camera, existed in the early 17th Century. It took much longer for science to find a light sensitive material to record the image. It was not until 1826 when Joseph Niepce from France discovered that silver chloride （氯化 银） could be used to make bitumen sensitive to light.

![](img/94fd648dd12ff5c2cbed197b5038ba1a_288_0.png)

![](img/94fd648dd12ff5c2cbed197b5038ba1a_288_1.png)

## Transformations and Camera Analogy

- **Modeling transformation**
  - Shaping, positioning and moving the objects in the world scene.
- **Viewing transformation**
  - Positioning and pointing camera onto the scene, selecting the region of interest.
- **Projection transformation**
  - Adjusting the distance of the eye
- **Viewport transformation**
  - Enlarging or reducing the physical photograph.

