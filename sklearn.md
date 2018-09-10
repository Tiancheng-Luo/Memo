### 1.1.1普通最小二乘法
$$
\tag{1-1} \underset{\omega}{\min}{||X\omega - y||_2}^2
$$
```python
from sklearn import linear_model
reg = linear_model.LinearRegresssion()
reg.fit([[0, 0], [1, 1], [2, 2]], [0, 1, 2])
print(reg.coef_)
```
### 1.1.2 岭回归
Ridge回归通过对系数的大小施加惩罚来解决普通最小二乘法的一些问题. 岭系数最小化的是带罚项的残差平方和.
$$
\underset{\omega}{min}{||X\omega - y||_2}^2 + \alpha{||\omega||_2}^2
$$
其中, $\alpha \geq 0$是控制系数收缩量的复杂性参数: $\alpha$的值越大, 收缩量越大, 这样系数对共线性的鲁棒性也更强.
与其他线性模型一样, Ridge用fit方法将模型系数$\omega$存储在其`coef_`成员中:
```python
from sklearn import linear_model
reg = linear_model.Ridge(alpha = 0.5)
reg.fit([[0, 0], [0, 0], [1, 1]], [0, 0.1, 1])
Ridge(alpha=0.5, copy_X=True, fit_intercept=True, max_iter=None,
		normalize=False, random_state=none, solver='auto',tol=0.001)
print(reg.

> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbNDE4Mzc1NjAwLDc3NzIwNjY3MV19
-->