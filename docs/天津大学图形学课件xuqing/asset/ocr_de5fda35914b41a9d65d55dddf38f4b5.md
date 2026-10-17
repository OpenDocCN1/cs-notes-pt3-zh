# # Local Illumination

# ## Diffuse Reflection Model

![](bbox=[0.064, 0.315, 0.377, 0.578])

```
$$I_{dr}=I_{Lr}\cdot K_{dr}(\vec{L}\cdot\vec{N})$$
$$I_{dg}=I_{Lg}\cdot K_{dg}(\vec{L}\cdot\vec{N})$$
$$I_{db}=I_{Lb}\cdot K_{db}(\vec{L}\cdot\vec{N})$$
```

```
$$I_d=K_d\sum_{i=1}^{m}\left[I_{L_i}\cdot(\vec{L_i}\cdot\vec{N})\right]$$
```

```
$$I_d=I_L\cdot K_d\cos\theta$$
```

+   - Know as *Lambertian reflection*
+   - It is view-independent
+   - Reflection coefficient depends on the characteristics of material and input light wavelength
+   - for multiple light sources