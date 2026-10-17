

## Rotation (cont.)

Rotation about an axis which parallel to X or Y or Z:

- Translate the object to make $\vec{oz}$ superpose $OZ$.
- Rotate the objects about Z axis.
- Translate the object back to original state.

![](img/258e4144ed4b66c8fd4b0f298118df23_166_0.png)

## Rotation (cont.)

Rotation about an arbitrary axis which passes through origin:

![](img/258e4144ed4b66c8fd4b0f298118df23_167_0.png)

$\vec{k}=(A_x,A_y,A_z)$

- Build a new coordinate system $O\bar{X}\bar{Y}\bar{Z}$, the $O\bar{Z}$ is in the direction of $\vec{k}$.
- Transform the objects from $OXYZ$ to $O\bar{X}\bar{Y}\bar{Z}$.
- Rotate the objects about $O\bar{Z}$ axis.
- Transform the objects from $O\bar{X}\bar{Y}\bar{Z}$ back to $OXYZ$.

## The order of transformations

- Matrix multiplication is not commutative, the sequence of transformations is significant.

![](img/258e4144ed4b66c8fd4b0f298118df23_168_0.png)

## 3D Scaling

- Scaling is an non-rigid-body transformation

$$\begin{bmatrix}x'\\y'\\z'\end{bmatrix}=\begin{bmatrix}S_x&0&0\\0&S_y&0\\0&0&S_z\end{bmatrix}\begin{bmatrix}x\\y\\z\end{bmatrix}$$

![](img/258e4144ed4b66c8fd4b0f298118df23_169_0.png)

![](img/258e4144ed4b66c8fd4b0f298118df23_169_1.png)

Scaling can make an object bigger or smaller, as shown in the left figure, which illustrates both uniform scaling in **all** directions and scaling in a **single** direction.

## Homogeneous coordinates

$$\begin{bmatrix}x''\\y''\\z''\end{bmatrix}=\begin{bmatrix}S_x&0&0\\0&S_y&0\\0&0&S_y\end{bmatrix}A^T\begin{bmatrix}\cos\alpha&-\sin\alpha&0\\\sin\alpha&\cos\alpha&0\\0&0&1\end{bmatrix}A\begin{bmatrix}x\\y\\z\end{bmatrix}$$

T, Unfortunately, it is not available, if there is a translation in it.

## Homogeneous coordinates:

$$P(x,y,z)\Rightarrow P(wx,wy,wz,w)$$

$$\begin{bmatrix}x'\\y'\\z'\\1\end{bmatrix}=\begin{bmatrix}1&0&0&\Delta x\\0&1&0&\Delta y\\0&0&1&\Delta z\\0&0&0&1\end{bmatrix}\begin{bmatrix}x\\y\\z\\1\end{bmatrix}$$

## Viewing Position

![](img/258e4144ed4b66c8fd4b0f298118df23_172_0.png)

- To choose a part of the world we want to draw, we have to specify where the viewer is located.
- Also defines where you are calculating and measuring from.

## Viewing Coordinate System

eye position - origin
\(\vec{n}\) - viewing direction

\(\vec{v}\) - viewing vertical direction
\(\vec{u}\) - viewing horizontal direction

define the viewing plane

![](img/258e4144ed4b66c8fd4b0f298118df23_173_0.png)

## Local coordinate

![](img/258e4144ed4b66c8fd4b0f298118df23_174_0.png)

## World coordinate

![](img/258e4144ed4b66c8fd4b0f298118df23_175_0.png)

## Camera

![](img/258e4144ed4b66c8fd4b0f298118df23_176_0.png)

## Viewing coordinate

![](img/258e4144ed4b66c8fd4b0f298118df23_177_0.png)

## Projections

- A projection is a mathematical technique (function) for converting a system of n-D points into an (n-1)-D space

![](img/258e4144ed4b66c8fd4b0f298118df23_178_0.png)

## Projections

- It is defined by straight projection rays (**projectors**) emanating from **a center of projection**, passing through each point of the object, and intersecting a **projection plane** to form the projection

![](img/258e4144ed4b66c8fd4b0f298118df23_179_0.png)

![](img/258e4144ed4b66c8fd4b0f298118df23_179_1.png)

## Projections (cont.)

- If the distance from the center of projection to the projection plane is finite, the projection is **perspective**; if the distance is infinite, the projection is **parallel**.

![](img/258e4144ed4b66c8fd4b0f298118df23_180_0.png)

## Perspective projection

![](img/258e4144ed4b66c8fd4b0f298118df23_181_0.png)

## Perspective projection

![](img/258e4144ed4b66c8fd4b0f298118df23_182_0.png)

## Parallel projection

![](img/258e4144ed4b66c8fd4b0f298118df23_183_0.png)

## Parallel projection

![](img/258e4144ed4b66c8fd4b0f298118df23_184_0.png)

