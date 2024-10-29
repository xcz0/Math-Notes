# 多项式朴素Bayes分类器

考虑[[朴素Bayes分类器#类别特征]]中的情况，特征为离散值，但与类别特征不同，其值可比较大小，进行加减运算；同时假设特征取值服从[[多项分布]]（同时考虑多个特征），故称为多项特征(Multinomial features)。假设 $x_1,\cdots,x_k$ 为多项特征，模型为：
$$ p(x_1,\cdots,x_k|m,y=c)=\frac{m!}{x_1!\cdot x_2!\cdot\cdots\cdot x_k!}\prod_{i=1}^k\left(p_{i c}\right)^{x_i}$$
其中 $\sum_{i=1}^{k} x_k=m ,\ x_i \in \{ 0,1,\cdots,m \},\ \sum_{i=1}^k p_{i c}=1$。


实例：根据邮件中词的出现频率来判断是否为垃圾邮件，其中 $x_i$ 代表特定的词，$m$ 为邮件总词数。