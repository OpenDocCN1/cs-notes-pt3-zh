下证 $R\cup R^2\cup\cdots$ 是传递的。事实上，对任意 $\langle x,y\rangle,\langle y,z\rangle$，

$(\langle x,y\rangle\in R\cup R^2\cup\cdots)\land(\langle y,z\rangle\in R\cup R^2\cup\cdots)$

$\Rightarrow \exists t(\langle x,y\rangle\in R^t)\land\exists s(\langle y,z\rangle\in R^s)$

$\Rightarrow \exists t\exists s(\langle x,z\rangle\in R^t\circ R^s)$

$\Rightarrow \exists t\exists s(\langle x,z\rangle\in R^{t+s})$

$\Rightarrow \langle x,z\rangle\in R\cup R^2\cup\cdots$

从而　$R\cup R^2\cup\cdots$ 是传递的。

因 $t(R)$ 是传递闭包，故　$t(R)\subseteq R\cup R^2\cup\cdots$。

由以上两方面知，$t(R)=R\cup R^2\cup\cdots$。