# Markov链的参数估计

设模型的初始状态分布为 $\pi$，状态转移矩阵为 $A$，则模型可写为：
$$\begin{align}
p(x_{1:T}|\boldsymbol{\theta})& =\pi(x_1)A(x_1,x_2)\ldots A(x_{T-1},x_T) \\
&=\prod_{j=1}^{K}(\pi_{j})^{\mathbb{I}(x_{1}=j)}\prod_{t=2}^{T}\prod_{j=1}^{K}\prod_{k=1}^{K}(A_{jk})^{\mathbb{I}(x_{t}=k,x_{t-1}=j)}
\end{align}$$
其对数似然函数为：
$$\begin{align}
\ln p(\mathcal{D}|\boldsymbol{\theta})&=\sum_{i=1}^N\ln p(\boldsymbol{x}_i|\boldsymbol{\theta}) \\
&=\sum_{i=1}^N \sum_{j=1}^{K}\mathbb{I}(x_{1}=j)\ln(\pi_{j})\sum_{t=2}^{T}\sum_{j=1}^{K}\sum_{k=1}^{K}\mathbb{I}(x_{t}=k,x_{t-1}=j)\ln(A_{jk})\\
&=\sum_jN_j^1\ln\pi_j+\sum_j\sum_kN_{jk}\ln A_{jk}
\end{align}$$
其中 $N_{j}^{1}\triangleq\sum_{i=1}^{N}\mathbb{I}\left(x_{i1}=j\right)$ 代表数据点的初始状态出现了 $j$；$N_{jk}\triangleq\sum_{i=1}^{N}\sum_{t=1}^{T_{i}-1}\mathbb{I}\left(x_{i,t}=j,x_{i,t+1}=k\right)$ 代表数据出现了几次从 $j$ 到 $k$ 的状态转移。

由定义可知：$\sum_{j=1}^{K} \pi _j=1,\quad \sum_{k=1}^{K} A_{jk}=1$
再使用Lagrange乘法，求得其极大似然估计为：
$$\hat{\pi}_j=\frac{N_j^1}{\sum_{j'}N_{j'}^1}, \hat{A}_{jk}=\frac{N_{jk}}{\sum_{k}N_{jk}}$$
皆为其频率。


