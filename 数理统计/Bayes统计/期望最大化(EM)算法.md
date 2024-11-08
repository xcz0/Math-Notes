# 期望最大化(EM)算法

期望最大化(expectation maximization, EM)算法是[[边界优化]]算法的一种。
假设[[混合模型]]的对数似然函数为
$$\ell(\boldsymbol{\theta})=\sum_{n=1}^N\log p(\boldsymbol{x}_n|\boldsymbol{\theta})=\sum_{n=1}^N\log\left[\sum_{\boldsymbol{z}_n}p(\boldsymbol{x}_n,\boldsymbol{z}_n|\boldsymbol{\theta})\right]$$
求解目标是其最大值点 $\theta^*=\underset{\theta}{\arg\max}\ell(\boldsymbol{\theta})$
## 下界
假定隐变量 $z_n$ 的分布为 $q_n(z_n)$，则对数似然函数可改写为：
$$\ell(\boldsymbol{\theta})=\sum_{n=1}^N\log\left[\sum_{\boldsymbol{z}_n}q_n(\boldsymbol{z}_n)\frac{p(\boldsymbol{x}_n,\boldsymbol{z}_n|\boldsymbol{\theta})}{q_n(\boldsymbol{z}_n)}\right]$$
由于对数函数是凸函数，根据 [[Jensen不等式]] 得
$$\begin{align}
\ell(\boldsymbol{\theta})& \geq\sum_{n}\sum_{\boldsymbol{z}_{n}}q_{n}(\boldsymbol{z}_{n})\log\frac{p(\boldsymbol{x}_{n},\boldsymbol{z}_{n}|\boldsymbol{\theta})}{q_{n}(\boldsymbol{z}_{n})} \\
&=\sum_n\mathbb{E}_{q_n}\left[\log p(\boldsymbol{x}_n,\boldsymbol{z}_n|\boldsymbol{\theta})\right]+\mathbb{H}(q_n)
\end{align}$$
其中 $\mathbb{H}(q_n)$ 为分布 $q_n$ 的[[熵]]。

记 $\mathbb{E}_{q_n}\left[\log p(\boldsymbol{x}_n,\boldsymbol{z}_n|\boldsymbol{\theta})\right]+\mathbb{H}(q_n)=\mathrm{L}(\boldsymbol{\theta},q_{n})$，且记 $\mathcal{L}(\boldsymbol{\theta},q_{1:N})\triangleq\sum_n\mathcal{L}(\boldsymbol{\theta},q_n)$ ，称为**信念下界**(evidence lower bound, ELBO)。其优化方法为[[变分推断]]。

$$\begin{align}
\mathrm{L}(\boldsymbol{\theta},q_{n})& =\sum_{\boldsymbol{z}_n}q_n(\boldsymbol{z}_n)\log\frac{p(\boldsymbol{x}_n,\boldsymbol{z}_n|\boldsymbol{\theta})}{q_n(\boldsymbol{z}_n)} \\
&=\sum_{\boldsymbol{z}_n}q_n(\boldsymbol{z}_n)\log\frac{p(\boldsymbol{z}_n|\boldsymbol{x}_n,\boldsymbol{\theta})p(\boldsymbol{x}_n|\boldsymbol{\theta})}{q_n(\boldsymbol{z}_n)} \\
&=\sum_{\boldsymbol{z}_n}q_n(\boldsymbol{z}_n)\log\frac{p(\boldsymbol{z}_n|\boldsymbol{x}_n,\boldsymbol{\theta})}{q_n(\boldsymbol{z}_n)}+\sum_{\boldsymbol{z}_n}q_n(\boldsymbol{z}_n)\log p(\boldsymbol{x}_n|\boldsymbol{\theta}) \\
&=-D_{\mathbb{KL}}\left(q_n(\boldsymbol{z}_n)\parallel p(\boldsymbol{z}_n|\boldsymbol{x}_n,\boldsymbol{\theta})\right)+\log p(\boldsymbol{x}_n|\boldsymbol{\theta})
\end{align}$$
其中 $D_{\mathbb{KL}}\left(q_n(\boldsymbol{z}_n)\parallel p(\boldsymbol{z}_n|\boldsymbol{x}_n,\boldsymbol{\theta})\right)$ 是两分布的 [[KL散度]]。由于其总是非负的，并且仅在两分布相同时才为 $0$。故
$$q_n^*=\underset{q_n}{\arg\max}\ \mathrm{L}(\boldsymbol{\theta},q_{n})=p(\boldsymbol{z}_n|\boldsymbol{x}_n,\boldsymbol{\theta})$$
并且
$$\mathcal{L}(\boldsymbol{\theta},\{q_n^*\})=\sum_n\log p(\boldsymbol{x}_n|\boldsymbol{\theta})=\ell(\boldsymbol{\theta})$$
故