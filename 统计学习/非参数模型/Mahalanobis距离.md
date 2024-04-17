# Mahalanobis距离

对于原空间，将其通过给定的[[线性映射]]转换到另一空间后，再考虑两点间的 [[Minkowski距离#Euclidean距离]] 。即对于 $\mathbf{x},\mathbf{y}$ 两点，考虑
$$ d(\boldsymbol{x},\boldsymbol{y})=\sqrt{(L\boldsymbol{x}-L\boldsymbol{y})^\mathsf{T}(L\boldsymbol{x}-L\boldsymbol{y})} $$
其中 $L$ 为给定的线性映射。

将其简化后可得**Mahalanobis距离**(Mahalanobis distance)为
$$ d_\mathbf{M}(\boldsymbol{x},\boldsymbol{y})=\sqrt{(\boldsymbol{x}-\boldsymbol{y})^\mathsf{T}\mathbf{M}(\boldsymbol{x}-\boldsymbol{y})} $$
其中 $\mathbf{M}=L^\mathsf{T}L$ 是一个[[半正定矩阵]]。

当 $L$ 为恒等变换，即 $\mathbf{M}$ 为单位矩阵时，此即退化为 [[Minkowski距离#Euclidean距离]] 。

由于当 $d_\mathbf{M}(\boldsymbol{x},\boldsymbol{y})=0$ 时只能推出 $L(\boldsymbol{x}-\boldsymbol{y})=0$，并不能推出 $\boldsymbol{x}-\boldsymbol{y}=0$，所以这是一种[[伪度量]]