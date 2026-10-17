

## Nuxt 3

Nuxt is an open source framework making web development intuitive and powerful.

Create dynamic and performant full-stack applications with incredible developer experience.

- **Hybrid**: Different rendering modes per route.
- **File-based routing**: Create routes based on your Vue components.
- **Auto-imports**: Use composables and components without importing.
- **SEO & a11y**: Improve your website SEO and accessibility.

Nuxt is a free and open-source framework with a vibrant ecosystem. It is also a fully customizable framework with more than 50 modules to use in your application.

![](img/94fd648dd12ff5c2cbed197b5038ba1a_590_0.png)

```bash
npm create nuxt
```

Get started in seconds with `npm create nuxt` — no configuration needed.

> Nuxt 3 is the newest version. It's fast, reliable, and full-featured. Try it today!

- Explore official documentation
- Join the community
- View source code on GitHub

## Cube Mapping

- The map resides on the surfaces of a cube around the object
  - Typically, align the faces of the cube with the coordinate axes
- To generate the map:
  - For each face of the cube, render the world from the center of the object with the cube face as the image plane
    - Rendering can be arbitrarily complex (it’s off-line)
  - Or, take 6 photos of a real environment with a camera in the object’s position
- Assume the cube’s faces are aligned with the coordinate axes, and have texture coordinates in [0,1]x[0,1]. Main issue is to decide
  - which face to use, and
  - decide which texture coordinates to use.
  - Use a ray from the centre; only cube corners and edges will need special attention

## Bump Mapping

Bump Mapping assumes that the Illumination model is applied at every pixel (as in Phong Shading or ray tracing).

![](img/94fd648dd12ff5c2cbed197b5038ba1a_592_0.png)

![](img/94fd648dd12ff5c2cbed197b5038ba1a_592_1.png)

![](img/94fd648dd12ff5c2cbed197b5038ba1a_592_2.png)

Sphere w/Diffuse Texture

Swirly Bump Map

Sphere w/Diffuse Texture & Bump Map

## Displacement Mapping

We use the texture map to actually move the surface point. This is called _displacement mapping_. How is this fundamentally different than bump mapping?

![](img/94fd648dd12ff5c2cbed197b5038ba1a_593_0.png)

The geometry must be displaced before visibility is determined.

## Procedural Texture Mapping

- Instead of looking up an image, pass the texture coordinates to a function that computes the texture value on the fly
  - Renderman, the Pixar rendering language, does this
  - Available in a limited form with vertex shaders on current generation hardware
- Advantages:
  - Near-infinite resolution with small storage cost
  - Idea works for many other things
- Has the disadvantage of being slow in many cases

## THANK YOU

## Global Illumination

Shadows, Radiosity, Ray-tracing

## Shadows

## Shadows

## Shadows

- Shadows eliminate the perceptual artifacts of objects floating above the ground
- Shadows emphasize the changing direction of the light source
- Shadows may be *sharp edged* or *soft edge*, can contain both an *umbra* and a *penumbra* depending on the shape of the light source and its distance from the light source
- An illuminated scene without shadows could be confusing and affects realism

## Shadow Z-buffer

![](img/94fd648dd12ff5c2cbed197b5038ba1a_601_0.png)

View

Source

Shadow buffer

## Z-buffer enhanced for shadows

- Second step - the scene is rendered from the actual view with an enhanced z-buffer algorithm
  - if a point (x, y, z) is visible, than the view transformation of the light source is applied to the point which maps it to a point (x¹, y¹, z¹)
  - (x¹, y¹, z¹) is a view of the point (x, y, z) seen from the source
  - (x¹, y¹) is used to index into the shadow z-buffer and the corresponding depth value is compared with z¹
  - if z¹ is greater than the depth value then the (x, y, z) is in a shadow

