# Ray Tracing

# Lighting calculation

If I(P₀, u) is the intensity seen from point P along direction u

$$I(P_0,\mathbf{u}) = I_{direct} + I_{reflected} + I_{transmitted}$$

where

$$I_{direct} = Shade(\mathbf{N},\mathbf{L},\mathbf{u},\mathbf{R})\ \text{(e.g. Phong shading model)}$$

$$I_{reflected} = k_r I(P,\mathbf{R})$$

$$I_{transmitted} = k_t I(P,\mathbf{T})$$

Typically, we set $k_r = k_s$ and $k_t$

![](bbox=[0.523, 0.661, 0.876, 0.955])