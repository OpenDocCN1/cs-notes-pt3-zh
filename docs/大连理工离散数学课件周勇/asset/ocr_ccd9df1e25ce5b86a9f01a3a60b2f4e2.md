# # 全功能联结词集合

+   - 前面我们已经学习了6个逻辑联结词： ¬ ∧ ∨ ⟷⟹∇

+   - 是不是这些逻辑联结词都是必不可少的呢？在前面介绍的等价公式中我们已经发现，有些逻辑联结词是可以被其它逻辑联结词代替的：

+   - 例如： \( P \rightarrow Q \Leftrightarrow \neg P \vee Q \)

+   - \( P \leftrightarrow Q \Leftrightarrow (P \wedge Q) \vee (\neg P \wedge \neg Q) \)

+   - \( P \vee Q \Leftrightarrow \neg (\neg P \wedge \neg Q) \)

+   - \( P \wedge Q \Leftrightarrow \neg (\neg P \vee \neg Q) \)

+   - 从上面的讨论我们可以看出逻辑联结词集合{¬, ∧, ∨}是全功能的，但不是最小的。逻辑联结词全功能最小完备集是指用该集合中的逻辑联结词能表示所有的命题公式，并且删除一个至少有一个公式不能被表示。例如： {¬, ∧}和{¬, ∨} 均是最小功能完备集