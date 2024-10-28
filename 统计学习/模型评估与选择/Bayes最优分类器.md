# Bayes最优分类器

在 [[Bayes决策论]]的框架下，将样本的实际类别视为状态，所有类别构成状态空间 $\mathcal{H}=\mathcal{Y}=\{ 1,\cdots , C \}$；预测类别视为动作，所有类别视为动作空间 $\mathcal{A}=\mathcal{Y}$，考虑分类问题。

## 01损失

将损失函数定义为误分类的数量：
$$ \ell_{01}(y^*,\hat{y})=\mathbb{1}(y^* \neq \hat{y}) $$
则其后验期望损失为
$$ \rho(\hat{y}|\mathcal{D})=p(y^* \neq \hat{y}|\mathcal{D})=1-p(y^* = \hat{y}|\mathcal{D}) $$
故最优策略为选择最可能的标签：
$$ \pi(\mathcal{D})=\underset{y\in \mathcal{Y}}{\arg\max} p(y|\mathcal{D}) $$
此即后验概率密度的峰值，即[[最大后验估计]]。

其出错概率为：

$$\epsilon_{BayesOpt}=1-\mathrm{P}(h_{\mathrm{opt}}(\mathbf{x})|\mathbf{x})=1-\mathrm{P}(y^*|\mathbf{x})$$

例如，若已知 $\mathrm{P}(+1|\mathbf{x})=0.8,\ \mathrm{P}(-1|\mathbf{x})=0.2$，则 $y^*=+1$，但其仍有 $\epsilon_{BayesOpt}==1-\mathrm{P}(y^*|\mathbf{x})=0.2$ 的概率出错。

虽然 $P(y|\mathbf{x})$ 几乎不可能提前知道，但这作为一种理想的分类器，为一般的分类器提供了一个误差下界，可用于评价分类器的性能。

## 代价敏感分类

假设即使选择正确也仍需付出一些代价，其代价函数矩阵（二分类）定义为：
$$\ell(y^*,\hat{y}) = \begin{bmatrix}\ell_{00}&\ell_{01}\\\ell_{10}&\ell_{11}\end{bmatrix}$$
其中行向量（即下标的第一个）为同一实际状况。

此时后验期望损失为：
$$ \rho(\hat{y}|\mathcal{D})=\ell(y^*,\hat{y})^\mathsf{T} p(y|\mathcal{D}) $$
