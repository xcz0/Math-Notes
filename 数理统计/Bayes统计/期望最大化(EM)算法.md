# 期望最大化(EM)算法

期望最大化(expectation maximization, EM)算法是[[边界优化]]算法的一种。
假设[[混合模型]]的对数似然函数为
$$\ell(\boldsymbol{\theta})=\sum_{n=1}^N\log p(\boldsymbol{x}_n|\boldsymbol{\theta})=\sum_{n=1}^N\log\left[\sum_{\boldsymbol{z}_n}p(\boldsymbol{x}_n,\boldsymbol{z}_n|\boldsymbol{\theta})\right]$$


假定隐变量 $z_n$ 的分布为 $p_n(z_n)$，则对数似然函数可改写为：
$$\ell(\boldsymbol{\theta})=\sum_{n=1}^N\log\left[\sum_{\boldsymbol{z}_n}q_n(\boldsymbol{z}_n)\frac{p(\boldsymbol{x}_n,\boldsymbol{z}_n|\boldsymbol{\theta})}{q_n(\boldsymbol{z}_n)}\right]$$
由于对数函数是凸函数，根据 [[Jensen不等式]] 得
$$\begin{align}
\ell(\boldsymbol{\theta})& \geq\sum_{n}\sum_{\boldsymbol{z}_{n}}q_{n}(\boldsymbol{z}_{n})\log\frac{p(\boldsymbol{x}_{n},\boldsymbol{z}_{n}|\boldsymbol{\theta})}{q_{n}(\boldsymbol{z}_{n})} \\
&=\sum\mathbb{E}_{q_n}\left[\log p(\boldsymbol{x}_n,\boldsymbol{z}_n|\boldsymbol{\theta})\right]+\mathbb{H}(q_n)
\end{align}$$
其中 $\mathbb{H}(q_n)$ 为分布 $q_n$ 的[[熵]]。
