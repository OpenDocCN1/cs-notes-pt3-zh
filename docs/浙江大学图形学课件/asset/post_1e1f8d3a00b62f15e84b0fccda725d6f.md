

## Diffuse Reflection

- **Diffuse reflection** also called **Lambertian reflection** is a characteristic of dull, matte surfaces like chalk
- Amount of light reflected from a point on the surface is equal in all directions
- The brightness depends on the angle between the direction to the light source and the surface normal
- The brightness is independent of the viewing direction

![](img/94fd648dd12ff5c2cbed197b5038ba1a_502_0.png)

![](img/94fd648dd12ff5c2cbed197b5038ba1a_502_1.png)

- If the beam of light has a cross-sectional area \(da\) and is inclined to the surface at an angle \(\theta\) then the beam intercepts the area \(da/\cos(\theta)\)

![](img/94fd648dd12ff5c2cbed197b5038ba1a_503_0.png)

- The amount of light energy that falls on a surface is proportional to \(\cos(\theta)\)

- The diffuse illumination equation is \(I_d = I_p k_d \cos(\theta)\) where, \(I_p\) is the point light source intensity, \(k_d\) is the materials diffuse reflection coefficient ranging from 0 to 1. and \(\theta\) must be between 0⁰ and 90⁰ for the point to be lit

- With \(\overline{N}\) and \(\overline{L}\) normalized the diffuse illumination equation could also be written as

\(I_d = I_p k_d (\overline{N} \bullet \overline{L})\)

- With the diffuse reflection the part of the surface not illuminated by the light is dark

![](img/94fd648dd12ff5c2cbed197b5038ba1a_504_0.png)

## Ambient Light

- In reality, parts of the object not directly illuminated by the light source are not completely dark
- These parts are lit by global illumination i.e. light reflected by the surrounding environment; light that is reflected so many times that doesn’t seem to come from any where
- This light is approximated by adding a constant light called ambient light
- The ambient light is \( I_a k_a \) , where \( I_a \) is the intensity of ambient light and \( k_a \) is the materials _ambient reflection coefficient_ ranging from 0 to 1

![](img/94fd648dd12ff5c2cbed197b5038ba1a_505_0.png)

## Illumination equation

- By adding the ambient term to the diffuse reflection the illumination equation is

\( I = I_a k_a + I_p k_d (\overline{N} \bullet \overline{L}) \)

![](img/94fd648dd12ff5c2cbed197b5038ba1a_506_0.png)

![](img/94fd648dd12ff5c2cbed197b5038ba1a_506_1.png)

![](img/94fd648dd12ff5c2cbed197b5038ba1a_506_2.png)

\( k_a = 0.2, \quad k_d = 0.4 \)

\( k_a = 0.2, \quad k_d = 0.6 \)

\( k_a = 0.2, \quad k_d = 0.8 \)

## Specular Reflection

- **Specular reflection** is exhibited by shiny surfaces like plastics

- In case of a perfect mirror light is reflected only in the reflection direction R . For the viewer to see the reflected light, his direction V should be same as the reflected direction i.e. angle α = 0

- Natural shiny surfaces reflect light unequally in different directions

- This is captured by the **Phong illumination model**

![](img/94fd648dd12ff5c2cbed197b5038ba1a_507_0.png)

## Phong Illumination Model

- These two types of reflection together make up the phong illumination model
  - Diffuse reflectance
  - Specular reflectance
- So, lighting depends on the properties of the surface as well as the light itself
  - Light Properties
  - Material Properties

## Phong Illumination Model

- Developed by Phong Bui-Tuong (1975) is a popular model for non-perfect reflectors
- Specular reflection of shiny objects is considered. It assumes that maximum specular reflection occurs at \(\alpha = 0\)
- The light calculation depends on the viewing direction
- Reflected intensity is modeled in terms of
  - Ambient component
  - Diffuse reflection component
  - Specular reflection component

![](img/94fd648dd12ff5c2cbed197b5038ba1a_509_0.png)

## Phong Illumination model

- The illumination equation in its simplest form is given as

\( I = I_a k_a + I_p k_d (\overline{N} \cdot \overline{L}) + I_p k_s (\overline{R} \cdot \overline{V})^n \)

where, \( k_s \) is the materials specular reflection coefficient ranging between 0 and 1, \( n \) is the specular reflection exponent is the material property the object, \( \overline{R} \) is the reflected ray vector and \( \overline{V} \) is the view vector

\( k_a = 0.2, \quad k_d = 0.2, \quad k_s = 0.6, n = 4 \)

