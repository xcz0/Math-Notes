# Bayes线性回归

线性模型的概率分布为
$$ p(\mathbf{y}|\mathbf{X},\boldsymbol{w} ,\sigma^2)=\prod_{i=1}^{N} p(y_n|\mathbf{x}_n^\mathsf{T}\boldsymbol{w},\sigma^2) = \mathcal{N}(\mathbf{y}|X \boldsymbol{w},\sigma^{2} \mathbf{I}_N)$$

## 权重的估计

假设其*权重的先验分布为正态分布*：$\boldsymbol{w} \sim N(\boldsymbol{w}_0,\boldsymbol{\Sigma}_0)$，由[[线性正态系统]]可知，其后验分布也为正态分布：
$$ p(\boldsymbol{w}|\mathcal{D},\sigma^{2})=p(\boldsymbol{w}|\mathbf{y},\mathbf{X},\sigma^{2})=\mathcal{N}(\boldsymbol{w}|\boldsymbol{w}_N,\boldsymbol{\Sigma}_N) $$
其中
$$ \begin{align}
\Sigma^{-1}_N &= \Sigma^{-1}_0+\mathbf{X}^\mathsf{T} (\sigma^{2} \mathbf{I}_N)^{-1} \mathbf{X} = \Sigma^{-1}_0+\sigma^{-2}\mathbf{X}^\mathsf{T} \mathbf{X} \\
\boldsymbol{w}_N & = \Sigma_N \left(\Sigma_0^{-1}\boldsymbol{w}_0+\mathbf{X}^T(\sigma^{2} \mathbf{I}_N)^{-1}\boldsymbol{y}\right)=\sigma^{-2} \Sigma_N \mathbf{X}^\mathsf{T} \boldsymbol{y} + \Sigma_N \Sigma_0^{-1} \boldsymbol{w}_0
\end{align} $$

若再假设其权重*各分量独立同分布*，即 $w_0=0,\Sigma_0=\tau^{2}\mathbf{I}_N$，则
$$ \begin{align}
\Sigma_N &= \left(\tau^{-2} \mathbf{I}+\sigma^{-2}\mathbf{X}^\mathsf{T} \mathbf{X}  \right)^{-1}  \\
\boldsymbol{w}_N & = \sigma^{-2} \Sigma_N\mathbf{X}^\mathsf{T} \boldsymbol{y} =  \sigma^{-2} \left(\tau^{-2} \mathbf{I}+\sigma^{-2}\mathbf{X}^\mathsf{T} \mathbf{X}  \right)^{-1}\mathbf{X}^\mathsf{T} \boldsymbol{y} = \left( \frac{\sigma^2}{\tau^2} \mathbf{I}+\mathbf{X}^\mathsf{T} \mathbf{X}  \right)^{-1}\mathbf{X}^\mathsf{T} \boldsymbol{y}
\end{align} $$
此时其最大后验估计为：
$$ \hat{w}_{MAP}=\left( \frac{\sigma^2}{\tau^2} \mathbf{I}+\mathbf{X}^\mathsf{T} \mathbf{X}  \right)^{-1}\mathbf{X}^\mathsf{T} \boldsymbol{y} $$
此即[[岭回归]]。

## 预测

用其对新的数据点进行预测：
$$\begin{align}
p(y_*|x_*,\mathcal{D},\sigma^{2}) &= \int  p(y_*|\mathbf{x}_*^\mathsf{T}\boldsymbol{w},\sigma^2)p(\boldsymbol{w}|\mathcal{D},\sigma^{2})  \, d\boldsymbol{w} \\
&=\int  \mathcal{N}(y_*|\mathbf{x}_*^\mathsf{T}\boldsymbol{w},\sigma^2)\mathcal{N}(\boldsymbol{w}|\boldsymbol{w}_N,\boldsymbol{\Sigma}_N)  \, d\boldsymbol{w} \\
 &= \mathcal{N}(y_*|\mathbf{x}_*^\mathsf{T}\boldsymbol{w}_N,\sigma^{2}+\mathbf{x}_*^\mathsf{T}\boldsymbol{\Sigma}_N\mathbf{x}_*)
\end{align}
 $$
其中的均值代入可得：
$$ \begin{align}
\mathbf{x}_*^\mathsf{T}\boldsymbol{w}_N & = \mathbf{x}_*^\mathsf{T}\sigma^{-2} \Sigma_N\mathbf{X}^\mathsf{T} \boldsymbol{y} \\
 & = \mathbf{x}_*^\mathsf{T}\Sigma_0\mathbf{X}^\mathsf{T}\left( \mathbf{X}\Sigma_0\mathbf{X}^\mathsf{T}+\sigma^2\mathbf{I} \right)^{-1}  \boldsymbol{y}
\end{align} $$
方差为：
$$ \begin{align}
\sigma^{2}+\mathbf{x}_*^\mathsf{T}\boldsymbol{\Sigma}_N\mathbf{x}_* & =\sigma^{2}+\mathbf{x}_*^\mathsf{T}\left(\Sigma_0+\sigma^{-2}\mathbf{X}^\mathsf{T} \mathbf{X}  \right)^{-1} \mathbf{x}_* \\
 & = \sigma^2+\mathbf{x}_*^\mathsf{T}\Sigma_0\mathbf{x}_*-\mathbf{x}_*^\mathsf{T}\Sigma_0\mathbf{X}(\sigma^2 \mathbf{I}+\mathbf{X}\Sigma_0\mathbf{X}^\mathsf{T})^{-1}\mathbf{X}^\mathsf{T}\Sigma_0\mathbf{x}_*
\end{align} $$

由于 $\mathbf{X}^\mathsf{T} \mathbf{X}$ 是实对称矩阵，故可对其进行正交分解：$\mathbf{X}^\mathsf{T} \mathbf{X}=U \Lambda U^\mathsf{T}$，其中 $U$ 为正交矩阵，$\Lambda$ 为对角矩阵。代入化简以上计算得：
$$ \begin{align}
\Sigma_N &= U \left(\tau^{-2} \mathbf{I}+\sigma^{-2}\Lambda  \right)^{-1} U^\mathsf{T}  \\
\boldsymbol{w}_N & = \sigma^{-2} \Sigma_N\mathbf{X}^\mathsf{T} \boldsymbol{y} =  \sigma^{-2} \left(\tau^{-2} \mathbf{I}+\sigma^{-2}\mathbf{X}^\mathsf{T} \mathbf{X}  \right)^{-1}\mathbf{X}^\mathsf{T} \boldsymbol{y} = U \left( \frac{\sigma^2}{\tau^2} \mathbf{I}+\Lambda \right)^{-1} U^\mathsf{T} \mathbf{X}^\mathsf{T} \boldsymbol{y}
\end{align} $$


其方差由原模型的测量噪声 $\sigma^{2}$ 与 $\mathbf{x}_*^\mathsf{T}\boldsymbol{\Sigma}_N\mathbf{x}_*$ 组成，而这一项代表了新数据点与原数据的接近程度：
$$ \mathbf{x}_*^\mathsf{T}\boldsymbol{\Sigma}_N\mathbf{x}_*=\mathbf{x}_*^\mathsf{T}U \left(\tau^{-2} \mathbf{I}+\sigma^{-2}\Lambda  \right)^{-1} U^\mathsf{T}\mathbf{x}_*=\| \left(\tau^{-2} \mathbf{I}+\sigma^{-2}\Lambda  \right)^{-1 / 2} U^\mathsf{T}\mathbf{x}_* \| $$





## 测量误差的估计

假设 $\omega,\sigma^{2}$ 服从正态[[逆Gamma分布]]：
$$P(\boldsymbol{w},\sigma^2)=NIG(\boldsymbol{w},\sigma^2|\boldsymbol{w}_0,\Sigma_0,a_0,b_0)=N(\boldsymbol{w}|\boldsymbol{w}_0,\sigma^2 \Sigma_0)IG(\sigma^2|a_0,b_0)$$
其中 $IG(\sigma^2|a_0,b_0) \propto (\sigma^2)^{-a_0-1}e^{-b_0/\sigma^2}$ 。


