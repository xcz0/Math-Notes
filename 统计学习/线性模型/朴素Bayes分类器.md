# 朴素Bayes分类器

**朴素Bayes分类器**(naive Bayes classifier, NBC)是一种[[分类器#生成分类器]]。由于估计类条件概率 $p(\boldsymbol{x}|y=c,\boldsymbol{\theta})$ 的难度在于特征之间存在关联，特征空间往往远大于样本数。故考虑特征之间相互独立的情况，采用**属性条件独立性假设**(attribute conditional i时ependence assu'mption)，减小特征空间。

## 朴素贝叶斯模型

设输入空间 $\mathcal{X} \subseteq \mathbb{R}^n$ 为 $n$ 维向量的集合，输出空间为类标记(class label)集合 $\mathcal{y} =\{ c_{1},\cdots,c_{K} \}$。输入为特征向量 $x \in \mathcal{X}$，输出为类标记 $y \in \mathcal{Y}$。$X$ 是定义在输入空间 $\mathcal{X}$ 上的随机向量，$Y$ 是定义在输出空间 $\mathcal{Y}$ 上的随机变量。$P(X,Y)$ 是 $X$ 和 $Y$ 的联合概率分布。训练数据集
$$ T=\{ (x_{1},y_{1}),\cdots , (x_{N},y_{N})\} $$
由 $P(X,Y)$ 独立同分布产生。

## 样本模型

设样本有 $d$ 个特征，则假设类条件概率为各特征条件概率之积：
$$ p(\boldsymbol{x}|y=c,\boldsymbol{\theta})=\prod_{i=1}^d p(x_{i}|y=c,\boldsymbol{\theta}) $$

此时，对于离散属性，则用其频率估计概率：
$$ p(x_{i}|y=c)=\frac{|D_{c,x_i}|}{|D_{c}|} $$
$D_c$表示类别为$c$ 的样本集； $D_{c,x_i}$ 表示 $D_c$ 中在第 $i$ 个属性上取值为 $x_i$ 的样本集。


对于连续属性，则假设其服从正态分布：
$$ p(x_{i}|y=c,\boldsymbol{\theta})=N(x_{i}|\mu_{c,i},\sigma^2_{c,i})$$
此时，参数估计方式与一般的正态分布参数估计方式一样：
$$ \begin{align}
\mu_{c,i}&=\overline{x_{c}}=\frac{1}{|D_c|} \sum_{x \in D_c} x \\
\sigma^2_{c,i}&=s^2_{c}=\frac{1}{|D_c|-1} \sum_{x \in D_c} (x-\overline{x_{c}})^2
\end{align} $$


## 模型修正

若某个离散属性的值在训练集中没有与某个类同时出现过，即此时 $|D_{c,x_i}|=0$，这计算出的概率值为0。此时，无论该样本的其他属性是什么，哪怕在其他属性上明显属于此类别，分类器都不会判定为此类别。为了避免其他属性携带的信息被训练集中未出现的属性值“抹去”，在估计概率值时通常要进行"平滑"(smoothing) 处理。常用的处理方式有拉普拉斯修正 (Laplacian correction)：令 $N$ 表示训练集 $D$ 中可能的类别数，$N_{i}$ 表示第 $i$ 个属性可能的取值数（$\sum N_i=N$），则估计分别修正为
$$ \begin{align}
\hat{P}(c)& =\frac{|D_c|+1}{|D|+N},  \\
\hat{P}(x_i\mid c)& =\frac{|D_{c,x_i}|+1}{|D_c|+N_i} 
\end{align} $$

拉普拉斯修正避免了因训练集样本不充分而导致概率估值为零的问题，并且在训练集变大时，修正过程所引入的先验 (prior) 的影响也会逐渐变得可忽略，使得估值渐趋向于实际概率值。