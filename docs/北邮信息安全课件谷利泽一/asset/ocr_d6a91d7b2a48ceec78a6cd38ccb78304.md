# DES解密过程

$i$：表示迭代次数，

$\oplus$：表示逐位模2求和

$f$：为加密函数

$R_{16}L_{16} \leftarrow IP(\langle 64bit密文\rangle)$

$R_{i-1} \leftarrow L_i \qquad i=16,15,\cdots,1$

$L_i \leftarrow R_{i-1} \oplus f(R_{i-1},k_i) \qquad i=16,15,\cdots,1$

$\langle 64bit明文\rangle \leftarrow IP^{-1}(R_0L_0)$