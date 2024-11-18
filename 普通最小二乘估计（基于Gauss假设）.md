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
## 最小二乘估计的期望与方差

由于 $E(Y)=X\beta$，故
$$\begin{aligned}
E(\hat{\beta})& =\quad E\left\{(X^{\mathrm{T}}X)^{-1}X^{\mathrm{T}}Y\right\} \\
&=\quad(X^{\mathrm{T}}X)^{-1}X^{\mathrm{T}}E(Y) \\
&=\quad(X^{\mathrm{T}}X)^{-1}X^{\mathrm{T}}X\beta \\
&\begin{array}{cc}{=}&{\beta.}\end{array}
\end{aligned}$$
由于 $cov(Y)=\sigma^2 I_n$，故
$$\begin{align}
\operatorname{cov}(\hat{\beta})& =\mathrm{cov}(HY) \\
&=H\mathrm{cov}(Y)H^\mathsf{T} \\
&=\sigma^{2}(X^{\mathrm{T}}X)^{-1}X^{\mathrm{T}}X(X^{\mathrm{T}}X)^{-1} \\
&=\sigma^2(X^\mathrm{T}X)^{-1}.
\end{align}$$

由于 $\hat{Y},\hat{\varepsilon}$ 为 $Y$ 的线性变换，即：
$$\begin{bmatrix}\hat{Y}\\ \hat{\varepsilon}\end{bmatrix}
=\begin{bmatrix}HY\\ (I_n-H)Y\end{bmatrix}
=\begin{bmatrix}H\\ I_n-H\end{bmatrix}Y$$
故其协方差为：
$$\begin{align}
\mathrm{cov}\begin{bmatrix}\hat{Y}\\ \hat{\varepsilon}\end{bmatrix}& =\begin{bmatrix}H\\ I_n-H\end{bmatrix}\mathrm{cov}(Y)\begin{bmatrix}H^\mathsf{T} & (I_n-H)^\mathsf{T}\end{bmatrix} \\
&=\sigma^2\begin{bmatrix}H\\ I_n-H\end{bmatrix}\begin{bmatrix}H^\mathsf{T} & (I_n-H)^\mathsf{T}\end{bmatrix} \\
&=\sigma^{2}\begin{bmatrix}H & 0 \\ 0 & I_n-H\end{bmatrix}
\end{align}$$

故 $\hat{Y}$ 与 $\hat{\varepsilon}$ 不相关，但其分量各自相关：
$$\mathrm{cov}(\hat{y}_i,\hat{y}_j)=\sigma^2h_{ij},\quad\mathrm{cov}(\hat{\varepsilon}_i,\hat{\varepsilon}_j)=\sigma^2(1-h_{ij})$$
## 方差估计

误差项的方差也为模型的参数，考虑其经验估计：残差平方和：
$$ \mathrm{RSS}=\sum_{i=1}^{n} \hat{\varepsilon}_i^2 $$
其期望均值为：
$$\begin{align}
E(\mathrm{RSS})& =\sum_{i=1}^n\sigma^2(1-h_{ii}) \\
&=\sigma^{2}\left\{n-\mathrm{trace}(H)\right\} \\
&=\sigma^{2}(n-p),
\end{align}$$
故其无偏估计为：
$$ \hat{\sigma}^2 $$