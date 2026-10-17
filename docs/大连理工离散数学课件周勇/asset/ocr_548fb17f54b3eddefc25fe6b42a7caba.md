# 直接证法

+   - **推理规则：**
+     - **CP规则：** 如果能从 R 和前提集合中推导出 S 来，则就能够从前提集合中推导出 $R \to S$。
+     - 换句话说，当结论是 $R \to S$ 的形式的时候，可以把结论的前件当作一个附加前提使用，并且它和前提一起若能推出结论的后件，则问题得证。
+     - 实际上恒等式 $E_{28}$ 就可以推出 CP 规则：

```
$$
(P \land Q) \to R
$$

$$
\Leftrightarrow \neg(P \land Q) \lor R
$$

$$
\Leftrightarrow (\neg P \lor \neg Q) \lor R
$$

$$
\Leftrightarrow \neg P \lor (\neg Q \lor R)
$$

$$
\Leftrightarrow P \to (Q \to R)
$$
```