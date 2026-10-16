# ■ 二维数组A

![](bbox=[0.089, 0.137, 0.477, 0.572])

# 存储方式：

按行存放

按列存放

每维的下界：$low_1$、$low_2$

每维的上界：$high_1$、$high_2$

每维的长度：$n_1=high_1-low_1+1$

$n_2=high_2-low_2+1$

域宽：$w$　　基址：$base$

# 数组元素 A[i,j] 的位置：

$$base+((i-low_1)\times n_2+(j-low_2))\times w$$

$$=(i\times n_2+j)\times w+base-(low_1\times n_2+low_2)\times w$$