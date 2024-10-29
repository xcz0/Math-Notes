# Bayes信息量准则(Bayesian information criterion)

由[[后验概率的正态近似]]得：
$$\begin{align}
\ln p(\mathcal{D}) & \approx -\ln p(\hat{\theta},\mathcal{D})-\frac12 \ln|\mathbf{H}|+ \frac{D}{2} \ln2\pi \\
&= -\ln p(\hat{\theta})-\ln p(\mathcal{D}|\hat{\theta})-\frac12 \ln|\mathbf{H}|+ \frac{D}{2} \ln2\pi
\end{align} $$

考虑其中的 $\ln|\mathbf{H}|$，称为Occam因子，代表了模型的复杂度。其中 $\mathbf{H}(\hat{\theta})$ 为 [[Fisher信息矩阵]]。假设样本独立同分布，则 $\mathbf{H}(\hat{\theta})=N \cdot \mathbf{J}(\hat{\theta})$，故
$$ \ln|\mathbf{H}|=\ln|N \cdot \mathbf{J}(\hat{\theta})|=\ln N^{D_m}| \mathbf{J}(\hat{\theta})|=D_m\ln N + \ln|\mathbf{J}(\hat{\theta})| $$
假设先验概率服从均匀分布，即 $p(\theta)$ 是常数。同时，在*大样本*下，$\ln2$ 相比于 $\ln n$ 相对影响微小，故将其忽略。而

定义**Bayes信息量准则分数**(BIC score)为
$$ J_{BIC}(m)= \ln p(\mathcal{D}|\hat{\theta},m)-\frac{D_m}{2} \ln N $$
其中 $D_m$ 为模型参数的数量，$N$ 为数据集大小。

将其乘以 $-2$ 后得到**Bayes信息量准则损失**(BIC loss)：
$$ \mathcal{L}_{BIC}(m)=-2\ln p(\mathcal{D}|\hat{\theta},m)+D_m \ln N $$

