# Bayes估计

## 先验分布与后验分布

理念：统计模型的参数不是一个固定的值，也带有随机性质，可看作随机变量，记为 $\overline{\Theta}$，可用概率分布 $\pi(\theta)$ 描述，称之为**先验分布**。在获得样本之后，总体分布、样本与先验分布通过贝叶斯公式结合起来得到关于未知量 $\theta$ 的后验分布 $p_{\overline{\Theta}|X=x}(\theta)$。任何关于 $\theta$ 的统计推断都基于其后验分布进行。

获取后验分布的步骤：

1. 根据总体信息与样本信息确定模型 $p_{\theta}(x)$，根据先验信息确定先验分布 $\pi(\theta)$
2. 综合总体信息、样本信息和先验信息得到样本 $X=x$ 和参数 $\theta$ 的联合分布
$$ p_{X,\overline{\Theta}}(x, \theta)=p_{\theta}(x) \pi(\theta)$$ 
3. 计算 $X$ 的边际概率函数:
$$p_{X}(x)=\int p_{X,\overline{\Theta}}(x, \theta) d\theta=\int p_{\theta}(x) \pi(\theta) d\theta$$
4. 得到后验分布
$$ p_{\overline{\Theta} | X=x}(\theta)=\frac{p_{X, \overline{\Theta}}(x, \theta)}{p_X(x)}=\frac{p_\theta(x) \pi(\theta)}{\int p_{\vartheta}(x) \pi(\vartheta) d \vartheta} $$



## Bayes估计

> [!definition] Bayes风险
> 若 $T$ 是一个关于参数 $g(\theta)$ 的估计，则将以先验分布 $\pi(\theta)$ 作为权重的均方误差 $MSE(\theta;T)$ 的加权平均值称为此估计的**Bayes风险(Bayes risk)**。
> $$ R(\pi;T) = \int E_\theta[T-g(\theta)]^2 \pi(\theta) \, d\theta = E[T(X)-g(\overline{\Theta})]^2$$

利用后验分布 $\pi(\theta|\bf{X})$ 估计 $\theta$ 有三种常用的方法：

+ 使用后验分布的密度函数最大值点作为 $\theta$ 的点估计的最大后验估计;
+ 使用后验分布的中位数作为 $\theta$ 的点估计的后验中位数估计;
+ 使用后验分布的均值作为 $\theta$ 的点估计的后验期望估计.

> [!definition] Bayes估计
> 若在给定先验分布 $\pi(\theta)$ 的情况下，估计 $T$ 在所有关于参数 $g(\theta)$ 的估计中，Bayes风险(Bayes risk)最小，则称其为**Bayes估计**。

>[!theorem] 
> 后验期望估计，即
> $$ T(x)=E(g(\overline{\Theta}) |X=x)=\int g(\theta) p_{\overline{\Theta} | X=x}(\theta) d \theta=\frac{\int g(\theta)p_\theta(x) \pi(\theta) d \theta}{\int p_{\vartheta}(x) \pi(\vartheta) d \vartheta} $$
> 是贝叶斯估计, 记为 $\hat{\theta}_B$。

>[!proof]
> $$ R(\pi;T) =E[T(X)-g(\overline{\Theta})]^2=E\{ E[(T(x)-g(\overline{\Theta}))^2 |X ] \}  $$
> 当 $T(x)=E(g(\overline{\Theta}) |X=x)$ 时，$x$ 取任意值
> $$ E[(T(x)-g(\overline{\Theta}))^2 |X=x ]$$
> 都最小，故 $E[T(X)-g(\overline{\Theta})]^2$ 也是最小的。

