# Bayes二分对率回归

回归模型为：
$$ p(y_i|x_i,w)=Ber(y_i|\sigma(w^\mathsf{T}x_i)) $$
数据集的似然函数为：
$$ p(y|X,w)=\prod_{i=1}^{N} Ber(y_i|\sigma(w^\mathsf{T}x_i)) $$

设权重的先验分布为正态分布：
$$ p(w)=\mathcal{N}(w|0,\lambda ^{-1}\mathbf{I}) $$

## 后验分布

使用[[后验概率的正态近似]]得
$$ p(w|X,y) \approx \mathcal{N}(w|\hat{w},H^{-1}) $$
其中$$