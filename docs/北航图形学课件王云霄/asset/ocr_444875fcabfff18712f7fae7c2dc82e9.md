# ③绕Y轴旋转

x' = x cosθ + z sinθ
y' = y
z' = -x sinθ + z cosθ

P' = [x'  y'  z'  1] = [x  y  z  1] ⎡cosθ  0  -sinθ  0⎤
                                 ⎢ 0    1    0    0⎥
                                 ⎢sinθ  0   cosθ  0⎥
                                 ⎣ 0    0    0    1⎦

= P • R_y(θ)