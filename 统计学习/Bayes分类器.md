# Bayes分类器




$$ 
\begin{aligned}
h(\mathbf{x})& =\underset{y}{\operatorname*{\operatorname*{\operatorname*{argmax}}}}P(y|\mathbf{x})  \\
&=\underset{y}{\operatorname*{\mathrm{argmax~}}}\frac{P(\mathbf{x}|y)P(y)}{P(\mathbf{x})} \\
&=\underset{y}{\operatorname*{\operatorname*{\mathrm{argmax}}}}P(\mathbf{x}|y)P(y) \\
&=\underset{y}{\operatorname*{argmax}}\prod_{i=1}^dP(x_i|y)P(y) \\
&=\underset{y}{\operatorname*{\mathrm{argmax~}}}\sum_{i=1}^d\log(P(x_i|y))+\log(P(y))
\end{aligned} 
$$