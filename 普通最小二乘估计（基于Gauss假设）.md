# 普通最小二乘估计（基于Gauss假设）

考虑线性模型为：
$$Y=X\beta+\varepsilon$$
其中设计矩阵 $X$ 为固定值，且列向量线性无关；误差 $\varepsilon$ 为随机变量；$\beta$ 为模型参数。
>[!note]
>假设误差项的期望为0，且各分量不相关，但方差相同：
> $$ \begin{align}
> E(\varepsilon) & = 0 \\
> cov(\varepsilon) & = \sigma^2 I_n \\
> \end{align} $$

采用[[普通最小二乘法（优化视角）]]中的结果作为参数 $\beta$ 的估计
## 最小二乘估计的特性

由于 $E(Y)=X\beta$，故
$$\begin{aligned}
E(\hat{\beta})& =\quad E\left\{(X^{\mathrm{T}}X)^{-1}X^{\mathrm{T}}Y\right\} \\
&=\quad(X^{\mathrm{T}}X)^{-1}X^{\mathrm{T}}E(Y) \\
&=\quad(X^{\mathrm{T}}X)^{-1}X^{\mathrm{T}}X\beta \\
&\begin{array}{cc}{=}&{\beta.}\end{array}
\end{aligned}$$
由于 $cov(Y)=\sigma^2 I_n$，故
$$\begin{aligned}
\operatorname{cov}(\hat{\beta})& =\mathrm{cov}(HY) \\
&=(X^\mathrm{T}X)^{-1}X^\mathrm{T}\mathrm{cov}(Y)X(X^\mathrm{T}X)^{-1} \\
&=\sigma^{2}(X^{\mathrm{T}}X)^{-1}X^{\mathrm{T}}X(X^{\mathrm{T}}X)^{-1} \\
&=\sigma^2(X^\mathrm{T}X)^{-1}.
\end{aligned}$$
