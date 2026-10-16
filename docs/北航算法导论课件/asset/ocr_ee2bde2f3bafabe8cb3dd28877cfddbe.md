# 30.2.4 Interpolation at the complex roots of unity

a₀, a₁, ..., aₙ₋₁
b₀, b₁, ..., bₙ₋₁

Ordinary multiplication

c₀, c₁, ..., c₂ₙ₋₂

1

Extend point-value,
Time Θ(n).

a₀, a₁, ..., aₙ₋₁, 0, ..., 0
b₀, b₁, ..., bₙ₋₁, 0, ..., 0

2

Evaluation, DFT,
Time Θ(nlgn)

A(ω₂ₙ⁰), B(ω₂ₙ⁰)
A(ω₂ₙⁱ), B(ω₂ₙⁱ)
⋮
A(ω₂ₙ²ⁿ⁻¹), B(ω₂ₙ²ⁿ⁻¹)

Time Θ(n²)

A(x) = Σⱼ₌₀ⁿ⁻¹ aⱼ xʲ
C = A · B ?

3

Pointwise multiplication
Time Θ(n)

C(ω₂ₙ⁰)
C(ω₂ₙⁱ)
⋮
C(ω₂ₙ²ⁿ⁻¹)

4

Interpolation,
Inverse DFT,
Time Θ(nlgn)

Theorem 30.8 (Convolution theorem, 卷积定理)
For any two vectors a and b of length n, where n is a power of 2,
a ⊗ b = DFT₂ₙ⁻¹(DFT₂ₙ(a) · DFT₂ₙ(b))
where the vectors a and b are padded with 0's to length 2n
and · denotes the component-wise product of two 2n-element vectors.