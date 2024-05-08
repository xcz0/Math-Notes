# 二项分布的共轭先验分布是Beta分布

设某事件 $A$ 在一次试验中发生的概率为 $\theta$，为估计 $\theta$，对试验进行了 $n$ 次独立观测，其中事件 $A$ 发生了 $X$ 次，显然 $X | \theta \sim b(n, \theta)$，即
$$ P(X=x | \theta)=\binom{n}{x} \theta^{x}(1-\theta)^{n-x}, \quad x=0,1, \cdots, n $$
假若我们在试验前对事件 $A$ 没有什么了解，从对其发生的概率也没有任何信息。在这种场合，贝叶斯本人建议采用“同等无知”的原则，使用区间 $(0,1)$ 上的均匀分布 $U(0,1)$ 作为 $\theta$ 的先验分布。贝叶斯的这个建议被后人称为贝叶斯假设。


先写出 $X$ 和 $\theta$ 的联合分布
$$h(x, \theta)=\binom{n}{x} \theta^x (1-\theta)^{n-x}, \quad x=0,1, \cdots, n, \quad 0<\theta<1$$
然后求 $X$ 的边际分布
$$ m(x)=\binom{n}{x} \int_0^1 \theta^x (1-\theta)^{n - x} \d \theta=\binom{n}{x} \frac{\Gamma(x+1) \Gamma(n-x+1)}{\Gamma(n+2)} $$
最后求出 $\theta$ 的后验分布
$$ \pi(\theta | x) =\frac{h(x, \theta)}{m(x)} =\frac{\Gamma(n+2)}{\Gamma(x+1) \Gamma(n-x+1)} \theta^{(x+1)-1}(1-\theta)^{(n-x+1)-1}, \quad 0<\theta<1 $$

即 $\theta | x \sim B e(x+1, n-x+1)$，故贝塔分布是伯努利试验中成功概率的共枙先验分布。其后验期望估计为
$$ \hat{\theta}_{\mathrm{B}}=E(\theta | x)=\frac{x+1}{n+2} $$
