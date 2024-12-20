# Bayes分类

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

这种分类原则称为**Bayes分类器**(Bayes classifier)，贝叶斯分类器得到的测试错误率称作**贝叶斯错误率**(Bayes error rate)。虽然 $P(y|\mathbf{x})$ 几乎不可能提前知道，但这作为一种理想的分类器，为一般的分类器提供了一个误差下界，可用于评价分类器的性能。

## 代价敏感分类

假设即使选择正确也仍需付出一些代价，其代价函数矩阵定义为：
$$\ell(y^*,\hat{y}) = \begin{bmatrix} 
\ell_{00} & \cdots &  \ell_{0C}\\
 \vdots  & \ddots  & \vdots \\
\ell_{C0}&\cdots & \ell_{CC}
\end{bmatrix}$$
其中行向量（即下标的第一个）为同一实际状况。

此时后验期望损失为：
$$ \rho(\hat{y}|\mathcal{D})=\ell(y^*,\hat{y})^\mathsf{T} p(y|\mathcal{D}) $$
最优策略为：
$$ \pi(\mathcal{D})=\underset{y\in \mathcal{Y}}{\arg\max} p(y|\mathcal{D}) $$

## 有拒绝的分类

在信息不足时，可能会拒绝回答分类问题，即此时的动作空间为 $\mathcal{A}=\mathcal{Y} \cup \{ 0 \}$，其中的 $0$ 即代表拒绝回答。此时代价函数矩阵定义为：
$$\ell(y^*,a) = \begin{bmatrix} 
\lambda_r  & \lambda_e
\end{bmatrix}$$
其中 $\lambda_r$ 代表拒绝回答的损失，为 $C \times 1$ 的列向量，$\lambda_e$ 为误分类损失，为 $C$ 阶方阵。

若拒绝损失皆相同，即 $\mathbf{\lambda_r}= \lambda_r \cdot \mathbf{1}$，且误分类损失为01损失，即 $\lambda_{e}=\lambda_e \cdot \mathbf{I}-\lambda_e \cdot \mathbf{E}$，
则后验期望损失为：
$$ \rho(\hat{y}|\mathcal{D})=\ell(y^*,\hat{y})^\mathsf{T} p(y|\mathcal{D})=\begin{bmatrix} 
\lambda_r   \\
\lambda_e \cdot \mathbf{1} - \mathbf{E} \cdot p(y|\mathcal{D})
\end{bmatrix} $$
此时，若 $\max p(y|\mathcal{D})>1-\frac{\lambda_r}{\lambda_e}$ 则信息足够，应选择最可能的类别；否则，应拒绝回答。