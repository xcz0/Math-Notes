# Bayes线性回归

线性模型的概率分布为
$$ p(\mathbf{y}|\mathbf{X},\boldsymbol{\omega} ,\sigma^2)=\prod_{i=1}^{N} p(y_n|\mathbf{x}_n^\mathsf{T}\boldsymbol{\omega},\sigma^2) = \mathcal{N}(\mathbf{y}|X \boldsymbol{\omega},\sigma^{2} \mathbf{I}_N)$$
假设其*权重的先验分布为正态分布*：$\boldsymbol{\omega} \sim N(\boldsymbol{\omega}_0,\boldsymbol{\Sigma}_0)$，由[[线性正态系统]]可知，其后验分布也为正态分布：
$$ p(\boldsymbol{\omega}|\mathbf{y},\mathbf{X},\sigma^{2})=\mathcal{N}(\boldsymbol{\omega}|\boldsymbol{\omega}_N,\boldsymbol{\Sigma}_N) $$
其中
$$ \begin{align}
\Sigma^{-1}_N &= \Sigma^{-1}_0+\mathbf{X}^\mathsf{T} (\sigma^{2} \mathbf{I}_N)^{-1} \mathbf{X} = \Sigma^{-1}_0+\sigma^{-2}\mathbf{X}^\mathsf{T} \mathbf{X} \\
\boldsymbol{\omega}_N & = \Sigma_N \left(\Sigma_0^{-1}\boldsymbol{\omega}_0+\mathbf{X}^T(\sigma^{2} \mathbf{I}_N)^{-1}\boldsymbol{y}\right)=\sigma^{-2} \Sigma_N \mathbf{X}^\mathsf{T} \boldsymbol{y} + \Sigma_N \Sigma_0^{-1} \boldsymbol{\omega}_0
\end{align} $$

若再假设其权重各分量独立同分布，即 $\omega_0=0,\Sigma_0=\tau^{2}\mathbf{I}_N$，则
$$ \begin{align}
\Sigma_N &= \left(\tau^{-2} \mathbf{I}+\sigma^{-2}\mathbf{X}^\mathsf{T} \mathbf{X}  \right)^{-1}  \\
\boldsymbol{\omega}_N & = \sigma^{-2} \Sigma_N\mathbf{X}^\mathsf{T} \boldsymbol{y} 
\end{align} $$