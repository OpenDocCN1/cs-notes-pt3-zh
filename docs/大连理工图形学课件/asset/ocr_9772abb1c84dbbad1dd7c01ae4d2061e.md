# # OpenGL中的反走样

# ## 定义混合因子

void glBlendFunc(GLenum srcfactor, GLenum destfactor);

# ### 表5-1 源混和因子和目标混合因子

| 常量 | RGB混合因子 | Alpha混合因子 |
|---|---|---|
| GL_ZERO | (0, 0, 0) | 0 |
| GL_ONE | (1, 1, 1) | 1 |
| GL_SRC_COLOR | (Rs, Gs, Bs) | As |
| GL_ONE_MINUS_SRC_COLOR | (1, 1, 1) - (Rs, Gs, Bs) | 1 - As |
| GL_DST_COLOR | (Rd, Gd, Bd) | Ad |
| GL_ONE_MINUS_DST_COLOR | (1, 1, 1) - (Rd, Gd, Bd) | 1 - Ad |
| GL_SRC_ALPHA | (As, As, As) | As |
| GL_ONE_MINUS_SRC_ALPHA | (1, 1, 1) - (As, As, As) | 1 - As |
| GL_DST_ALPHA | (Ad, Ad, Ad) | Ad |
| GL_ONE_MINUS_DST_ALPHA | (1, 1, 1) - (Ap, Ap, Ap) | 1 - Ap |