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
其中, $\alpha \l


> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTg4NzY0NzM5Miw3NzcyMDY2NzFdfQ==
-->