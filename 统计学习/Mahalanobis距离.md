# Mahalanobis距离

对于原空间，将其通过给定的[[线性映射]]转换到另一空间后，再考虑两点间的 [[Minkowski距离#Euclidean距离]] 。即对于 $\mathbf{x},\mathbf{y}$ 两点，考虑
$$ d(\boldsymbol{x},\boldsymbol{y})=\sqrt{(L\boldsymbol{x}-L\boldsymbol{y})^\mathsf{T}(L\boldsymbol{x}-L\boldsymbol{y})} $$
其中 $L$ 为给定的线性映射。

将其简化后可得**Mahalanobis距离**(Mahalanobis distance)为
$$ d_\mathbf{M}(\boldsymbol{x},\boldsymbol{y})=\sqrt{(\boldsymbol{x}-\boldsymbol{y})^\mathsf{T}\mathbf{M}(\boldsymbol{x}-\boldsymbol{y})} $$
其中 $\mathbf{M}=L^\mathsf{T}L$ 是一个[[半正定矩阵]]。

当 $L$ 为恒等变换，即 $\mathbf{M}$ 为单位矩阵时，此即退化为 [[Minkowski距离#Euclidean距离]] 。

当 $d_\mathbf{M}(\boldsymbol{x},\boldsymbol{y})=0$ 时，推出 $L(\boldsymbol{x}-\boldsymbol{y})=0$，若 $L$ 为可逆线性映射，则 $\boldsymbol{x}=\boldsymbol{y}$，满足[[度量]]的性质；否则为[[伪度量]]。

>对于[[多元正态分布]]，其概率密度函数可完全由 $y$ 与 $\mu$ 之间的Mahalanobis距离表示。

对 $M$ 做[[谱分解]]：$M=\sum_{i=1}^{n}\lambda _i u_i u_i^\mathsf{T}$，则 
$$d_\mathbf{M}(\boldsymbol{x},\boldsymbol{y})^2=\sum_{i=1}^{n}\lambda_i [u_i^\mathsf{T}(\boldsymbol{x}-\boldsymbol{y})]^\mathsf{T} [u_i^\mathsf{T}(\boldsymbol{x}-\boldsymbol{y})]$$
令 $z_i=[u_i^\mathsf{T}(\boldsymbol{x}-\boldsymbol{y})]$，即 $d_\mathbf{M}(\boldsymbol{x},\boldsymbol{y})^2=\sum_{i=1}^{n}\lambda_i z_i^2$，其等高线为椭圆。