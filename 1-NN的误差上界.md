# 1-NN的误差上界

考虑 [[K近邻分类]] 中当 $k=1$ 时的情况。假设对于测试点 $\mathbf{x}_{t}$ 而言，其最近邻点记为 $\mathbf{x}_0$ 。并且假设随着训练集大小 $n$ 趋于无穷，两者间的距离趋于 $0$： $\lim_{ n \to \infty } d(\mathbf{x}_{t},\mathbf{x}_{0})=0$。此时对于 $\mathbf{x}_{t}$ 的预测标签即为 $\mathbf{x}_0$ 的标签。那么有两种错误情况：$\mathbf{x}_{t}$ 的实际标签为 $y^*$，但 $\mathbf{x}_0$ 的标签不是；$\mathbf{x}_0$ 的标签为 $y^*$，但 $\mathbf{x}_{t}$ 的实际标签不是。即误差概率为
$$ \epsilon=P(y^*|\mathbf{x}_t)[1-P(y^*|\mathbf{x}_0)]+P(y^*|\mathbf{x}_0)[1-P(y^*|\mathbf{x}_t)] $$
