# 常见激活函数

+   - 常见激活函数及其导数

| 激活函数 | 函数 | 导数 |
|---|---|---|
| Logistic 函数 | $f(x) = \frac{1}{1+\exp(-x)}$ | $f'(x) = f(x)(1 - f(x))$ |
| Tanh 函数 | $f(x) = \frac{\exp(x)-\exp(-x)}{\exp(x)+\exp(-x)}$ | $f'(x) = 1 - f(x)^2$ |
| ReLU | $f(x) = \max(0, x)$ | $f'(x) = I(x > 0)$ |
| ELU | $f(x) = \max(0, x) + \min(0, \gamma(\exp(x) - 1))$ | $f'(x) = I(x > 0) + I(x \le 0) \cdot \gamma \exp(x)$ |
| SoftPlus 函数 | $f(x) = \log(1 + \exp(x))$ | $f'(x) = \frac{1}{1+\exp(-x)}$ |