# Fisher信息矩阵

**Fisher信息矩阵**(Fisher information matrix, FIM)定义为对数似然函数的梯度的相关系数：
$$\mathbf{F}(\boldsymbol{\theta}) \triangleq E[\nabla\log p(\boldsymbol{x}|\boldsymbol{\theta})\nabla\log p(\boldsymbol{x}|\boldsymbol{\theta})^\mathsf{T}]$$
其第 $(i,j)$ 项为
$$F_{ij}=\mathbb{E}\left[\left(\frac{\partial}{\partial\theta_i}\log p(\boldsymbol{x}|\boldsymbol{\theta})\right)\left(\frac{\partial}{\partial\theta_j}\log p(\boldsymbol{x}|\boldsymbol{\theta})\right)\right]$$

若 $p(\boldsymbol{x}|\boldsymbol{\theta})$ 满足某些条件，则Fisher息矩阵等于负对数似然函数的期望：
$$ F_{ij}=- \mathbb{E}\left[\left(\frac{\partial^2}{\partial\theta_i \partial\theta_j}\log p(\boldsymbol{x}|\boldsymbol{\theta})\right)\right]$$
#TODO 待证明