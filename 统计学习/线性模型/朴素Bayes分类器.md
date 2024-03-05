# 朴素Bayes分类器

**朴素Bayes分类器**(naive Bayes classifier, NBC)是一种[[分类器#生成分类器]]，主要训练目标是估计类条件概率 $p(\boldsymbol{x}|y=c,\boldsymbol{\theta})$ 。

## 样本模型

类条件概率的

朴素Bayes分类器采用**属性条件独立性假设**(attribute conditional i时ependence assu'mption): 对
日知类别?假设所有属性相互独立.换言之，假设每个属性独立地对分类结果发生影响。