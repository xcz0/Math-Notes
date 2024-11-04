# 期望最大化(EM)算法

期望最大化(expectation maximization, EM)算法是[[边界优化]]算法的一种。
假设[[混合模型]]的似然函数为
$$\ell(\boldsymbol{\theta})=\sum_{n=1}^N\log p(\boldsymbol{x}_n|\boldsymbol{\theta})=\sum_{n=1}^N\log\left[\sum_{\boldsymbol{z}_n}p(\boldsymbol{x}_n,\boldsymbol{z}_n|\boldsymbol{\theta})\right]$$

由于对数函数是凸函数，根据 [[Jensen不等式]] 得
