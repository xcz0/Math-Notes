# Mahalanobis距离

定义两点 $\mathbf{x},\mathbf{y}$ 之间的Mahalanobis距离(Mahalanobis distance)为
$$ d_\mathbf{M}(\boldsymbol{x},\boldsymbol{\mu})=\sqrt{(\boldsymbol{x}-\boldsymbol{\mu})^\mathsf{T}\mathbf{M}(\boldsymbol{x}-\boldsymbol{\mu})} $$

其中 $\mathbf{M}$ 是一个正定矩阵。

当 $\mathbf{M}$ 为单位矩阵时，此即退化为 [[L_p距离#Euclidean距离]] 。