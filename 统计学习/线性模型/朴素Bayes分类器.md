# 朴素Bayes分类器

**朴素Bayes分类器**(naive Bayes classifier, NBC)是一种[[生成分类器]]。由于估计类条件概率 $p(\boldsymbol{x}|y=c,\boldsymbol{\theta})$ 的难度在于特征之间存在关联，特征空间往往远大于样本数。故考虑特征之间相互独立的情况，采用**属性条件独立性假设**(attribute conditional i时ependence assu'mption)，减小特征空间。

## 朴素Bayes假设

假设在已知类标签的情况下，各特征条件概率独立：
$$ p(\boldsymbol{x}|y=c,\boldsymbol{\theta})=\prod_{i=1}^d p(x_{i}|y=c,\boldsymbol{\theta}) $$

接下来一般使用 [[Bayes分类器]]得出结果：
$$ 
\begin{aligned}
h(\mathbf{x})& =\underset{y}{\operatorname*{\operatorname*{\operatorname*{argmax}}}}P(y|\mathbf{x})  \\
&=\underset{y}{\operatorname*{\mathrm{argmax~}}}\frac{P(\mathbf{x}|y)P(y)}{P(\mathbf{x})} \\
&=\underset{y}{\operatorname*{\operatorname*{\mathrm{argmax}}}}P(\mathbf{x}|y)P(y) \\
&=\underset{y}{\operatorname*{argmax}}\prod_{i=1}^dP(x_i|y)P(y) \\
&=\underset{y}{\operatorname*{\mathrm{argmax~}}}\sum_{i=1}^d\log(P(x_i|y))+\log(P(y))
\end{aligned} 
$$

## 参数估计

### 类别特征

对于类别特征，则用其频率估计概率：
$$ p(x_{i}|y=c)=\frac{|D_{c,x_i}|}{|D_{c}|} $$
$D_c$ 表示类别为 $c$ 的样本集； $D_{c,x_i}$ 表示 $D_c$ 中在第 $i$ 个属性上类别为 $x_i$ 的样本集。

若某个类别特征的值在训练集中没有与某个类同时出现过，即此时 $|D_{c,x_i}|=0$，这计算出的概率值为 $0$。此时，无论该样本的其他属性是什么，哪怕在其他属性上明显属于此类别，分类器都不会判定为此类别。为了避免其他属性携带的信息被训练集中未出现的属性值“抹去”，在估计概率值时通常要进行"平滑"(smoothing) 处理。

令 $N_{i}$ 表示第 $i$ 个属性可能的取值数，将其修正为
$$ \hat{P}(x_i\mid c) =\frac{|D_{c,x_i}|+l}{|D_c|+lN_i}  $$


常用的处理方式有拉普拉斯修正 (Laplacian correction)：则估计分别修正为


拉普拉斯修正避免了因训练集样本不充分而导致概率估值为零的问题，并且在训练集变大时，修正过程所引入的先验 (prior) 的影响也会逐渐变得可忽略，使得估值渐趋向于实际概率值。

### 连续特征

对于连续属性，则假设其服从正态分布：
$$ p(x_{i}|y=c,\boldsymbol{\theta})=N(x_{i}|\mu_{c,i},\sigma^2_{c,i})$$
此时，参数估计方式与一般的正态分布参数估计方式一样：
$$ \begin{align}
\mu_{c,i}&=\overline{x_{c}}=\frac{1}{|D_c|} \sum_{x \in D_c} x \\
\sigma^2_{c,i}&=s^2_{c}=\frac{1}{|D_c|-1} \sum_{x \in D_c} (x-\overline{x_{c}})^2
\end{align} $$

## 模型修正


