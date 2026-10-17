
## Define the optimal function

Define \(c(i,j)\) to be the cost of \(M_i \times M_{i+1} \times \cdots \times M_j\).

- \(c(0,0)=0\)
- \(c(i,i)=0\)
- \(c(i,i+1)=r_i \times r_{i+1} \times r_{i+2}\)
- \(c(1,q)\) is our goal
- The recursive equation is

$$
c(i,j)=\min_{i\le k<j}\{c(i,k)+c(k+1,j)+r_i \times r_{k+1} \times r_{j+1}\}\tag{3}
$$

- Let \(k(i,j)\) be the number minimizing the above equation.
  - \(k(i,i)=0\)
  - \(k(i,i+1)=i\)

## An example

Suppose that \(q=5\) and \(r=(10,5,1,10,2,10)\), find the optimal orders of multiplications.

| Subproblem | Calculation | Result |
|---|---|---|
| \(c(1,5)\) | \(\min\{c(1,1)+c(2,5)+500,\ c(1,2)+c(3,5)+100,\ c(1,3)+c(4,5)+1000,\ c(1,4)+c(5,5)+200\}\) | |
| \(c(2,5)\) | \(\min\{c(2,2)+c(3,5)+50,\ c(2,3)+c(4,5)+500,\ c(2,4)+c(5,5)+100\}\) | \(c(2,5)=90,\ k(2,5)=2\) |
| \(c(3,5)\) | \(\min\{c(3,3)+c(4,5)+100,\ c(3,4)+c(5,5)+20\}=\min\{300,40\}=40\) | \(c(3,5)=40,\ k(3,5)=4\) |
| \(c(2,4)\) | \(\min\{c(2,2)+c(3,4)+10,\ c(2,3)+c(4,4)+100\}=\min\{30,150\}=30\) | \(c(2,4)=30,\ k(2,4)=2\) |
