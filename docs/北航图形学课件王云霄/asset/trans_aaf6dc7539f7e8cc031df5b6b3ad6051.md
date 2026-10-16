

## Constructing Surface Patches with Specified Boundary Curves:

A solution given by Coons is to find two blending functions $f_0(t)$ and $f_1(t)$ that are continuous and satisfy $f_0(0)=1$, $f_0(1)=0$, $f_1(0)=0$, $f_1(1)=1$, and $f_0(t)+f_1(t)=1$, $0\leqslant t\leqslant1$.

$f_0(t)=2t^3-3t^2+1$, $f_1(t)=-2t^3+3t^2$
$f_0(t)=1-t$, $f_1(t)=t$

## Problem 1: Find the surface through four boundary curves

Given four boundary curves u0, u1, 0w, 1w, with 0≤u≤1, 0≤w≤1

① Performing linear interpolation in the u direction gives the ruled surface:

P₁(u,w) = f₀(u)·0w + f₁(u)·1w

where f₀(u) + f₁(u) = 1, 0 ≤ u ≤ 1

② Performing linear interpolation in the w direction gives the ruled surface:

P₂(u,w) = f₀(w)·u0 + f₁(w)·u1
where f₀(w)+f₁(w)=1, 0≤w≤1

③ Superimposing ① and ② yields a new surface P₃(u, w) whose boundaries are exactly the unwanted straight-line boundaries:

$P_3(u,w)=f_0(w)[f_0(u)\cdot 00+f_1(u)\cdot 10]$

$\quad\quad\quad+f_1(w)[f_0(u)\cdot 01+f_1(u)\cdot 11]$

$=f_0(w)\cdot f_0(u)\cdot 00+f_0(w)\cdot f_1(u)\cdot 10$

$\quad\quad\quad+f_1(w)\cdot f_0(u)\cdot 01+f_1(w)\cdot f_1(u)\cdot 11$

where $f_0(u)+f_1(u)=1,\ 0\leq u\leq 1,$

$\quad\quad\quad f_0(w)+f_1(w)=1,\ 0\leq w\leq 1$

### P₁(u,w)

### P₂(u,w)

### P₃(u,w)

### P(u,w)

For example, let us verify that 0w is one of its boundary curves. This is done by substituting u=0 into the right-hand side of the formula, obtaining

RHS = 00·f₀(w) + 01·f₁(w) + 0w
− 00·f₀(w) − 01·f₁(w) = 0w

## Problem 2:

① The boundary curves are specified curves.

② It has specified cross-boundary tangent vectors.

Apply the four blending functions $q_{00}(u)$, $q_{01}(u)$, $q_{10}(u)$, $q_{11}(u)$ defined in the previous section.

- $q_{00}(u)=2u^3-3u^2+1$
- $q_{01}(u)=-2u^3+3u^2$
- $q_{10}(u)=u^3-2u^2+u$
- $q_{11}(u)=u^3-u^2$

These four functions are all cubic polynomials. Hence they are continuously differentiable and also satisfy the following conditions:

$$\begin{cases}
q_{00}(0)=1\\
q_{01}(0)=0\\
q_{10}(0)=0\\
q_{11}(0)=0
\end{cases}
\qquad
\begin{cases}
q_{00}(1)=0\\
q_{01}(1)=1\\
q_{10}(1)=0\\
q_{11}(1)=0
\end{cases}$$

$$\begin{cases}
q'_{00}(0)=0\\
q'_{01}(0)=0\\
q'_{10}(0)=1\\
q'_{11}(0)=0
\end{cases}
\qquad
\begin{cases}
q'_{00}(1)=0\\
q'_{01}(1)=0\\
q'_{10}(1)=0\\
q'_{11}(1)=1
\end{cases}$$

Suppose the four boundary curves $\omega_0$, $\omega_1$, $0_w$, $1_w$ and the cross-boundary tangent vectors along these four boundary curves $\omega_{w}$, $\omega_{u}$, $0_{w,u}$, $1_{w,u}$ are known.

Determine the position vectors $00$, $01$, $10$, $11$ of the four corner points, the tangent vectors $00_w$, $01_w$, $10_w$, $11_w$, $00_u$, $01_u$, $10_u$, $11_u$, and the twist vectors $00_{uw}$, $01_{uw}$, $10_{uw}$, $11_{uw}$.

Write the mathematical expression of the required surface as follows:

$$uw=[u_0,u_1,u_0',u_1']_{w',w}\begin{bmatrix}q_{00}(w)\\q_{01}(w)\\q_{10}(w)\\q_{11}(w)\end{bmatrix}+[0_w,1_w,0_w,1_w]_{u',u}\begin{bmatrix}q_{00}(u)\\q_{01}(u)\\q_{10}(u)\\q_{11}(u)\end{bmatrix}-[q_{00}(u),q_{01}(u),q_{10}(u),q_{11}(u)]\cdot M\cdot\begin{bmatrix}q_{00}(w)\\q_{01}(w)\\q_{10}(w)\\q_{11}(w)\end{bmatrix}$$

M = \begin{bmatrix} 00 & 01 & 00_{w} & 01_{w} \\ 10 & 11 & 10_{w} & 11_{w} \\ 00_{u} & 01_{u} & 00_{uw} & 01_{uw} \\ 10_{u} & 11_{u} & 10_{uw} & 11_{uw} \end{bmatrix}

## Verification of passing through boundary 0w

RHS = 00·q₀₀(w) + 01·q₀₁(w)
    + 00_w·q₁₀(w) + 01_w·q₁₁(w) + 0w
    − 00·q₀₀(w) − 01·q₀₁(w)
    − 00_w·q₁₀(w) − 01_w·q₁₁(w) + 0w
    = 0w

## Verify the cross-boundary tangent vector $\mathbf{0}_{wu}$:

RHS $=[00\ _u\quad 01\ _u\quad 00\ _{uw}\quad 01\ _{uw}]\begin{bmatrix}q_{00}(w)\\q_{01}(w)\\q_{10}(w)\\q_{11}(w)\end{bmatrix}$

$+[0w\quad 1w\quad 0w\ _u\quad 1w\ _u]\begin{bmatrix}0\\0\\1\\0\end{bmatrix}$

$-[0\quad 0\quad 1\quad 0]M\begin{bmatrix}q_{00}(w)\\q_{01}(w)\\q_{10}(w)\\q_{11}(w)\end{bmatrix}$

$=0w\ _u$

## Problem 3: After specifying the four corner points and the tangent and twist vectors at these points, derive the surface expression.

Compute the position vectors 00, 01, 10, 11 of the four corner points, the tangent vectors 00_w, 01_w, 10_w, 11_w, 00_u, 01_u, 10_u, 11_u, and the twist vectors 00_uw, 01_uw, 10_uw, 11_uw.

Given the corner position vectors 00, 10 and the tangent vectors with respect to u at these two points, 00_u and 10_u, the Hermite interpolation formula can be used to specify a boundary curve:

u0 = 00·q00(u) + 10·q01(u)
+ 00_u·q10(u) + 10_u·q11(u)
u1 = 01·q00(u) + 11·q01(u)
+ 01_u·q10(u) + 11_u·q11(u)

u0_w = 00_w · q_00(u) + 10_w · q_01(u)
    + 00_uw · q_10(u) + 10_uw · q_11(u)

u1_w = 01_w · q_00(u) + 11_w · q_01(u)
    + 01_uw · q_10(u) + 11_uw · q_11(u)

$$[u_0\quad u_1\quad u_{0_w}\quad u_{1_w}] = [q_{00}(u)\quad q_{01}(u)\quad q_{10}(u)\quad q_{11}(u)]\cdot M$$

$$M=\begin{bmatrix} 00 & 01 & 00_w & 01_w \\ 10 & 11 & 10_w & 11_w \\ 00_u & 01_u & 00_{uw} & 01_{uw} \\ 10_u & 11_u & 10_{uw} & 11_{uw} \end{bmatrix}$$

uw = [q₀₀(u)  q₀₁(u)  q₁₀(u)  q₁₁(u)] · M · [q₀₀(w) q₀₁(w) q₁₀(w) q₁₁(w)]ᵀ

= [u³  u²  u  1] ⎡ 2  -2  1  1 ⎤
                ⎢-3   3 -2 -1 ⎥
                ⎢ 0   0  1  0 ⎥
                ⎣ 1   0  0  0 ⎦

· ⎡ 00   01   00_w  01_w ⎤ ⎡ 2  -3  0  1 ⎤ ⎡ w³ ⎤
  ⎢ 10   11   10_w  11_w ⎥ ⎢-2   3  0  0 ⎥ ⎢ w² ⎥
  ⎢ 00_u 01_u 00_uw 01_uw⎥ ⎢ 1  -2  1  0 ⎥ ⎢ w  ⎥
  ⎣ 10_u 11_u 10_uw 11_uw⎦ ⎣ 1  -1  0  0 ⎦ ⎣ 1  ⎦

= [u³  u²  u  1] · H · M · Hᵀ · [w³  w²  w  1]ᵀ

