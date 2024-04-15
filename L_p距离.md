# $L_{p}$ 距离

设特征空间 $\mathcal{X}$ 是 $n$ 维实数向量空间 $R^n$，$X_i,X_j \in \mathcal{X}, X_i= (x_i^{(1)},\cdots,x_i^{(n)}),\ X_j= (x_j^{(1)},\cdots,x_j^{(n)})$，$X_i,X_j$ 的 $L_p$ 距离($L_{p}$ distance)定义为
$$ L_{p}(x_{i},x_{j})=\left( \sum_{l=1}^{n} \mid x_{i}^{(l)}- x_{j}^{(l)}\mid^p\right)^{\frac{1}{p}} $$
![[Lp距离.png]]


## Euclidean距离

当 $p=1$ 时，称为欧氏距离 (Euclidean distance) ，即
$$L_2(x_i,x_j)=\left(\sum_{l=1}^n|x_i^{(l)}-x_j^{(l)}|^2\right)^{\frac12}$$

## Manhattan距离

当 $p=1$ 时，称为曼哈顿距离 (Manhattan distance)，即
$$L_1(x_i,x_j)=\sum_{l=1}^n|x_i^{(l)}-x_j^{(l)}|$$

## 最大距离

当 $p=\infty$ 时，它是各个坐标距离的最大值，即
$$L_\infty(x_i,x_j)=\max_l|x_i^{(l)}-x_j^{(l)}|$$
