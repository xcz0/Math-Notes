# Gini指数

分类问题中，假设有 $K$ 个类，样本点属于第 $K$ 类的概率为 $p_k$ ，则概率分布的Gini指数定义为
$$\mathrm{Gini}(p)=\sum_{k=1}^Kp_k(1-p_k)=1-\sum_{k=1}^Kp_k^2$$

![[二分类的Gini指数.png]]


对于给定的样本集合 $S$，将其根据标签划分为 $S_k=\{(\mathbf{x},y)\in S:y=k\}$，则用其频率代替概率，即
$$ p_k= \frac{|S_k|}{|S|}$$
样本集的Gini指数定义为
$$ \mathrm{Gini}(S)=1-\sum_{k=1}^K \left( \frac{|S_k|}{|S|} \right)^2 $$