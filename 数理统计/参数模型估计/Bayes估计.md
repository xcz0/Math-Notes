# Bayes估计

若 $T$ 是一个关于参数 $g(\theta)$ 的估计，则将以先验分布 $\pi(\theta)$ 作为权重的均方误差 $MSE(\theta;T)$ 的加权平均值称为此估计的**Bayes风险(Bayes risk)**。
$$ R(\pi;T) = \int E_\theta[T-g(\theta)]^2 \pi(\theta) \, d\theta = E[T(X)-g(\overline{\Theta})]^2$$


在给定先验分布的情况下，估计在所有关于参数的估计中，后验期望估计的Bayes风险(Bayes risk)最小，即
$$ T(x)=E(g(\overline{\Theta}) |X=x)=\int g(\theta) p_{\overline{\Theta} | X=x}(\theta) d \theta=\frac{\int g(\theta)p_\theta(x) \pi(\theta) d \theta}{\int p_{\vartheta}(x) \pi(\vartheta) d \vartheta} $$
称之为**贝叶斯估计**, 记为 $\hat{\theta}_B$。

证明：
$$ R(\pi;T) =E[T(X)-g(\overline{\Theta})]^2=E\{ E[(T(x)-g(\overline{\Theta}))^2 |X ] \}  $$
当 $T(x)=E(g(\overline{\Theta}) |X=x)$ 时，$x$ 取任意值
$$ E[(T(x)-g(\overline{\Theta}))^2 |X=x ]$$
都最小，故 $E[T(X)-g(\overline{\Theta})]^2$ 也是最小的。

