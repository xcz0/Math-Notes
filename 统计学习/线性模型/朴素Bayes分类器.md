# 朴素Bayes分类器

**朴素Bayes分类器**(naive Bayes classifier, NBC)是一种[[分类器#生成分类器]]。由于估计类条件概率 $p(\boldsymbol{x}|y=c,\boldsymbol{\theta})$ 的难度在于特征之间存在关联，特征空间往往远大于样本数。故考虑特征之间相互独立的情况，采用**属性条件独立性假设**(attribute conditional i时ependence assu'mption)，减小特征空间。

## 样本模型

设样本有 $d$ 个特征，则假设类条件概率为各特征条件概率之积：
$$ p(\boldsymbol{x}|y=c,\boldsymbol{\theta})=\prod_{i=1}^d p(x_{i}|y=c,\boldsymbol{\theta}) $$

此时，对于离散属性，则用其频率估计概率：
$$ p(x_{i}|y=c)=\frac{|D_{c,x_i}|}{D_{c}} $$

对于连续属性，则假设其服从正太分布：
$$ p(x_{i}|y=c,\boldsymbol{\theta})=N(x_{i}|\mu_{c,i},\sigma^2_{c,i})$$


## 模型修正

