# Multivariate Linear Regression

## Simultaneously Update
$$
\begin{aligned}
J(w_0, w_1, \cdots, w_n)&=\frac1{2m}\sum^m_{i=1}(w_0+w_1
x_1^{(i)}+w_2x_2^{(i)}+\cdots+w_nx_n^{(i)}-y^{(i)})^2 \\
&=\frac1{2m}\sum^m_{i=1}(\mathbf{w}^T\mathbf{x}-y^{(i)})^2
\end{aligned}
$$
$$
\frac{\partial{J}}{\partial{w_0}}=\frac1{m}\sum^m_{i=1}(\mathbf{w}^T\mathbf{x}-y^{(i)})^2
$$
$$
\frac{\partial{J}}{\partial{w_n}}=\frac1{m}\sum^m_{i=1}(\mathbf{w}^T\mathbf{x}-y^{(i)})^2 \cdot x_n
$$