# K近邻分类器

K 近邻法 (K nearest neighbor, KNN) 是一种[[非参数方法#基于实例模型(exemplar-based model)]] 。基本思想是：对新的实例 $\mathbf{x}$，在训练集 $\mathcal{D}$ 中找到 $k$ 个与其最接近的实例，记为 $N_k(\mathbf{x},\mathcal{D})$，再根据分类决策规则得出新实例的标签。模型的超参数为近邻数 $K$ 、距离度量及分类决策规则。

当训练集、距离度量、 K 值及分类决策规则确定后，对于任何一个新的输入实例，它所属的类唯一确定。这相当于根据上述要素将特征空间划分为一些子空间，确定子空间里的每个点所属的类。
![[Pasted image 20230219154926.png]]


+ *优点*：可以学习非线性边界、能够自然地处理多分类任务
+ *缺点*：不适用于维数过高的情况、占用内存大（需要储存所有训练数据）、
## 距离度量

过去常用 [[Minkowski距离]]度量，而现在一般使用学习后的度量[[度量学习]]，参考 [Distance Metric Learning for Large Margin Nearest Neighbor Classification]([Distance Metric Learning for Large Margin Nearest Neighbor Classification | The Journal of Machine Learning Research (acm.org)](https://dl.acm.org/doi/10.5555/1577069.1577078))与[FaceNet: A Unified Embedding for Face Recognition and Clustering](https://arxiv.org/abs/1503.03832)

## 分类决策规则

一种自然的想法，选用 $N_k(\mathbf{x},\mathcal{D})$ 中最多的标签类别作为输入实例的类，即多数表决规则 (majority voting rule)。模型可记为：
$$ p(y=c|\boldsymbol{x},\mathcal{D})=\frac{1}{K}\sum_{n\in N_K(\boldsymbol{x},\mathcal{D})}\mathbb{I}\left(y_n=c\right) $$

>如果出现平局，那么依次剔除距离最远的近邻点，再看能否确定多数标签。

## K 值的选择

当 $K=1$ 时，即返回最近的训练样本类别，此时样本空间被划分为Voronoi镶嵌(Voronoi tessellation)：每个样本点 $\mathbf{x}_n$ 对应着一个区域 $V(\mathbf{x}_n)$，此区域内的任意点与 $\mathbf{x}_n$ 的距离都比与其他样本点的更小，此区域也称为单元(cell)。此时训练集中的各样本点都将被分类为其本身的类，故训练误差为零。

同理，如果选择较小的 $K$ 值，训练误差较小。但预测结果对近邻的实例点非常敏感。如果邻近的实例点恰巧是噪声，预测就会出错。此时，分类边界曲折，模型复杂，容易发生过拟合。

相反，如果选择较大的 $K$ 值，受噪声影响小，但训练误差较大。此时，分类边界平滑，模型简单，容易发生欠拟合。

如果$k = N$，那么无论输入实例是什么，都将简单地预测它属于在训练实例中最多的类。这时，模型过于简单，完全忽略训练实例中的大量有用信息，是不可取的。

在应用中，$K$ 值一般取一个比较小的数值。通常采用交叉验证法来选取最优的 $K$ 值。

## 1-NN的误差上界

考虑当 $k=1$ 时的情况。假设对于测试点 $\mathbf{x}_{t}$ 而言，其最近邻点记为 $\mathbf{x}_0$ 。并且假设随着训练集大小 $n$ 趋于无穷，两者间的距离趋于 $0$： $\lim_{ n \to \infty } d(\mathbf{x}_{t},\mathbf{x}_{0})=0$。此时对于 $\mathbf{x}_{t}$ 的预测标签即为 $\mathbf{x}_0$ 的标签。那么有两种错误情况：$\mathbf{x}_{t}$ 的实际标签为 $y^*$，但 $\mathbf{x}_0$ 的标签不是；$\mathbf{x}_0$ 的标签为 $y^*$，但 $\mathbf{x}_{t}$ 的实际标签不是。即误差概率为
$$ \epsilon=P(y^*|\mathbf{x}_t)[1-P(y^*|\mathbf{x}_0)]+P(y^*|\mathbf{x}_0)[1-P(y^*|\mathbf{x}_t)] $$

假设 $\mathbf{x}_{t}$ 与 $\mathbf{x}_0$ 足够接近，以至于 $P(y^*|\mathbf{x}_t)=P(y^*|\mathbf{x}_0)$，可以得到
$$ \epsilon < [1-P(y^*|\mathbf{x}_0)]+[1-P(y^*|\mathbf{x}_t)]=2[1-P(y^*|\mathbf{x}_t)] $$
这仅仅是 [[Bayes最优分类器]]误差的两倍。

## 维数灾难

假设样本空间是一个 $d$ 维单位超立方体 $[0,1]^d$，并且 $n$ 个训练样本点*均匀地*分布在空间中。
![[Pasted image 20240416223026.png]]
假设 $l$ 是包含 $k$ 个近邻的最小超立方体的边长，那么其“体积”为 $l^d$，根据几何概型，$l^d / 1=k / n$，即
$$ l=\left( \frac{k}{n} \right)^{1 / d} $$
当 $k=10,d=100$ 时，$l=0.955$，即此10个近邻几乎需要囊括整个空间才能找到。如下图所示，当维数很大时，任意两点间的距离几乎都一样。这失去了找出最接近的点的意义。

![[Pasted image 20240416223009.png]]

如果想通过增加数据量来避免这一问题，那么 $n=k (l^{-1})^d$，即需要的数据量随维度指数增长。