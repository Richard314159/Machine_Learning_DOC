# 线性回归和逻辑回归的 MLE 视角

## 线性回归

令 $z = w^T x + b$，得到: 

$y = z + \epsilon, \, \epsilon \sim N(0, \sigma^2)$

于是: 

$y|x \sim N(z, \sigma^2)$

为啥是 $y|x$，因为判别模型的输出只能是 $y|x$。

它的概率密度函数: 

$f_{Y|X}(y)=\frac{1}{\sqrt{2 \pi} \sigma} \exp(\frac{-(y -z)^2}{2\sigma^2}) \\ = A \exp(-B (y - z)^2), \, A, B > 0$

计算损失函数: 

$L = -\sum_i \log f_{Y|X}(y^{(i)}) \\ = -\sum_i(\log A - B(y^{(i)} - z^{(i)})^2) \\ = B \sum_i(y^{(i)} - z^{(i)})^2 + C$

所以 $\min L$ 就相当于 $\min (y^{(i)} - z^{(i)})^2$。结果和最小二乘是一样的。

## 逻辑回归

令 $z = w^T x + b, a = \sigma(z)$，我们观察到在假设中: 

$P(y=1|x) = a \\ P(y=0|x) = 1 - a$

也就是说: 

$y|x \sim B(1, a)$

> 其实任何二分类器的输出都是伯努利分布。因为变量只能取两个值，加起来得一，所以只有一种分布。

它的概率质量函数（因为是离散分布，只有概率质量函数，不过无所谓）: 

$p_{Y|X}(y) = a^y(1-a)^{1-y}$

然后计算损失函数: 

$L = -\sum_i \log p_{Y|X}(y^{(i)}) \\ = -\sum_i(y^{(i)} \log a^{(i)} + (1-y^{(i)})\log(1-a^{(i)}))$

和交叉熵是一致的。

可以看出，在线性回归的场景下，MLE 等价于最小二乘，在逻辑回归的场景下，MLE 等价于交叉熵。但不一定 MLE 在所有模型中都是这样。
