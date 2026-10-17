
## 子代数系统

定义9.8 设 \( V = \langle S, f_1, f_2, \dots, f_k \rangle \) 是代数系统，\( B \) 是 \( S \) 的非空子集，如果 \( B \) 对 \( f_1, f_2, \dots, f_k \) 都是封闭的，且 \( B \) 和 \( S \) 含有相同的代数常数，则称 \( \langle B, f_1, f_2, \dots, f_k \rangle \) 是 \( V \) 的子代数系统，简称子代数。有时将子代数系统简记为 \( B \)。

## 实例

\( N \) 是 \( \langle Z, + \rangle \) 的子代数，\( N \) 也是 \( \langle Z, +, 0 \rangle \) 的子代数。

\( N - \{0\} \) 是 \( \langle Z, + \rangle \) 的子代数，但不是 \( \langle Z, +, 0 \rangle \) 的子代数。

## 说明：

- 子代数和原代数是同种的代数系统
- 对于任何代数系统 \( V = \langle S, f_1, f_2, \dots, f_k \rangle \)，其子代数一定存在。

## 关于子代数的术语

1. **最大的子代数**：就是 \( V \) 本身
2. **最小的子代数**：如果令 \( V \) 中所有代数常数构成的集合是 \( B \)，且 \( B \) 对 \( V \) 中所有的运算都是封闭的，则 \( B \) 就构成了 \( V \) 的最小的子代数
3. 最大和最小的子代数称为 \( V \) 的**平凡的子代数**
4. 若 \( B \) 是 \( S \) 的真子集，则 \( B \) 构成的子代数称为 \( V \) 的**真子代数**。

例 设 \( V = \langle Z, +, 0 \rangle \)，令 \( nZ = \{ nz \mid z \in Z, n \text{ 为自然数} \} \)，则 \( nZ \) 是 \( V \) 的子代数。

当 \( n = 1 \) 和 \( 0 \) 时，\( nZ \) 是 \( V \) 的平凡的子代数，其他的都是 \( V \) 的非平凡的真子代数。

## 积代数

定义9.9 设 \( V_1 = \langle A, \circ \rangle \) 和 \( V_2 = \langle B, * \rangle \) 是同类型的代数系统，\( \circ \) 和 \( * \) 为二元运算，在集合 \( A \times B \) 上如下定义二元运算 \( \blacksquare \)，
\( \forall \langle a_1, b_1 \rangle, \langle a_2, b_2 \rangle \in A \times B \)，有
\[ \langle a_1, b_1 \rangle \blacksquare \langle a_2, b_2 \rangle = \langle a_1 \circ a_2, b_1 * b_2 \rangle \]
称 \( V = \langle A \times B, \blacksquare \rangle \) 为 \( V_1 \) 与 \( V_2 \) 的积代数，记作 \( V_1 \times V_2 \)。这时也称 \( V_1 \) 和 \( V_2 \) 为 \( V \) 的因子代数。

实例 \( Z_2 = \{0, 1\} \)，\( V = \langle Z_2, \oplus \rangle \)，\( V_1 \times V_2 = \langle Z_2 \times Z_2, \blacksquare \rangle \)
\( Z_2 \times Z_2 = \{ \langle 0, 0 \rangle, \langle 1, 0 \rangle, \langle 0, 1 \rangle, \langle 1, 1 \rangle \} \)
\( \langle 0, 1 \rangle \blacksquare \langle 1, 0 \rangle = \langle 0, 0 \rangle \)

注意：积代数的定义可以推广到具有多个运算的同类型的代数系统。

## 定理9.3

设 \( V_1 = \langle A, \circ \rangle \) 和 \( V_2 = \langle B, * \rangle \) 是同类型的代数系统，\( V_1 \times V_2 = \langle A \times B, \blacksquare \rangle \) 是它们的积代数。

1. 如果 \( \circ \) 和 \( * \) 运算是可交换（可结合、幂等）的，那么 \( \blacksquare \) 运算也是可交换（可结合、幂等的）
2. 如果 \( e_1 \) 和 \( e_2 \)（\( \theta_1 \) 和 \( \theta_2 \)）分别为 \( \circ \) 和 \( * \) 运算的单位元（零元），那么 \( \langle e_1, e_2 \rangle \)（\( \langle \theta_1, \theta_2 \rangle \)）也是 \( \blacksquare \) 运算的单位元（零元）
3. 如果 \( x \) 和 \( y \) 分别为 \( \circ \) 和 \( * \) 运算的可逆元素，那么 \( \langle x, y \rangle \) 也是 \( \blacksquare \) 运算的可逆元素，其逆元就是 \( \langle x^{-1}, y^{-1} \rangle \)

## 证明(1)中的交换律，(2)中的零元

1. 任取 \( \langle a_1, b_1 \rangle, \langle a_2, b_2 \rangle \in V_1 \times V_2 \)，
   \[ \langle a_1, b_1 \rangle \cdot \langle a_2, b_2 \rangle = \langle a_1 \circ a_2, b_1 * b_2 \rangle = \langle a_2 \circ a_1, b_2 * b_1 \rangle = \langle a_2, b_2 \rangle \cdot \langle a_1, b_1 \rangle \]

2. 任取 \( \langle a, b \rangle \in V_1 \times V_2 \)，
   \[ \langle a, b \rangle \cdot \langle \theta_1, \theta_2 \rangle = \langle a \circ \theta_1, b * \theta_2 \rangle = \langle \theta_1, \theta_2 \rangle \]
   \[ \langle \theta_1, \theta_2 \rangle \cdot \langle a, b \rangle = \langle \theta_1 \circ a, \theta_2 * b \rangle = \langle \theta_1, \theta_2 \rangle \]

3. 任取 \( \langle a, b \rangle \in V_1 \times V_2 \)，使得
   \[ \langle x, y \rangle \cdot \langle a, b \rangle = \langle e_1, e_2 \rangle \Rightarrow x \circ a = e_1 \land y * b = e_2 \Rightarrow a = x^{-1} \land b = y^{-1} \]
   \[ \Rightarrow \langle a, b \rangle = \langle x^{-1}, y^{-1} \rangle \]

## 9.3 代数系统的同态与同构

定义9.10 设 \( V_1 = \langle A, \circ \rangle \) 和 \( V_2 = \langle B, * \rangle \) 是同类型的代数系统，\( f: A \rightarrow B \)，且 \( \forall x, y \in A \) 有 \( f(x \circ y) = f(x) * f(y) \)，则称 \( f \) 是 \( V_1 \) 到 \( V_2 \) 的同态（Homomorphism）映射，简称同态。

同态分类：

1. \( f \) 如果是单射，则称为单同态（Monomorphism）
2. 如果是满射，则称为满同态（Epimorphism），这时称 \( V_2 \) 是 \( V_1 \) 的同态像，记作 \( V_1 \sim V_2 \)
3. 如果是双射，则称为同构，也称代数系统 \( V_1 \) 同构（Isomorphism）于 \( V_2 \)，记作 \( V_1 \cong V_2 \)
4. 如果 \( V_1 = V_2 \)，则称作自同态（Endomorphism）

(1) 设 \( V_1 = \langle Z, + \rangle \)，\( V_2 = \langle Z_n, \oplus \rangle \)。其中 \( Z \) 为整数集，\( + \) 为普通加法；\( Z_n = \{0, 1, \dots, n-1\} \)，\( \oplus \) 为模 \( n \) 加。令 \( f: Z \rightarrow Z_n \)，\( f(x) = (x) \mod n \)，那么 \( f \) 是 \( V_1 \) 到 \( V_2 \) 的满同态。

(2) 设 \( V_1 = \langle R, + \rangle \)，\( V_2 = \langle R^*, \cdot \rangle \)，其中 \( R \) 和 \( R^* \) 分别为实数集与非零实数集，\( + \) 和 \( \cdot \) 分别表示普通加法与乘法。令 \( f: R \rightarrow R^* \)，\( f(x) = e^x \)，则 \( f \) 是 \( V_1 \) 到 \( V_2 \) 的单同态。

(3) 设 \( V = \langle Z, + \rangle \)，其中 \( Z \) 为整数集，\( + \) 为普通加法。\( \forall a \in Z \)，令 \( f_a: Z \rightarrow Z \)，\( f_a(x) = ax \)，那么 \( f_a \) 是 \( V \) 的自同态。当 \( a = 0 \) 时称 \( f_0 \) 为零同态；当 \( a = \pm 1 \) 时，称 \( f_a \) 为自同构；除此之外其他的 \( f_a \) 都是单自同态。

## 定理6.3.2

给定 \( \langle X, \odot, * \rangle \sim \langle Y, \oplus, \otimes \rangle \) 且 \( f \) 为其满同态映射，则

1. 如果 \( \odot \) 和 \( * \) 满足结合律，则 \( \oplus \) 和 \( \otimes \) 也满足结合律。
2. 如果 \( \odot \) 和 \( * \) 满足交换律，则 \( \oplus \) 和 \( \otimes \) 也满足交换律。
3. 如果 \( \odot \) 对于 \( * \) 或 \( * \) 对于 \( \odot \) 满足分配律，则 \( \oplus \) 对于 \( \otimes \) 或 \( \otimes \) 对于 \( \oplus \) 也相应满足分配律。
4. 如果 \( \odot \) 对于 \( * \) 或 \( * \) 对于 \( \odot \) 满足吸收律，则 \( \oplus \) 对于 \( \otimes \) 或 \( \otimes \) 对于 \( \oplus \) 也满足吸收律。
5. 如果 \( \odot \) 和 \( * \) 满足等幂律，则 \( \oplus \) 和 \( \otimes \) 也满足等幂律。
6. 如果 \( e_1 \) 和 \( e_2 \) 分别是关于 \( \odot \) 和 \( * \) 的么元，则 \( f(e_1) \) 和 \( f(e_2) \) 分别为关于 \( \oplus \) 和 \( \otimes \) 的么元。
7. 如果 \( \theta_1 \) 和 \( \theta_2 \) 分别是关于 \( \odot \) 和 \( * \) 的零元，则 \( f(\theta_1) \) 和 \( f(\theta_2) \) 分别为关于 \( \oplus \) 和 \( \otimes \) 的零元。
8. 如果对每个 \( x \in X \) 均存在关于 \( \odot \) 的逆元 \( x^{-1} \)，则对每个 \( f(x) \in Y \) 均存在关于 \( \oplus \) 的逆元 \( f(x^{-1}) \)；如果对每个 \( z \in X \) 均存在关于 \( * \) 的逆元 \( z^{-1} \)，则对每个 \( f(z) \in Y \) 均存在关于 \( \otimes \) 的逆元 \( f(z^{-1}) \)。

## 主要内容

- 代数系统的构成：非空集合、封闭的二元和一元运算、代数常数
- 二元运算性质和特异元素：交换律、结合律、幂等律、分配律、吸收律、单位元、零元、可逆元和逆元
- 同类型的与同种的代数系统
- 子代数的定义与实例
- 积代数的定义与性质
- 代数系统的同态与同构

## 基本要求

- 判断给定集合和运算能否构成代数系统
- 判断给定二元运算的性质
- 求二元运算的特异元素
- 了解同类型和同种代数系统的概念
- 了解子代数的基本概念
- 计算积代数
- 判断函数是否为同态映射和同构映射

## 练习1

1. 设。运算为 \( Q \) 上的二元运算，
   \( \forall x, y \in Q, \ x \circ y = x + y + 2xy \)

   (1) 判断。运算是否满足交换律和结合律，并说明理由。
   (2) 求出。运算的单位元、零元和所有可逆元素的逆元。

   (1)。运算可交换，可结合。

   任取 \( x, y \in Q \)，
   \( x \circ y = x + y + 2xy = y + x + 2yx = y \circ x \)

   任取 \( x, y, z \in Q \)，
   \( (x \circ y) \circ z = (x + y + 2xy) \circ z + 2(x + y + 2xy)z \)
   \( = x + y + z + 2xy + 2xz + 2yz + 4xyz \)
   \( x \circ (y \circ z) = x + (y + z + 2yz) + 2x(y + z + 2yz) \)
   \( = x + y + z + 2xy + 2xz + 2yz + 4xyz \)
