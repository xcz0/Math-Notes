# Bayes信息量准则(Bayesian information criterion)

由[[后验概率的正态近似]]得：
$$\begin{align}
\ln p(\mathcal{D}) & \approx -\ln p(\hat{\theta},\mathcal{D})-\frac12 \ln|\mathbf{H}|+ \frac{D}{2} \ln2\pi \\
&= -\ln p(\hat{\theta})-\ln p(\mathcal{D}|\hat{\theta})-\frac12 \ln|\mathbf{H}|+ \frac{D}{2} \ln2\pi
\end{align} $$

考虑其中的 $\ln|\mathbf{H}|$



假设先验概率服从均匀分布，即 $p(\theta)$ 是常数。

