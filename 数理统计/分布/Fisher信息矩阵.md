# Fisher信息矩阵

**Fisher信息矩阵**(Fisher information matrix, FIM)定义为对数似然函数的梯度的相关系数：
$$\mathbf{F}(\boldsymbol{\theta}) \triangleq E[\nabla\log p(\boldsymbol{x}|\boldsymbol{\theta})\nabla\log p(\boldsymbol{x}|\boldsymbol{\theta})^\mathsf{T}]$$
其第 $(i,j)$ 项为
$$F_{ij}=\mathbb{E}\left[\left(\frac{\partial}{\partial\theta_i}\log p(\boldsymbol{x}|\boldsymbol{\theta})\right)\left(\frac{\partial}{\partial\theta_j}\log p(\boldsymbol{x}|\boldsymbol{\theta})\right)\right]$$

若 $p(\boldsymbol{x}|\boldsymbol{\theta})$ 满足某些条件，则Fisher息矩阵等于负对数似然函数的期望：
$$ F_{ij}=- \mathbb{E}\left[\left(\frac{\partial^2}{\partial\theta_i \partial\theta_j}\log p(\boldsymbol{x}|\boldsymbol{\theta})\right)\right]$$
#TODO 待证明

若各样本间独立同分布，即
$$ \log p(\boldsymbol{x}|\boldsymbol{\theta})= \log \prod_{i=1}^{N}p(x_i|\boldsymbol{\theta})=\sum_{i=1}^{N}\log p(x_i|\boldsymbol{\theta})$$
将单个样本的Fisher信息矩阵记为
$$\mathbf{J}(\theta)=\mathbb{E}\left[-\frac{\partial^2}{\partial\theta^2}\ln p(x_i|\theta)\right]$$
则 $N$ 个样本的信息矩阵为
$$ \mathbf{F}(\boldsymbol{\theta})=N \cdot \mathbf{J}(\theta) $$


## Fisher 信息矩阵的近似

当样本量 $n$ 增大时，似然函数的曲率也会增加。因此，在大样本下，负对数似然函数的海森矩阵 $\mathbf{I}(\hat{\theta}_k)$ 的值通常会与 $n$ 成正比，即：
$$\mathbf{I}(\hat{\theta}_k) \approx n \cdot \mathbf{J}(\hat{\theta}_k)$$
其中， $\mathbf{J}(\hat{\theta}_k)$ 是单位样本的 Fisher 信息矩阵，它不依赖于样本数量。因此，当样本量增加时，整体 Fisher 信息矩阵的幅值也会线性增长为 $n$。
