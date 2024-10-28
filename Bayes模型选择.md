# Bayes模型选择

仍从[[最大后验估计]]的角度选择模型
$$ \hat{m}=\underset{m\in \mathcal{M}}{\arg\max} p(m|\mathcal{D})=\underset{m\in \mathcal{M}}{\arg\max}  p(\mathcal{D}|m)p(m)$$
若采样同等无知的原则，即模型的先验分布为均匀分布，则最优模型为
$$ \hat{m}=\underset{m\in \mathcal{M}}{\arg\max} p(\mathcal{D}|m) $$ 而似然函数可通过边际