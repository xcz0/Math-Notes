# Bayes决策论

在**内在状态**(state of nature) $h \in \mathcal{H}$ 下，**智能体**(agent)依据**偏好**(preferences)做出的**行为**(action) $a \in \mathcal{A}$ 产生的损失或收益用**代价函数**(loss function) $\ell(h,a)$ 或**效用函数**(utility function) $U(h,a)=-\ell(h,a)$ 表示。

一般而言，代价函数是已知的，但事物的状态需要通过观测得到，并且往往只是**部分可观测**(partially observed)。此时，只能获得事物状态的[[后验概率]]，再结合代价函数，得到特定行为的**后验期望损失**(posterior expected loss)或**后验期望风险**(posterior expected risk)：
$$ \rho(a|\mathcal{D}) \triangleq \mathbb{E}_{p(h|\mathcal{D})}\left[\ell(h,a)\right]=\sum_{h\in\mathcal{H}}\ell(h,a)p(h|\mathcal{D})$$

**最优策略**(optimal policy)定义为风险最小化的的行为，也称为**Bayes估计**或**Bayes决策准则**或**最大期望效用原则**(maximum expected utility principle)：
$$ \pi^*(\mathcal{D})=\underset{a\in \mathcal{A}}{\arg\min} \rho(a|\mathcal{D}) = \underset{a\in \mathcal{A}}{\arg\max} \mathbb{E}_{p(h|\mathcal{D})}\left[U(h,a)\right] $$

