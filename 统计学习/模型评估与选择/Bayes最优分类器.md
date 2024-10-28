# Bayes最优分类器

在 [[Bayes决策论]]的框架下，将样本的实际类别视为状态，所有类别构成状态空间 $\mathcal{H}=\mathcal{Y}=\{ 1,\cdots , C \}$；预测类别视为动作，所有类别视为动作空间 $\mathcal{A}=\mathcal{Y}$，考虑分类问题。





假设 $P(y|\mathbf{x})$ 是已知的，那么将其中最可能的标签作为预测结果，即
$$ y^*=h_{opt}(\mathbf{x})=\underset{y}{\operatorname*{argmax}}P(y|\mathbf{x}) $$

其出错概率为：

$$\epsilon_{BayesOpt}=1-\mathrm{P}(h_{\mathrm{opt}}(\mathbf{x})|\mathbf{x})=1-\mathrm{P}(y^*|\mathbf{x})$$

例如，若已知 $\mathrm{P}(+1|\mathbf{x})=0.8,\ \mathrm{P}(-1|\mathbf{x})=0.2$，则 $y^*=+1$，但其仍有 $\epsilon_{BayesOpt}==1-\mathrm{P}(y^*|\mathbf{x})=0.2$ 的概率出错。

虽然 $P(y|\mathbf{x})$ 几乎不可能提前知道，但这作为一种理想的分类器，为一般的分类器提供了一个误差下界，可用于评价分类器的性能。