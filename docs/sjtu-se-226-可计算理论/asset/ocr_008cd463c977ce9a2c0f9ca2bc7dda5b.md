# Proof in Detail ([ch](ch))

The following function

$$\operatorname{ch}(c,z) = \text{ the resulting configuration when the configuration } c \text{ is operated on by the instruction with code number } z.$$

is primitive recursive if

$$\operatorname{ch}(c,z)=\begin{cases}\operatorname{zero}(c,u(z)), & \text{if } rm(4,z)=0,\\\operatorname{succ}(c,u(z)), & \text{if } rm(4,z)=1,\\\operatorname{tran}(c,u_1(z),u_2(z)), & \text{if } rm(4,z)=2,\\c, & \text{if } rm(4,z)=3.\end{cases}$$