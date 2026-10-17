

## Wireframe Vs. Solid Models - Illustration

![](img/258e4144ed4b66c8fd4b0f298118df23_26_0.png)

## Flat Shading

![](img/258e4144ed4b66c8fd4b0f298118df23_27_0.png)

## Gouraud Shading

![](img/258e4144ed4b66c8fd4b0f298118df23_28_0.png)

## Phong Shading

![](img/258e4144ed4b66c8fd4b0f298118df23_29_0.png)

## Modeling with Curved Surfaces

![](img/258e4144ed4b66c8fd4b0f298118df23_30_0.png)

## Rendering with Texture Mapping

![](img/258e4144ed4b66c8fd4b0f298118df23_32_0.png)

## Advanced illumination - Illustration

![](img/258e4144ed4b66c8fd4b0f298118df23_33_0.png)

## Global Illumination - radiosity

![](img/258e4144ed4b66c8fd4b0f298118df23_35_0.png)

## Global Illumination - radiosity

![](img/258e4144ed4b66c8fd4b0f298118df23_36_0.png)

## Global Illumination - photon mapping

![](img/258e4144ed4b66c8fd4b0f298118df23_37_0.png)

## Global Illumination - photon mapping

![](img/258e4144ed4b66c8fd4b0f298118df23_38_0.png)

## Global Illumination - photon mapping

![](img/258e4144ed4b66c8fd4b0f298118df23_39_0.png)

## Global Illumination - photon mapping

![](img/258e4144ed4b66c8fd4b0f298118df23_40_0.png)

## Global Illumination - photon mapping

![](img/258e4144ed4b66c8fd4b0f298118df23_41_0.png)

## Researches in our CS, TJU

- Realism Image Synthesis  
  - Monte Carlo Global Illumination (demo)
- Simulation of natural phenomena (demo)
- Virtual Reality
- Image Based Rendering
- Visualization in Medicinal Data
- Simulation of Chinese Ink-wash Drawing
- ......

## Researches in our group

### MCGI renderer

![](img/258e4144ed4b66c8fd4b0f298118df23_43_0.png)

### MCGI renderer

![](img/258e4144ed4b66c8fd4b0f298118df23_44_0.png)

![](img/258e4144ed4b66c8fd4b0f298118df23_44_1.png)

### Pmap

![](img/258e4144ed4b66c8fd4b0f298118df23_45_0.png)

![](img/258e4144ed4b66c8fd4b0f298118df23_45_1.png)

### Researches in our group

![](img/258e4144ed4b66c8fd4b0f298118df23_46_0.png)

### Chinese Ink-wash Drawing

![](img/258e4144ed4b66c8fd4b0f298118df23_47_0.png)

## Image based Modeling and Rendering

![](img/258e4144ed4b66c8fd4b0f298118df23_48_0.png)

![](img/258e4144ed4b66c8fd4b0f298118df23_48_1.png)

![](img/258e4144ed4b66c8fd4b0f298118df23_48_2.png)

![](img/258e4144ed4b66c8fd4b0f298118df23_48_3.png)

1
2
3

![](img/258e4144ed4b66c8fd4b0f298118df23_49_0.png)

# Splatting algorithm for visualization

## Reference Books

- ◆ Computer Graphics - Principles and Practice  
  James D. Foley, Steven K. Feiner

- ◆ Computer Graphics with OpenGL (3rd edition)  
  Donald Hearn and M. Pauline Baker

- ◆ “教材”：计算机图形学（新版）清华大学出版社  
  孙家广 编著

- ◆ 计算机图形学基础 清华大学出版社  
  唐泽圣 等编著

## Prerequisite

- C/C++ Programming
- Data Structure
- Tool for experiments: Visual C++

## 2. Graphics System and Architecture

- Graphics System
- The Synthetic-Camera Model
- Graphics Architecture

## Graphics System

![](img/258e4144ed4b66c8fd4b0f298118df23_53_0.png)

## Pixels and the Frame Buffer

- A picture is produced as an array - the **raster** - of picture elements, **pixels**, within the graphics system.
- **Resolution** - number of pixels in the frame buffer
  - determines the detail that you can see in the image.
- The converting of geometric entities to pixel assignments in the frame buffer is known as **scan conversion**, or **rasterization**.

## Frame Buffer

- It contains color information for each pixel

![](img/258e4144ed4b66c8fd4b0f298118df23_55_0.png)

| 1280 X 1024 X | 1 (B/W) | 4 (16 Colors) = 0.655 M Byte |
|---------------|---------|------------------------------|
|               | 8 (256 Colors) = 1.31 M Byte |                              |
|               | 24 (16M Colors) = 3.932 M Byte |                            |

