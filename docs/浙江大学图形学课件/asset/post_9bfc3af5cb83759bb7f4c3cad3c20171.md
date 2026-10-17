

## Surface Normals

Taking the derivatives of a function with respect to one of the arguments gives us “partial derivatives”. If f(u,v) is the function then

\(\frac{\partial f}{\partial u}, \frac{\partial f}{\partial v}, \frac{\partial^2 f}{\partial u^2}, \frac{\partial^2 f}{\partial v^2}, \frac{\partial^2 f}{\partial u \partial v}\)

etc. are partial derivatives

![](img/94fd648dd12ff5c2cbed197b5038ba1a_155_0.png)

Normal is given by:
\((\frac{\partial f}{\partial u} X \frac{\partial f}{\partial v})\)

## Piecewise Linear Representations

Any curve can be approximated by a connected sequence of line segments. Similarly any surface can be approximated by a connected set of planar polygonal faces.

![](img/94fd648dd12ff5c2cbed197b5038ba1a_156_0.png)

## Meshes from Scanning

- Laser scanners sample 3D positions
  - One method uses time of flight
  - Some take images also for use as textures
  - Famous example: Scanning the David
- Software then takes thousands of points and builds a polygon mesh out of them
- Research topics:
  - Reduce the number of points in the mesh
  - Reconstruction and re-sampling!

## Picture

![](img/94fd648dd12ff5c2cbed197b5038ba1a_158_0.png)

http://www-graphics.stanford.edu/projects/mich

## Normal Vectors

- Normal vectors give information about the true surface shape
- Per-Face normals:
  - One normal vector for each face, stored as part of face
  - Flat shading
- Per-Vertex normals:
  - A normal specified for every vertex (smooth shading)

## Computing Normal Vectors

- Many models do not come with normals
  - Models from laser scans are one example
- Per-Face normals are easy to compute:
  - Normalize cross product of two edges
- For per-vertex normals:
  - Compute per-face normals
  - Average normals of faces surrounding vertex
    - A case where neighbor information is useful

## End.

## 2D Graphics Algorithms

## Rasterization

- The task of displaying a world modelled using primitives like lines, polygons, filled/patterned areas, etc. can be carried out in two steps
  - determine the pixels through which the primitive is visible, a process called **Rasterization or scan conversion**
  - determine the color value to be assigned to each such pixel.

## Rasterization

![](img/94fd648dd12ff5c2cbed197b5038ba1a_164_0.png)

## Why Study these Algorithms?

- Some of these algorithms are very good examples of clever algorithmic optimization done to dramatically improve performance using minimal hardware facilities.

## Scan Converting a Line Segment

- The line is a powerful element used since the days of Euclid to model the edges in the world.

![](img/94fd648dd12ff5c2cbed197b5038ba1a_167_0.png)

- Given a line segment defined by its endpoints determine the pixels and colour which best model the line segment.

## Scan converting lines

start from $(x_1, y_1)$ end at $(x_2, y_2)$

![](img/94fd648dd12ff5c2cbed197b5038ba1a_168_0.png)

## Question1: How ?

$(x_1, y_1), (x_2, y_2)$

$y=mx+b$

$x_1+1 \rightarrow y=?, Rounding$

$x_1+2 \rightarrow y=?, rounding \quad \longrightarrow \quad x_1+i \rightarrow y=?, rounding$

## Question2: How to speed up?

![](img/94fd648dd12ff5c2cbed197b5038ba1a_170_0.png)

## Equation of a Line

- Equation of a line is **y - m.x + c = 0**
- For a line segment joining points **P(x1,y2)** and **P(x2,y2)**

*slope* \(m = \frac{y2-y1}{x2-x1} = \frac{\Delta y}{\Delta x}\)

- Slope **m** means that for every unit increment in X the increment in Y is *m* units

![](img/94fd648dd12ff5c2cbed197b5038ba1a_171_0.png)

## Digital Differential Analyzer (DDA)

- We consider the line in the first octant. Other cases can be easily derived.
- Uses differential equation of the line

\( y_i=m \cdot x_i+c \)

where, \( m=\frac{y2-y1}{x2-x1} \)

- Incrementing X-coordinate by 1

\( x_i=x_{i\_prev}+1 \)

\( y_i=y_{i\_prev}+m \)

- Illuminate the pixel \( [x_i,round(y_i)] \)

![](img/94fd648dd12ff5c2cbed197b5038ba1a_172_0.png)

Discussion1: What technique makes it faster?
Discussion2: Is there any problem in the algorithm?
How to avoid it?

