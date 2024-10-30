# 经验Bayes

#TODO PML1:4.6.5.3

在[[层次Bayes模型]]的基础上，超参数 $\boldsymbol{\xi}$ 不认为是随机变量，同样利用数据对其数值进行估计。即在计算参数 $\theta$ 的先验分布时，不需计算 $p(\boldsymbol{\theta},\boldsymbol{\xi}|\mathcal D)$，而使用 $p(\boldsymbol{\theta}|\hat{\boldsymbol{\xi}},\mathcal D)$ 代替。

超参数的边际似然为
$$ p(\mathcal{D}|\xi)=\int p(\mathcal{D}|\theta)[(\theta|\xi)] \, d\xi  $$
将其最大化即得到第二类极大似然估计(type II maximum likelihood)：
$$ \hat{\xi}_{MML}=\underset{\xi}{\arg\max} p(\mathcal{D}|\xi) $$
将结果代入 $p(\boldsymbol{\theta}|\hat{\boldsymbol{\xi}},\mathcal D)$ 即可得到参数 $\theta$ 的后验分布