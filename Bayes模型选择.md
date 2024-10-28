# Bayes模型选择

仍从[[最大后验估计]]的角度选择模型
$$ \hat{m}=\underset{m\in \mathcal{M}}{\arg\max} p(m|\mathcal{D})=\underset{m\in \mathcal{M}}{\arg\max}  p(\mathcal{D}|m)p(m)$$
## 边际似然

其中
$$ p(\mathcal{D}|m)=\int p(\mathcal{D}|\mathbf{\theta},m)p(\theta|m) \, d\theta  $$
称为**边际似然**(marginal likelihood)，或模型 $m$ 的**可信度**(evidence)。

## 同等无知
若采样*同等无知*的原则，即模型的先验分布为均匀分布，此时最优模型为
$$ \hat{m}=\underset{m\in \mathcal{M}}{\arg\max} p(\mathcal{D}|m) $$

## Occam剃刀效应

一般而言，复杂模型拥有解释复杂数据的能力。例如线性模型在数据线性相关时的解释能力强，数据线性相关度低时解释能力弱；而更复杂的多项式模型不仅能解释线性相关的数据，还能解释更复杂的数据。即对于简单的模型，其边际似然 $p(\mathcal{D}|m)$ 往往集中在某一类数据集上，而复杂模型的边际似然则分布得更加均匀。同时，由于概率的正则性，在简单模型对应的那类数据上，其边际似然高于复杂模型的。




模型将表现得越来越好（至少不弱于被其包含的简单模型）。Occam剃刀原则认为复杂模型出现的概率低。模型的复杂度一般使用其自由度衡量，自由度高则代表模型更加复杂。