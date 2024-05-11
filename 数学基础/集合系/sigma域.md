# $\sigma$ 域

若非空集合系对*可列并、可列交、补*运算封闭，则称其为 $\sigma$ 域($\sigma$ field)，或 $\sigma$ 代数($\sigma$ algebra)。

与域同理，此定义也等价于以下条件：

若集合系 $\mathscr{F}$ 满足：

- 包含全集： $X \in \mathscr{F}$
- 包含任意集合的补集： $A \in \mathscr{F} \implies A^{\complement} \in \mathscr{F}$
- $A_n \in \mathscr{F} \implies \bigcup_{n=1}^{\infty} A_n \in \mathscr{F}$

例：
最小的 $\sigma$ 域：$\{ X,\emptyset \}$