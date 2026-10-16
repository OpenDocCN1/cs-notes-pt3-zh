
## Representation of Geometric Constructs

- line segment

  ```
  {(x1,y1), (x2,y2)}
  ```

- triangle

  ```
  {(x1,y1), (x2,y2), (x3,y3)}
  ```

- polygon

  ```
  {(x1,y1), (x2,y2), (x3,y3), (x4,y4), (x5,y5)}
  ```

- polygon

  ```
  {(x1,y1), (x2,y2), (x3,y3), ID1}
  ```

  ```
  {(x1,y1), (x4,y4), (x5,y5), ID1}
  ```

- object representation

## Representation of Geometric Information (Cont.)

- Representation of points and line segments in 3-D is similar to 2-D, except that points have an extra z component.
- Represent arbitrary polyhedra by dividing them into tetrahedrons, like triangulating polygons.
- Alternative: List their faces, each of which is a polygon, along with an indication of which side of the face is inside the polyhedron.

## Design Databases

- Represent design components as objects (generally geometric objects); the connections between the objects indicate how the design is structured.
- Simple two-dimensional objects: points, lines, triangles, rectangles, polygons.
- Complex two-dimensional objects: formed from simple objects via union, intersection, and difference operations.
- Complex three-dimensional objects: formed from simpler objects such as spheres, cylinders, and cuboids by union, intersection, and difference operations.
- Wireframe models represent three-dimensional surfaces as a set of simpler objects.

## Representation of Geometric Constructs

![](img/00bedbdd4ee0b6a84e67d550b5b9ee64_1345_0.png)

![](img/00bedbdd4ee0b6a84e67d550b5b9ee64_1345_1.png)

(a) Difference of cylinders

(b) Union of cylinders

- Design databases also store non-spatial information about objects (e.g., construction material, color, etc.)
- Spatial integrity constraints are important.
  - E.g., pipes should not intersect, wires should not be too close to each other, etc.

## Geographic Data

![](img/00bedbdd4ee0b6a84e67d550b5b9ee64_1346_0.png)

- **Raster data** consist of bit maps or pixel maps, in two or more dimensions.
  - Example 2-D raster image: satellite image of cloud cover, where each pixel stores the cloud visibility in a particular area.
  - Additional dimensions might include the temperature at different altitudes at different regions, or measurements taken at different points in time.
- Design databases generally do not store raster data.
- **Vector data** are constructed from basic geometric objects: points, line segments, triangles, and other polygons in two dimensions, and cylinders, spheres, cuboids, and other polyhedrons in three dimensions.
- Vector format is often used to represent map data.
  - Roads can be considered as two-dimensional and represented by lines and curves.
  - Some features, such as rivers, may be represented either as complex curves or as complex polygons, depending on whether their width is relevant.
  - Features such as regions and lakes can be depicted as polygons.

## Spatial Queries

- **Nearness queries** request objects that lie near a specified location.
- **Nearest neighbor queries**, given a point or an object, find the nearest object that satisfies given conditions.
- **Region queries** deal with spatial regions (e.g., ask for objects that lie partially or fully inside a specified region).
- Queries that compute intersections or **unions** of regions.
- **Spatial join** of two spatial relations with the location playing the role of join attribute.

![](img/00bedbdd4ee0b6a84e67d550b5b9ee64_1349_0.png)

- Spatial data is typically queried using a graphical query language; results are also displayed in a graphical manner.
- Graphical interface constitutes the front-end.
- Extensions of SQL with abstract data types, such as lines, polygons and bit maps, have been proposed to interface with the back-end.
  - allows relational databases to store and retrieve spatial information
  - Queries can use spatial conditions (e.g., contains or overlaps).
  - Queries can mix spatial and nonspatial conditions.

![](img/00bedbdd4ee0b6a84e67d550b5b9ee64_1350_0.png)
